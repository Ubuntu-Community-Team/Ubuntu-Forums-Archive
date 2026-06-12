---
title: "stop gedit from opening shortcuts(screenshot)"
date: 2010-09-24
forum: General Help
---

### Post by jklopez on 2010-09-24
i'm new to linux and i have ubuntu 10.04 installed via usb on WD external HD,now my problem is every time i double click on any of my shortcuts like the row you see(screenshot)near the bottom middle of the screen going upwards not the dock itself but the row of folders or the one on the top left(browse c:drive(wine) it allways comes back the way you see the window in the pic ,with that error,even if i open c:drive in the start menu and they worked fine before today and right clicking dosent give me the option to open with another app. what can i do...thnx

---

### Post by mc4man on 2010-09-25
Not sure if this relates to links from a dock (don;t use here), but if you wish open a terminal, run this, copy what shows uo and post
(line in question if there would be inode/directory=

```
gedit ~/.local/share/applications/mimeapps.list
```

---

### Post by jklopez on 2010-09-25
[Added Associations]
application/x-wine-extension-inf=wine.desktop;
text/x-ms-regedit=wine-extension-key.desktop;wine-extension-FLInstaller.desktop;wine.desktop;
application/x-ms-dos-executable=wine.desktop;
application/x-shellscript=gedit.desktop;
audio/x-wav=wine-extension-FSC.desktop;
inode/directory=gedit.desktop;wine.desktop;

         I hope this helps , i ran it in terminal and this came up in gedit , thnx 4 help'n imma noob:)

---

### Post by mc4man on 2010-09-25
This is a continuing bug that affects some people (and all in maverick - see edit in next my post for cause in maverick and probably lucid

2 ways to 'fix'

Right click on any folder -> Open With -> Other Application, scroll down and choose 'Open Folder' (screen

Or run the gedit command again and edit the file. 
Either just delete this line

>  inode/directory=gedit.desktop;wine.desktop;

or edit to look like this
```
inode/directory=nautilus-folder-handler.desktop;
```

=====================================================================

This may happen again, if so just do the r. click on a folder deal or move
 nautilus-folder-handler.desktop;
to the front of the line instead of deleting the line
(notice that when the line has multiple entries there are no spaces and each entry ends with a ;

Ex.
> inode/directory=nautilus-folder-handler.desktop;gedit.desktop;wine.desktop;

---

### Post by jklopez on 2010-09-25
that did the trick...thnx :)

---

### Post by jklopez on 2010-09-25
i did'nt delete it, i edited it with the 2nd option you gave me...

---

### Post by mc4man on 2010-09-25
> i did'nt delete it, i edited it with the 2nd option you gave me... 
That may be your best option (other than the r. click -> open with...

While gedit (gedit.desktop) really is of no use there (opening directories,), once an app is in that line it shouldn't inadvertently become the default again.

As mentioned this could happen again with something else - if so you know how to deal with now.

I think that this issue not being properly fixed and even much worse in the upcoming maverick is a bit of an embarrassment, just don't understand why it's still around

Edit: The culprit is the " Remember this application for "folder" files" box. It's enabled by default, unchecking will prevent this behavior
(hopefully will be patched to not have the box enabled or the option will be removed altogether

---

