---
title: "Mount ~/Desktop as Desktop after wiping out my ~"
date: 2010-02-13
forum: General Help
---

### Post by terminator14 on 2010-02-13
I was deleting some files in terminal like I've done hundreds of times before and basically ended up running something like:

```
cd /folder/I/need/to/delete/content/of
sudo rm -rf *
```
which did exactly what I needed (the files belonged to root so yes, I did need the sudo part). Next I needed to delete some more files so in a new terminal I just hit the up arrow and added the name of the new folder. Unfortunately for me this is what I ended up with:

```
~$ sudo rm -rf **[COLOR="Red"]*[/COLOR]** /new/folder/I/needed/deleted
```

And that's how I wiped out my home dir :). Fortunately I keep backups of everything on external drives. All hidden config files of programs also stayed intact since rm didn't see them. Since all my home dir's folders were wiped out (Downloads, Desktop, Docs, Videos, etc...) I created a new user to see what all those folders were (I couldn't remember all of them since I don't use them all) and copied the empty folders over to my account. I also changed the ownership on the folders to my user. I would have thought that's all I would have to do to have my account function like new again but my Desktop seems to have ~ mounted on it instead of ~/Desktop. That means looking at my Desktop I can see folders like Downloads, Desktop, Documents... which are in my ~ folder. If I do a:

```
ls ~/Desktop
```

the folder is empty. Also if I click Places from the menu above and hit "Desktop" I get the ~ folder as well - not ~/Desktop like I should.

How do I fix this? Any ideas? Oh and does rm keep any kind of logs? I don't feel like doing extensive low level data recovery but it would be nice to know exactly what I deleted on my Desktop - I don't remember if anything was important. I'm sure if anything was I would have backed it up but it would still let me relax if I knew nothing was lost that I needed.

---

### Post by jken146 on 2010-02-13
Run ```
gconf-editor
```
and look under apps/nautilus/preferences for the option desktop_is_home_dir . Set it to false and see if that solves the problem (make sure that ~/Desktop exists too).

---

### Post by terminator14 on 2010-02-13
Sounded like what I was looking for but when I checked, it was set to false already. I set it to true and logged out and in to see if anything changes switching the option on/off. Nothing changed. I set it to false again and logged off and on again. Still the same. Any other ideas?

---

### Post by terminator14 on 2010-02-13
Here we go... This looks promising. My ~/.config/user-dirs.dirs file says:

```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"

```

lets see if I can fix that.

---

### Post by jken146 on 2010-02-14
XDG_DESKTOP_DIR="$HOME/Desktop"

is what you want.

---

### Post by terminator14 on 2010-02-14
The file is easy enough to edit by hand but to save a few seconds I just copied it from the new user which read:

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

after logging out and in again - problem solved. Anything else that could have messed up from a deleted home dir?

---

### Post by Richard1979 on 2010-02-14
App settings in .appname directories maybe.
Such as ~/.wine or ~/.firefox etc - dunno.
Wish people would use the -r switch on rm more carefully though (or more correctly, the -f).

---

### Post by terminator14 on 2010-02-14
> **Richard1979 said:**
> App settings in .appname directories maybe.
Such as ~/.wine or ~/.firefox etc - dunno.
Wish people would use the -r switch on rm more carefully though (or more correctly, the -f).

Nope. rm didn't see the hidden .appname folders so they were all still intact. 

The external drives I have my backups on are actually more like one 4TB NAS with RAID 5. It's always mounted in my /media dir so this incident kind of made me think of what would happen if I ended up running "rm -rf /". I can't think of any reason that I ever would even by mistake, but that would cause several TB on my NAS to get wiped out. Because of this, since yesterday I have installed safe-rm from [http://code.google.com/p/safe-rm/](http://code.google.com/p/safe-rm/) that double checks what is being erased before erasing it. I configured it to ignore erase commands like "rm -rf /" or "rm -rf /media" and such. I'm also looking into using libtrash to copy any files I use rm on into a trash folder. I recommend others that have important information either in their home folder or mounted on the filesystem somewhere to use these tools as well (at least the safe-rm one which seems to work - I'm having trouble setting up libtrash). Thanks guys for your help.

---

