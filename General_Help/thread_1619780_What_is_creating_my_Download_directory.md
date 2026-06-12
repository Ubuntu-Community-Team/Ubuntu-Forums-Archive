---
title: "What is creating my Download directory?"
date: 2010-11-12
forum: General Help
---

### Post by erlguta on 2010-11-12
Hi.
I DON'T want the 'Download' dir in my home. I don't have it in any other computer and there is no problem. But in my Desktop, every time i reboot there is one 'Downloads' dir in my home...and i remove it every time (rmdir Downloads). But when i reboot, it is there again!.
So what the h.. is creating my Downloads dir?.
Thank you for your help.

I repeat, i have another lapotop with the same ubuntu version (10.04) and i don't have this problem.

---

### Post by ki4jgt on 2010-11-12
I wish I had your luck! I had a program which deleted mine. Now I need it back.

---

### Post by 7h3d4rk0n3 on 2010-11-12
I believe if you use Firefox and have your downloads set to save to ~/Downloads, it will create the folder on boot. Check to see if you have Firefox set to save to that folder.

---

### Post by ki4jgt on 2010-11-12
I have FF set to the downloads directory and the folder is still missing.

---

### Post by erlguta on 2010-11-12
No. It is not firefox because I use Chrome, and i never start firefox...and even Firefox have configured the 'Desktop' directory for downloads, as chrome...

---

### Post by sisco311 on 2010-11-12
What's the output of 
```
cat ~/.config/user-dirs*
```?

---

### Post by erlguta on 2010-11-12
> **sisco311 said:**
> What's the output of 
```
cat ~/.config/user-dirs*
```?

cat ~/.config/user-dirs*
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Escritorio"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/Plantillas"
XDG_PUBLICSHARE_DIR="$HOME/Público"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"
es_ES

---

### Post by realzippy on 2010-11-16
> **sisco311 said:**
> What's the output of 
```
cat ~/.config/user-dirs*
```?


...and now ??????????????

---

### Post by sisco311 on 2010-11-16
> **realzippy said:**
> ...and now ??????????????

Everything looks fine in ~/.config/user-dirs.dirs, so I have no clue what process is creating the ~/Download directory.

---

### Post by realzippy on 2010-11-16
...thought you were going to suggest changes in *user-dirs.dirs*,
'cause you wanted OP's file.

---

### Post by sisco311 on 2010-11-16
Yeh, my guess was that XDG_DOWNLOAD_DIR is set to "$HOME/Downloads", but that's not the case.

---

### Post by davec64 on 2010-11-16
What about backing up the file then try commenting out:

```
#XDG_DOWNLOAD_DIR="$HOME/"
```

I think the line is actually where to put the Download folder i.e. in Home rather than the actual download location.

EDIT

Ignore it is the actual download location!

---

