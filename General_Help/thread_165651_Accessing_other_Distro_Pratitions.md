---
title: "Accessing other Distro Pratitions"
date: 2006-04-24
forum: General Help
---

### Post by Nano Geek on 2006-04-24
On my computer I have:
[LIST]
[*]Ubuntu 5.10 - My Default Distro
[*]Ubuntu 6.06
[*]Fedora Core 5
[*]SUSE 10.0
[/LIST]
I installed Ubuntu 5.10 first and I can't access my other partitions on my hard drive, so if anybody knows of a way to get them working, I would be grateful.
Thanks

---

### Post by Sutekh on 2006-04-24
First you should try to locate them using
```
sudo fdisk -l
```
which will list the partitions on your hard discs.

Then you can mount them using these commands, if say Dapper was on /dev/hda2, you could create a folder for the Dapper partition to be mounted to, say /media/dapper.  Then you could mount it there.
```
sudo mkdir /media/dapper
sudo mount /dev/hda2 /media/dapper -t ext3 -o defaults
```
The other partitions can be mounted in a similar way

---

### Post by Nano Geek on 2006-04-25
Thanks

---

