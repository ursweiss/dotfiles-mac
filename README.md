# Setup local environment
Steps to configure **zsh**, **Vim** and **iTerm2** on a macOS machine.

## ZSH

### Set your login shell to zsh
```sh
chsh -s /bin/zsh
```
### Install oh-my-zsh
```sh
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
````

### Download the powerline patched font "Meslo"
Download only the font files needed and copy them to the users fonts folder:
```sh
cd ~ && \
svn export https://github.com/powerline/fonts/trunk/Meslo%20Slashed Meslo-$(date +"%Y%m%d") && \
cp -f Meslo-$(date +"%Y%m%d")/*.ttf ~/Library/Fonts/ && \
fc-cache -f "~/Library/Fonts"
```
**Note:** Updating the font cache (fc-cache command) can take some time.

## dotfiles
If not done already, you should set the name and eMail address git uses first:
```sh
git config --global user.name "your name"
git config --global user.email "email@domain.com"
```
It's very likely that some of the files in the repository already exist on the local machine. These will cause conflicts when a normal `git clone` command is used.

To prevent this, we initialize a new git repository, fetch all the content from the repository and then reset to the most recent commit.

```sh
cd ~
git init
git remote add origin https://github.com/ursweiss/dotfiles-mac
git fetch --all
git reset --hard origin/master
```
**Optional:** Set an oh-my-zsh option to not show any version control state for the dotfile repository. This will speed up the prompt within the home directory significantly.
```sh
git config --add oh-my-zsh.hide-status 1
```

## iTerm2

### Download an install iTerm2
[iTerm2 Download page](https://www.iterm2.com/downloads.html)

Open iTerms preferences and enable "Load preferences from a custom folder or URL". As path enter `/Users/<username>/.iterm2`.

**Important:** **Don't** check "Save changes to folder when iTerm2 quits" and **don't** click the "Save Current Settings to Folder".

Restart iTerm2 and you should a nice looking windows with the default prompt of the "agnoster" theme.

## Vim

No additional actions needed for Vim. Everything needed was already done by cloning the dotfiles repository.
