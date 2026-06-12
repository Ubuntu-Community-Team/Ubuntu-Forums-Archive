---
title: "Filesystem link"
date: 2009-06-28
forum: General Help
---

### Post by chmacka on 2009-06-28
How can I create desktop link to Filesystem?

I found how to add Trash, Computer, Home & Mounted Volumes links to Dekstop in Configuration Editor, but not the Filesystem link.

---

### Post by t4thfavor on 2009-06-28
ln -s something something/else I believe this creates a ling called something, pointing at something/else (or its the other way around.

either way, if you need a link to /media/disk you shoud do something like this.

ln -s /home/u/disk_drive /media/disk

---

### Post by chmacka on 2009-06-29
> **t4thfavor said:**
> ln -s something something/else I believe this creates a ling called something, pointing at something/else (or its the other way around.

either way, if you need a link to /media/disk you shoud do something like this.

ln -s /home/u/disk_drive /media/disk
I solved it last night:

You create a Desktop launcher with these options:

1) Type: **Location**
2) Command: **/**

And then I found the Filesystem icon in /usr/share/icons

---

