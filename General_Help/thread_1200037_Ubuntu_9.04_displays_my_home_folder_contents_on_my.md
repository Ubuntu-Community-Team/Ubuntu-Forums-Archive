---
title: "Ubuntu 9.04 displays my home folder contents on my desktop"
date: 2009-06-29
forum: General Help
---

### Post by PC_load_letter on 2009-06-29
This is unbelievable. I did some research and here is what I have in my ~/config/user-dirs.dirs
```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
XDG_DOCUMENTS_DIR="$HOME/Documents"
```


I restarted X like 10 times now and I still have all the contents of my home directory displayed (not just linked) on my desktop. 
I do have some KDE apps installed and the last thing I did before this happened is that I copied the contents of my backed-up ~/Documents folder from the Hardy install to the new ~/Documents folder.

**EDIT:** The backed-up files were burnt on a dvd, then copied to the new Jaunty install.

---

### Post by PC_load_letter on 2009-06-29
Here is a kicker. I created an empty folder in my /home/user_name directory and called it 'Desktop_new', and made it my Desktop folder in ~/config/user-dirs.dirs and restarted.

Result: Nothing changed except now that the desktop folder on my desktop is called 'Desktop_new'

This is by far the most annoying and disturbing problem I encountered w/ Ubuntu since Feisty 7.04.

---

### Post by credobyte on 2009-06-29
1) Open gconf-editor ( via terminal or from your main menu if listed )
2) Browse to Nautilus and find a place where it says "home directory as desktop" ( something like that .. you'll see it ) and uncheck it
3) Remove all "desktop" folders from your home directory and create a new one called Desktop
4) Reboot ..

Not sure if it will help but .. give it a try :)

---

### Post by PC_load_letter on 2009-06-29
Thanks man! It worked like a charm, actually just unchecking the 'desktop as home directory' option in gconf-editor did it, which in all honesty I'm not sure how useful this feature is. 
Another thing, since I didn't know this option even existed, I didn't turn this feature on, so what did? 

Anyway, thanks a lot.

---

