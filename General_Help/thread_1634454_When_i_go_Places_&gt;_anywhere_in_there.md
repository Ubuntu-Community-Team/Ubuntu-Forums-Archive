---
title: "When i go Places &gt; anywhere in there"
date: 2010-11-30
forum: General Help
---

### Post by mst3k on 2010-11-30
Attached is the video.

---

### Post by cariboo on 2010-11-30
It would help if you also explained what the problem is, instead of just attaching a video. many of our members don't click on attachments, unless there is an explanation.

---

### Post by pricetech on 2010-11-30
I rarely click on attachments even when there is an explanation, so yeah give us a description of the problem.

---

### Post by wojox on 2010-11-30
Look in your /home/user/.config/user-dirs.dirs and see if it looks like this:

```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

---

### Post by mc4man on 2010-11-30
see here
[http://ubuntuforums.org/showthread.php?p=10098466](http://ubuntuforums.org/showthread.php?p=10098466)

this 'bug' (request to mitigate), will explain why and what do to to prevent in the future
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194)

---

