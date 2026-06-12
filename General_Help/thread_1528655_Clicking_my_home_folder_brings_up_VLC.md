---
title: "Clicking my home folder brings up VLC"
date: 2010-07-11
forum: General Help
---

### Post by SirPaPa on 2010-07-11
Hello I'm using Ubuntu 10.04 and when ever i click my home folder VLC Media Player launches instead. 
I had the same problem but with Totem instead back a few Ubuntu versions ago. 

Need help with this one now. 

Thank you.

---

### Post by mc4man on 2010-07-11
Try right clicking on a folder on your desktop, (if you don't have any then create one). and go -> 'open with ->  Other Application' and there should be a choice in the list  of 'Open Folder'.
Choose that and see.

Otherwise try this in terminal
```
gedit ~/.local/share/applications/mimeapps.list
```

Look for the line inode/directory= and put this directly after the =
```
nautilus-folder-handler.desktop;
```

Ex.
> inode/directory=nautilus-folder-handler.desktop;totem-xine.desktop;mediainfo-gui.desktop;vlc.desktop;
notice there are no spaces between entries, each ends with a ;

---

### Post by TwistedWeezar on 2011-02-20
I had the same problem and the second solution solved it.
Thanks. :)

Edit: Maybe someone can mark this as solved.

---

