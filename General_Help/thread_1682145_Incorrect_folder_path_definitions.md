---
title: "Incorrect folder path definitions"
date: 2011-02-05
forum: General Help
---

### Post by Hirot on 2011-02-05
I have somehow managed to wreck the definitions /paths for my Home and Desktop. If I click on Places I now have a "Home Folder" displayed as "Open Your personal Folder", a "Desktop"  displayed as "Open the contents of your Desktop in a folder" and a second "Home Folder" displays as "Open '/home/ian'"....and they all point to the same folder which is my personal user file "ian". This is kind of OK except that every file I have now gets displayed on my screen because "Desktop" has a view of these files.

Is there any easy way to reset my file directory ? or do I have to backup my files and reinstall Ubuntu.

Any help would be appreciated.

Many Thanks   Ian

---

### Post by Krytarik on 2011-02-05
No need to re-install at all.;-)

There are (at least) two simple ways to fix it, either by using Ubuntu Tweak, or by changing the relevant text file manually, I would even prefer the latter.

Ubuntu Tweak:
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```You will find Ubuntu Tweak in "Applications -> System Tools" after the installation.
In it choose "Default Folder Locations" in the section "Personal".


edit the text file:

~/.config/user-dirs.dirs

This is mine, these are the default entries:
```
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```Greetings.

---

### Post by Hirot on 2011-02-06
Krytarik, many thanks for your quick reply. I now have a new toy to play with and will hopefully sort out my mistakes.

---

