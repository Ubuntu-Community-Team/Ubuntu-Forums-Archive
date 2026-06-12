---
title: "new drive, partitioning, NTFS problem"
date: 2009-09-25
forum: General Help
---

### Post by akakingess on 2009-09-25
Hello all,

First of all, I would like to thank those of you that volunteer your time to assist us noobies, but now on to my question of the day. I added a drive (old 25 Gb drive) to my current desktop system to have as a central storage/backup location for everyone to use for the obvious purposes. Now, I have tried to use GParted (while logged into Ubuntu) to format this old drive and it will not give me the option to format it NTFS (it is ghosted). I can format it Fat32 which I have done and then attempted to share it, but then it disappears from Ubuntu and I have to start the whole routine over again. There is a 99% chance this is user error on my part, but could anyone let me know what I am doing wrong or what step I am missing?  Any assistance would be greatly appreciated!

---

### Post by nikhilk on 2009-09-25
What mechanism are you using to share the disk FTP, Samba or something like that?

But regardless, are you able to mount and use the disk as a regular local disk (no sharing or anything else) after formatting it? Can you read/write files normally without any problems?

---

### Post by akakingess on 2009-09-25
I am going to use Samba and have that all set up, i can print to Windows shared printers and the Windows machines see the Ubuntu desktop, but when I try to open the drive after doing the formatting and adding the sharing (basically allowing everyone to see/write to it) then it unmounts and I can no longer see it even with Ubuntu. Do those answer your questions?  Also, keep in mind I am at work so trying anything would have to wait til I get home tomorrow, but I will take all suggestions and try each of them once I get back in front of the machine in question.

Edit: Am I supposed to do something in regards to mount point or something of that nature that I am missing?

---

### Post by nikhilk on 2009-09-25
If it is mounting correctly and then simply unmounting on its own there could be a problem. This is just a guess but maybe since the disk is old there might be some problem, bad sectors or something like that.

After freshly formatting the disk but before mounting it run fsck.vfat on it to check for any errors
```
sudo /sbin/fsck.vfat -V <the fat32 device>
```

---

### Post by akakingess on 2009-09-25
Thnaks again, now for the <the fat32 device> should I use what I named it or media/drive/sdab or something of that nature?  Remember, I am fairly new to linux, but have learned quite a bit, so a short answer should suffice.  Also, do I need to use a different utility other that GParted to fix the fact that I can't format NTFS which is really what I want it formatted as?

---

### Post by nikhilk on 2009-09-25
The device will be the the one corresponding to your 25GB hard drive, something like /dev/sdb1.

GParted should work fine for formatting partitions as NTFS. Make sure that you have the package "ntfsprogs" installed.

---

### Post by akakingess on 2009-09-25
Thank you nikhilk, that must be why I don't have the option to format as NTFS, yet.  Hopefully that will solve all of my problems. Thanks to all for your help!

---

