---
title: "Moving from ntfs to ext3 - windows to linux"
date: 2009-08-15
forum: General Help
---

### Post by tjb_15 on 2009-08-15
This has probably been posted hundreds of times but I need some Input. I have decided that I no longer need windows for most tasks. The only thing I will need it for is games (which I barely ever play). I but here is my plan:

```

750GB OS Drive

Partition         File System      Size (GB)     For
sda1              NTFS             74.84          Windows XP
sda2              NTFS             100.00         Windows 7   
sda3              extended         103.81
    sda5          ext3             100.00         Linux Mint 
    sda6          linux-swap       3.81
    sda7          fat32            40.00          Profiles, Game Data, Transfers Between OS's

```
*edit: Moved the fat32 partition in to the extend partition.*
```

640GB Data Drive

Partition         File System      Size (GB)     For
sdb1              ext3             596.17        DATA

```

I don't need access to the data drive from windows since I will be using it for games. I will also try "Ext2 Installable File System for Windows" so I can access it. It looks like I will have to use command when formating in order for it to work:

```
mke2fs -I 128 /dev/sdb1
```

If I don't do this, windows will want me to format the drive. I tested this in virtual box. I had to use the mountdiag.exe to determine why it wanted me to format it. It has to have a Inode size of 128.

Thanks,
TJB

---

### Post by Hendronicus on 2009-08-15
I have used ext2ifs and it works well with the exception that in my case it sets the last access time for the partition into the future. fsck fixes it in the background every time I go back to Linux, though. YMMV

---

### Post by tjb_15 on 2009-08-16
This:
```
mke2fs -I 128 /dev/sdb1
```
Will make the file system ext**2**. So today I upgraded to ext3 with this:
```
tune2fs -j /dev/hdb1
```
I could have avoided this by adding -j to the original. Other then that I think I have accomplish this task. :popcorn: :) :P

---

