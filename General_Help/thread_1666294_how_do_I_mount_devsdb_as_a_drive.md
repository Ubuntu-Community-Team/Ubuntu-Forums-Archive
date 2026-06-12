---
title: "how do I mount /dev/sdb as a drive?"
date: 2011-01-13
forum: General Help
---

### Post by Meow27 on 2011-01-13
Hi, Im trying to mount /dev/sdb (the whole drive, not the partition!) to a folder (notably /media/folder) but I don't know what to do here

I'm trying to do this so i can access the drive from virtualbox using a ```
 
VBoxManage internalcommands createrawvmdk -filename /home/username/.VirtualBox/Harddisks/sdb.vmdk -rawdisk /dev/sdb
```
command, but It wont let me do it because virtualbox doesn't have permission to touch /dev/sdb directly. 
searching told me giving virtualbox root access is a bad idea, but i don't know how to get this done.

I want to do this so I can install OS's on separate drives without having to worry about grub messing anything. For this particular situation, I _don't_ want a virtual drive.

thanks in advance!

---

