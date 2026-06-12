---
title: "Make multiple disks act as one"
date: 2011-06-21
forum: General Help
---

### Post by BrokenKingpin on 2011-06-21
I have a home media server that has 4 hard disks in it. The first is an 80 GB OS disk, and the other 3 are data disks (all 500 GB, but different makes/models).

Is there an easy way to make Ubuntu see the 3 data disks as one disk/partition? Can I do this with LVM, or do I need to use RAID/JBOD for something like this? It would also be nice if I could add an additional disk later on without having to break the existing configuration. Also, if would be awesome if I didn't have to format the existing data to get them into the new configuration.

Any help would be great, thanks!

---

### Post by grahammechanical on 2011-06-21
This link might help:

[http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29]("http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29")

Regards.

---

### Post by BrokenKingpin on 2011-06-21
Okay, so LVM seems to be what I am looking for, but I have no idea where to start? Is there a GUI tool that will allow me to easily create an LVM with the three disks... and will I have to format them to setup the LVM?

---

### Post by BrokenKingpin on 2011-06-21
Anyone?

---

### Post by BrokenKingpin on 2011-06-24
I am marking this as solved. I didn't want to mess around with LVM just so I didn't accidentally blow away my data.

What I ended up using was symlinks to the other disks form the main one. It is a dirty solution, but will have to do until I get all my data backed up and trying my luck with LVM.

---

### Post by linuxford on 2011-07-29
There is another thread that I think that will be of help.
[http://ubuntuforums.org/showthread.php?t=1759896&highlight=lvm+gui]("http://ubuntuforums.org/showthread.php?t=1759896&highlight=lvm+gui")

Basically, go to package manager and add "system-config-lvm" and then type "system-config-lvm" at a regular linux terminal shell. This loads a gui tool.

---

