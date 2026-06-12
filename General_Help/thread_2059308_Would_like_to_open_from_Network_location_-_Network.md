---
title: "Would like to open from Network location - Network doesn't show in OPEN dialog"
date: 2012-09-17
forum: General Help
---

### Post by 777funk on 2012-09-17
Is there a way to get Network to show in the OPEN from dialog in programs?

---

### Post by 777funk on 2012-09-18
btt

---

### Post by Morbius1 on 2012-09-18
I do not believe that there is a way to have "network" show up in the Open dialog because it's more of a "nautilus launcher" than a bookmark.

You will need to use Nautilus to browse to and connect to the remote share first and then go to your .gvfs folder to actually access the that share. You can only make it easier to access in the Open dialog if you create a bookmrk to the .gvfs location:
```
nautilus $HOME/.gvfs
```When Nautilus opens up bookmark it: Bookmark > Add Bookmark

You can even rename the Bookmark to "Network" at that point. It should show up in Nautilus and all your other applications on the left side panel. But remember that it's a bookmark to the mount location not a launcher to that remote location so you will need to mount it first.

---

