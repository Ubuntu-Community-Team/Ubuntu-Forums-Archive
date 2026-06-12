---
title: "easiest way to find files in a folder/directory?"
date: 2010-10-10
forum: General Help
---

### Post by fuzzylogic25 on 2010-10-10
With Windows XP, I just right clicked a folder/directory and pressed FIND then I could search for whatever file/folder name i wanted to. I could even do custom searches based on the size, modification date etc.

How do you do this on Ubuntu? There doesnt seem to be a way to easily do it like this. So far i found PLACES -> SEARCH FOR FILES but that means I have to go into the directory i want. Where as I would much rather be browsing through directories and THEN want to quickly search in a particular folder. The SEARCH FOR FILES method in PLACES just wastes more time.

---

### Post by juil on 2010-10-10
For myself, I find that the fastest way to find a file is to open a terminal and type:

```
locate -i *filename*
```

The -i means that ignores upper/lower cases.
It displays the results in a split second.

For example, when i typed *[COLOR="Blue"]locate -i avatar[/COLOR]* it gave me this result in a split second:

```
skynet@skynet-desktop~ $ locate -i avatar
/home/skynet/Pictures/avatar
/home/skynet/Pictures/avatar/paper-mario.jpeg
/home/skynet/Pictures/avatar/pm..jpg
/home/skynet/Pictures/avatar/pm.xcf
/home/skynet/Pictures/avatar/pm1..jpg
/home/skynet/Pictures/avatar/pmdeviant..jpg
/usr/lib/python2.6/dist-packages/butterfly/avatars.py
/usr/lib/python2.6/dist-packages/butterfly/avatars.pyc
/usr/lib/python2.6/dist-packages/telepathy/_generated/Account_Interface_Avatar.py
/usr/lib/python2.6/dist-packages/telepathy/_generated/Account_Interface_Avatar.pyc
/usr/lib/python2.6/dist-packages/telepathy/_generated/Connection_Interface_Avatars.py
/usr/lib/python2.6/dist-packages/telepathy/_generated/Connection_Interface_Avatars.pyc
/usr/share/pixmaps/pidgin/toolbar/22/select-avatar.png
/usr/share/pyshared/butterfly/avatars.py
/usr/share/pyshared/telepathy/_generated/Account_Interface_Avatar.py
/usr/share/pyshared/telepathy/_generated/Connection_Interface_Avatars.py

```

---

### Post by stinkeye on 2010-10-10
If your browsing with nautilus just start typing and it will highlight any 
files which match your input in that folder. Click the down arrow to go to the next match.

---

### Post by oopsie on 2010-10-10
Click the little magnifying glass icon

---

