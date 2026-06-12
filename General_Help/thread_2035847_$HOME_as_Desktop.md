---
title: "$HOME as Desktop"
date: 2012-07-31
forum: General Help
---

### Post by evilsoup on 2012-07-31
I prefer using my $HOME folder as my Desktop folder; on an old netbook, I want to do this. Normally, I'd just edit $HOME/.config/user-dirs.dirs and make the line

XDG_DESKTOP_DIR="$HOME/"

This works perfectly on my computer running normal Ubuntu, but on this old netbook with Luubntu it refuses to pick up the changes - even after rebooting.

Anyone got any ideas?

---

### Post by Lars Noodén on 2012-07-31
The way I'd try it would be to make the ~/Desktop directory a symlink back to ~

---

### Post by evilsoup on 2012-07-31
Thanks. That worked, but now I've got some ugly recursion going on.

I guess I'll have to put my bug report-filing glasses on.

[Here]("https://bugs.launchpad.net/lubuntu-software-center/+bug/1031463") is the bug report, if it affects anyone else.

---

### Post by Zvlwab on 2012-07-31
> **Lars Noodén said:**
> The way I'd try it would be to make the ~/Desktop directory a symlink back to ~
That's a really bad way actually.

You should edit .config/user-dirs.dirs instead
```
:~$ cat .config/user-dirs.dirs 
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/.templates"
XDG_PUBLICSHARE_DIR="$HOME"
XDG_DOCUMENTS_DIR="$HOME/Other"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"

```

I think the syntax is self explaining.

---

### Post by Lars Noodén on 2012-07-31
> **Zvlwab said:**
> That's a really bad way actually.

You should edit .config/user-dirs.dirs instead

Yes, the symlink method is an awful way of doing it.  

However, I've tried editing [font=Courier New].config/user-dirs.dirs[/font] to try to get the home directory as the desktop, as evilsoup wants.  Setting XDG_DESKTOP_DIR to $HOME and to $HOME/ but neither work.  When the LXDE desktop starts up, there is the error 'The specified directory is not valid'.  XDG_DESKTOP_DIR seems to need something more than just $HOME/, because anything else does work.  So there might be a bug in LXDE or something else that it depends on.

---

### Post by evilsoup on 2012-07-31
Uh... that's what I *did*; the problem is that doing so doesn't have any effect on Lubuntu.

---

### Post by Lars Noodén on 2012-08-01
Evilsoup: it turns out there is a bug reported already.  If you have anything to add to it (including 'it affects me') the link to it is this:

[https://bugs.launchpad.net/pcmanfm/+bug/1031463](https://bugs.launchpad.net/pcmanfm/+bug/1031463)

---

### Post by evilsoup on 2012-08-01
Thanks, but that's actually the bug report I filed :P

---

### Post by Zvlwab on 2012-08-01
You may need to take a look at ~/.gtk-bookmarks if that file exists then. I don't use Lubuntu myself.

---

