---
title: "&quot; PLACES&quot; cannot open Folders"
date: 2010-10-31
forum: General Help
---

### Post by Dyffo on 2010-10-31
I have a strange problem that has "Just" appeared.  When I go to " Places" and click on a folder Videos for example - the display shows "No Images" however if I click on the image icon - all the videos on file are displayed.
If I insert a USB memory stick -  open this - ALL my folders are displayed as normal in the side pane.
Equally if I go to " Computer " open this - all folders are displayed in the side pane.
It is just an annoying problem - has anyone any ideas on how to solve this ?

---

### Post by zvacet on 2010-10-31
Are you saying that you can not oopen folder from "Places"? If that is problem type in terminal

```
grep -i directory .local/share/applications/mimeapps.list

```

and post output here.

---

### Post by Dyffo on 2010-10-31
> **zvacet said:**
> Are you saying that you can not oopen folder from "Places"? If that is problem type in terminal

```
grep -i directory .local/share/applications/mimeapps.list

```

and post output here.

mike@mike-desktop:~$ grep -i directory .local/share/applications/mimeapps.list
inode/directory=eog.desktop;nautilus-folder-handler.desktop;vlc.desktop;kde4-kaffeine.desktop;kde4-kmplayer.desktop;gimp.desktop;wine.desktop;brasero.desktop;file-roller.desktop;
As requested:- any help much appreciated.

---

### Post by mc4man on 2010-10-31
this is an unattended and annoying bug - 
You can edit the file to look like this (first listed is the default
```
inode/directory=nautilus-folder-handler.desktop;eog.desktop;nautilus-folder-handler.desktop;vlc.desktop;kde4-kaffeine.desktop;kde4-kmplayer.desktop;gimp.desktop;wine.desktop;brasero .desktop;file-roller.desktop;
```
or see here
[http://ubuntuforums.org/showthread.php?t=1609138](http://ubuntuforums.org/showthread.php?t=1609138)

---

### Post by Dyffo on 2010-10-31
r.click on any folder you can find -> Open With -> Other Application
scroll down and pick 'Open Folder' -> open

This will return the default folder handler back to nautilus.
(if no folders around on desktop then just create one to use w/ r. click -> Create Folder

This solved my problem - Many thanks

---

