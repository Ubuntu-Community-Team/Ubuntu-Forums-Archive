---
title: "fstab being ignored for external vfat USB? Or Nautilus naughtiness?"
date: 2012-04-23
forum: General Help
---

### Post by doubi on 2012-04-23
Hi all,

I hope I'm missing something obvious here...

The operative line in my fstab is this:
```

UUID=0123-4567 /media/clip     vfat    noauto,user,rw,uid=1000,dmask=027,fmask=137     0       2

```/media/clip is always present in my list of "Places" in Nautlius. 

However, when I attach the device, it's always mounted at /media/<label>, where <label> is the device label, and is often a string of random junk (usually unrenderable unicode, last was "68&user" or something).

Whenever I try to access the 'clip' location in Nautilus with my device connected I get this error message:
```

mount: /dev/sdb already mounted or /media/clip busy
mount: according to mtab, /dev/sdb is already mounted on /media/clip

```This is right after a reboot, so mtab shouldn't be confused by anything else having happened.

I should point out that I **can** still access the device via /media/clip on the command line, and e.g. gPodder can sync to /media/clip/PODCASTS. 

However Nautilus seems to insist on regarding the device as mounted at /media/<label> and won't acknowledge its presence at /media/clip as required in my fstab.

Yes, 0123-4567 is really the silly UUID of my Sansa Clip:
```

doubi@doubuntu1:~$ sudo blkid /dev/sdb
/dev/sdb: LABEL="CLIPPY" UUID="0123-4567" TYPE="vfat" 

```In trying to finally get to the bottom of this, I just today gave the device the label 'clippy'. I've tried both uppercase and lowercase versions with LABEL="" in fstab instaed of using the UUID, but it hasn't helped.

All the guides and help around make fstab seem pretty straight forward, and given that I *can* access the device via the commandline at the mount point specified, I'm just confused as to why Nautilus won't play ball?

Ubuntu 10.04, Gnome 2.30.2, Nautilus 2.30.1. Any insights mucho gracias'd :-)

---

### Post by ajgreeny on 2012-04-23
There is no need to add any lines to your fstab for a fat32 external disk, as it will by default be mounted as read/write either when plugged in, or at boot time if it is attached then.

As you have seen, the disk already mounts automatically using the partition label as ther mountpoint, so if you want to mount it at a particularly named mountpoint every time it is attached, just label the partition with the name you want for the mountpoint, which you can do with gparted, and comment out that unnecessary line in fstab.

A line in fstab would only be needed for an internal disk formatted with a fat32 filesystem, not an external USB disk/partition.

---

### Post by gsgleason on 2012-04-23
The mechanism that monitors for volumes and mounts is different than the mechanism that reads fstab.

---

### Post by doubi on 2012-04-23
> **ajgreeny said:**
> There is no need to add any lines to your fstab for a fat32 external disk, as it will by default be mounted as read/write either when plugged in, or at boot time if it is attached then.

[...]

A line in fstab would only be needed for an internal disk formatted with a fat32 filesystem, not an external USB disk/partition.
Hm, fancy that!

I think I started using fstab because I had an issue with r/w permissions at one point. And as I mentioned above, the volume label seems to randomly change sometimes, so I thought I could have a permanent solution using fstab. I'll just set it back in future. Thanks ajgreeny!

Final note for anyone coming after who like me was having trouble renaming the volume: most searching around on re-labelling vfat / FAT32 volumes finds recommendations of mtools' mlabel command. Problem is that will uppercase any label you give it, leading some people to [quite remarkable workarounds]("http://embraceubuntu.com/2006/03/01/editing-fat32-partition-labels-using-mtools/#comment-141763").

Solution: use dosfslabel instead ([thanks to this post]("http://ubuntuforums.org/showthread.php?p=10286651#post10286651")). Here are the (sometimes mistaken) commands I used, and their output:
```

doubi@doubuntu1:~$ sudo umount /dev/sdb
doubi@doubuntu1:~$ dosfslabel /dev/sdb
open: Permission denied
doubi@doubuntu1:~$ sudo dosfslabel /dev/sdb
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:43/4e, 72:4c/4f, 73:49/20, 74:50/4e, 75:20/41, 76:20/4d, 77:20/45
  Not automatically fixing this.
CLIP       
doubi@doubuntu1:~$ sudo dosfslabel /dev/sdb clip
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:43/4e, 72:4c/4f, 73:49/20, 74:50/4e, 75:20/41, 76:20/4d, 77:20/45
  Not automatically fixing this.
doubi@doubuntu1:~$ sudo blkid /dev/sdb
/dev/sdb: LABEL="clip" UUID="0123-4567" TYPE="vfat"
```

---

