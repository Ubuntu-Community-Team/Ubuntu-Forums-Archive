---
title: "&quot;desktop&quot; link in thunar/pcmanfm"
date: 2010-04-07
forum: General Help
---

### Post by nicoseb on 2010-04-07
I have a little problem both in LXDE and XFCE. I already run into it a long time ago but do not remember how I manage to get rid of it:
A user is suppose to have a "Desktop" folder into their home directory, then that is the files that are shown on the desktop. If one delete that folder, the system uses the home directory as the "Desktop" link and shows on the desktop the files that are in the home directory... If the "Desktop" folder is re-created, the system does not care.

Does anyone know how to revert this? How can I tell the system what folder the desktop should link to? As I said this is the same behavior with both XFCE4 and pcmanfm in LXDE. 
(However I am using pcmanfm2 right now so the desktop is not supported anyway, and if I click on the "Desktop" link in pcmanfm2, it quickly shows "~/artup" in the address bar and crashes pathetically!)

Thanks

---

### Post by kerry_s on 2010-04-07
not following you there. :lolflag:

just go to /usr/share/applications, copy & paste what ever you want to the desktop. if you try & drag it you'll get a permission error. once it's on your desktop you can do whatever you want to it, like change the name, what icon to use, etc...
just use your text editor.

make sure you have the lubuntu ppa for the latest lxde stuff like pcmanfm2.
```
sudo add-apt-repository ppa:lubuntu-desktop/ppa
```

---

### Post by nicoseb on 2010-04-08
> **kerry_s said:**
> not following you there. :lolflag:

just go to /usr/share/applications, copy & paste what ever you want to the desktop. if you try & drag it you'll get a permission error. once it's on your desktop you can do whatever you want to it, like change the name, what icon to use, etc...
just use your text editor.

make sure you have the lubuntu ppa for the latest lxde stuff like pcmanfm2.
```
sudo add-apt-repository ppa:lubuntu-desktop/ppa
```

I do have the repos, and pcmanfm2 installed (desktop is not even supported anymore).
Anyway, I was not talking about what you are referring to!

In Thunar, like pcmanfm, the "Desktop://" is a link to somewhere (by default ~/Desktop). I am trying to understand where that link is, and how to change it.
(because if you delete ~/Desktop, then the system is lost... and re-creating the folder does not help)

---

### Post by kerry_s on 2010-04-08
i think i'm getting you. look at ~/.config/user-dirs.dirs

mine has this:

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

### Post by nicoseb on 2010-04-08
> **kerry_s said:**
> i think i'm getting you. look at ~/.config/user-dirs.dirs

mine has this:

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

There you go!!! Very appreciated, I had been looking into .config but did not look for the right thing!

Thank you so much :)

---

