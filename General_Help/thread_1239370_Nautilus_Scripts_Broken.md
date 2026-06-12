---
title: "Nautilus Scripts Broken?"
date: 2009-08-13
forum: General Help
---

### Post by KlinerDraken on 2009-08-13
Ever sense I started using Ubuntu 9.04 I can't get any Nautilus Scripts to work. I used them in 8.10 with no problems. I have tried new scripts and I have even reinstalled Ubuntu but they just not working for me. :confused:

Anyway to get them working again?


Thanks

---

### Post by Johnny B on 2009-08-13
did you put them in ~/.gnome2/nautilus-scripts?
then run: > chmod +x -R ~/.gnome2/nautilus-scripts

---

### Post by KlinerDraken on 2009-08-13
The scripts show up in the context menu and I think they have to be executable to show up. But I ran "chmod +x -R ~/.gnome2/nautilus-scripts" just to make sure, but they still do nothing when I click on them. :(

---

### Post by KlinerDraken on 2009-08-13
Is anyone else able to run Nautilus Scripts?

---

### Post by kaibob on 2009-08-13
> **KlinerDraken said:**
> Is anyone else able to run Nautilus Scripts?
I use many Nautilus scripts on a daily basis, and they work fine.

---

### Post by KlinerDraken on 2009-08-14
looks like any script that has script-worker in it failes with the error "script-worker: command not found"

---

### Post by fragos on 2009-08-14
I've script-worker located in /usr/bin. I looked at it and it appears to have something to do with the ubuntu-tweak package.

---

