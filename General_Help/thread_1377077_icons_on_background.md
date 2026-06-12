---
title: "icons on background"
date: 2010-01-09
forum: General Help
---

### Post by tituspurdin on 2010-01-09
Old user---new problem---at least for me.  My usually blank and happy
background suddenly lists the things in my home directory. Well, it
has icons for them.  I have tried the gconf-editor, apps->nautilus->desktop
drill, but the stuff is still there.  Showed up suddenly about a day ago.
Any suggestions are appreciated.


Titus sends

---

### Post by lidex on 2010-01-10
Are you using ubuntu-tweak?

---

### Post by tituspurdin on 2010-01-10
Don't know what tweak is.  So, I doubt that I use it.


Titus sends

---

### Post by michy99 on 2010-01-10
What is the output of this command?```
cat ~/.config/user-dirs.dirs
```

---

### Post by mechro on 2010-01-10
Was the "drill" you used?...

**gconf-editor > apps > nautilus > preferences > uncheck "desktop_is_home_dir"**

---

### Post by tituspurdin on 2010-01-10
Output from cat ~/.config/user-dirs.dirs is:

XDG_DESKTOP_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"


Titus sends

---

### Post by tituspurdin on 2010-01-10
No, the 'drill' involved

apps->nautilus->desktop

and making sure that things were unchecked.


Titus sends

---

### Post by mechro on 2010-01-10
The point I was making did you do?...

**gconf-editor > apps > nautilus > _[COLOR="Red"]preferences[/COLOR]_ > uncheck "desktop_is_home_dir"**

If not, try it.

---

### Post by tituspurdin on 2010-01-10
Thanks.  I did that

gconf-editor > apps > nautilus > preferences > uncheck "desktop_is_home_dir"

without effect.


Titus sends

---

### Post by michy99 on 2010-01-10
> **tituspurdin said:**
> Output from cat ~/.config/user-dirs.dirs is:

XDG_DESKTOP_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"


Titus sends

The problem is th line that says```
XDG_DESKTOP_DIR="$HOME/"
```Open for editing.```
gedit ~/.config/user-dirs.dirs
```and change it to read```
XDG_DESKTOP_DIR="$HOME/Desktop"
```Actually, most of the lines are wrong. Here's how mine looks.```
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
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

---

### Post by tituspurdin on 2010-01-11
Thanks.  That was what was wanted.  Can't explain how they got munged
up in the first place.  Incidentally, it works just fine (good old
command line living) if you comment out all of the lines in that
user-dirs.dirs file.  Backgrounds should, after all, be just that:
backgrounds---not breeding grounds for icons!  Many thanks for your
help and your patience.


Titus sends

---

### Post by mechro on 2010-01-11
@ michy99

Many thanks for the dirs.dirs info. It's added to my Ubuntu knowledge. :D

---

