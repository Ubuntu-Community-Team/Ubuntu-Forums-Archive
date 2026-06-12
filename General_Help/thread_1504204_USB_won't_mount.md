---
title: "USB won't mount"
date: 2010-06-07
forum: General Help
---

### Post by The_Eggert on 2010-06-07
Hello :)
Here the other day, my USB-stick just stopped working, and I have no idea why :/
The first thing I tried, was plugging it in different computers, with different OS's, and no luck.
In Ubuntu, when I plug it in, it does show a difference with "lsusb", it does appear in "Disk Utility", and it does appear in "Commputer". However I can't open it from "Computer", and when I look at it in "Disk Utility", it says "No media detected":confused:
Does anyone have any idea as to why this has happened all of a sudden? Whether it is simply broken, or if it can be fixed?

---

### Post by dcstar on 2010-06-08
> **The_Eggert said:**
> Hello :)
Here the other day, my USB-stick just stopped working, and I have no idea why :/
The first thing I tried, was plugging it in different computers, with different OS's, and no luck.
In Ubuntu, when I plug it in, it does show a difference with "lsusb", it does appear in "Disk Utility", and it does appear in "Commputer". However I can't open it from "Computer", and when I look at it in "Disk Utility", it says "No media detected":confused:
Does anyone have any idea as to why this has happened all of a sudden? Whether it is simply broken, or if it can be fixed?

Plug it in, start **gparted** and find the /dev designation of it, then open a terminal and:

```
sudo fsck /dev/whatever-it-is
```
If it is a NTFS partition, then install the **ntfsprogs** package and then:
```
sudo ntfsfix /dev/whatever-it-is
```

Unplug it, plug it back in and see what happens.

---

### Post by The_Eggert on 2010-06-08
> **dcstar said:**
> Plug it in, start **gparted** and find the /dev designation of it
One on my problems is, that it doesn't show up in gparted :/
But when I look in the /dev folder, and plug in my USB, sdc appears, so I guess that the USB must be "assigned" to sdc?

> **dcstar said:**
> 
```
sudo fsck /dev/whatever-it-is
```
If it is a NTFS partition, then install the **ntfsprogs** package and then:
```
sudo ntfsfix /dev/whatever-it-is
```

Yet again, there is a problem :P
I don't remember what filesystem I have/had on it..
When I run *sudo fsck /dev/sdc*:
```

fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No medium found while trying to open /dev/sdc

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```
When I run *sudo ntfsfix /dev/sdc*:
```

Mounting volume... Error opening partition device: No medium found.
Failed to startup volume: No medium found.
FAILED
Attempting to correct errors... Error opening partition device: No medium found.
FAILED
Failed to startup volume: No medium found.
Volume is corrupt. You should run chkdsk.

```

When I then try *chkdsk* in Windows, I get (and this is translated from Danish ;))
```

Cannot open volume for direct access.

```
Don't know it that help anyone..?:confused:

---

### Post by The_Eggert on 2010-06-12
Sooo...Bump?

---

