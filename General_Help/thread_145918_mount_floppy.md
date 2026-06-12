---
title: "mount floppy"
date: 2006-03-17
forum: General Help
---

### Post by milen on 2006-03-17
What is the exact command i should type in the terminal in order to make this, well, system  mount my floppy so that I could copy some Word files to my hard disk?
Thanx

---

### Post by steve.horsley on 2006-03-17
Try this:
**mount -t auto /dev/fd0**
but you may need this:
**mount -t vfat /dev/fd0**

---

### Post by hajk on 2006-03-17
A floppy disk can be mounted by clicking on the Floppy icon in the Places --> Computer menu. 

Proper operation requires that an update of the "pmount" package from the backports repository is installed -- so, if necessary, uncomment the backport repositories in /etc/apt/sources.list, and in Synaptic do a reload and install the upgradable pmount packages. 

I recommend that you change the floppy entry in /etc/fstab to

/dev/fd0     /media/floppy0    msdos    rw,users,noauto,umask=0000    0     0

(instead of msdos you may also use vfat, they're synonyms). You may have to
make sure that the permissions for the mount point /media/floppy0 allow writing
with "sudo chmod 777 /media/floppy0", since otherwise the ``rw'' option in /etc/fstab wouldn't have any effect.

Have fun!

---

### Post by milen on 2006-03-17
Doesn't work. Man, this Ubuntu is absolute bullshit. One should be crazy to switch to it from Windows.

---

### Post by StefanoCole on 2006-03-17
> Man, this Ubuntu is absolute bullshit. One should be crazy to switch to it from Windows

Please do not offend.

---

### Post by hajk on 2006-03-17
The original poster sounds frustrated... and Linux can indeed appear a bit daunting when coming from Windows.

What exactly didn't work?

---

### Post by void_false on 2006-03-17
LOL. At first I thougt it was smart guy that wanted to learn about bash.
But surprisingly he turned to be just a windoze lamma.:mrgreen:

---

