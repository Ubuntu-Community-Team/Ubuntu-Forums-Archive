---
title: "Partition permission"
date: 2009-11-22
forum: General Help
---

### Post by Jareb on 2009-11-22
I want to set up a dual boot. I have Partition Editor and have found the partitions, but they are locked. How can I unlock them? I've looked for some kind of permission to give myself (or something like that), but can't seem to figure it out (Ubuntu 9.04).

---

### Post by Boulemans on 2009-12-06
Don't know the best solution, but I would do it with fstab.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) for mor info.

you can read these pages too:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) for more information about mounting

[http://en.wikipedia.org/wiki/File_system_permissions](http://en.wikipedia.org/wiki/File_system_permissions) for more information about permissions

I'm sorry to say i'm just as noob in this as you, so i can't give you a clear and 100% solution. But I did get it to work.

---

### Post by Zoot7 on 2009-12-06
What sort of partitions are they? What filesystems have they?

Could you post the output of
```
df -h
```
and 
```
sudo fdisk -l
```

---

### Post by oldfred on 2009-12-06
Are you using the liveCD of Ubuntu or gparted? You cannot edit partitions that are mounted,i.e. your working copy. You can review them but not make changes with the download gparted unless you have a second drive and can unmount all the partitions on that drive.

---

