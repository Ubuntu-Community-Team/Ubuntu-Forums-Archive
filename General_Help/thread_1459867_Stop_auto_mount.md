---
title: "Stop auto mount"
date: 2010-04-22
forum: General Help
---

### Post by Daskies on 2010-04-22
I did a pretty thorough search and didn't find anything so I figure I'll just ask: is there a way to stop a partition from auto-mounting? It seems pretty easy to get it to auto-mount through a few tools, but I can't get it to unmount because it's "in use." I'm assuming I'll have to do this through a live CD program or something similar, but I have no idea how to go about doing this.

---

### Post by darolu on 2010-04-22
What partition do you want to stop auto-mounting?

Post the following info, it will help us to tell you how to do it (all form a terminal):
```
$ sudo fdisk -l
```
```
$ gedit /etc/fstab
```

---

### Post by rnerwein on 2010-04-22
hi
the tline with the partition in /etc/fstab should have the option "noauto" included eg:

/dev/sda6 /suse_root ext3 defaults,suid,[COLOR=Red]noauto[/COLOR]

to mount it type in a terminal:
sudo mount /suse_root

ciao

---

