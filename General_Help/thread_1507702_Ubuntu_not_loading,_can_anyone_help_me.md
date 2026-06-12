---
title: "Ubuntu not loading, can anyone help me?"
date: 2010-06-11
forum: General Help
---

### Post by robot_chicken_parm on 2010-06-11
after a fresh install of ubuntu karmic, it worked for a little while, untill after using the update manager to get up to date, after which i restarted as required, and the computer stopped on a black screen with two lines of white type white type that reads:

```

fsck from util-linux-ng 2.16
/dev/sda1: clean, 130994/2351104 files, 7790779400025 blocks

```

it seems the only thing i can do is turn off the laptop from the power button.  i would really appreciate it if anyone can help me.  much appreciated.  i love you ubuntuforums!

---

### Post by robot_chicken_parm on 2010-06-11
oh and also i tried restarting in recovery mode, and i got a whole bunch of white text on a black screen and at the end was basically the same thing, and then...  nothing.  pressing enter does nothing.  just trying to give as much detail on the prob as possible.  thanks guys.

---

### Post by garvinrick4 on 2010-06-11
In Live CD what are results of:

```
sudo fdisk -l 
```  (small L)

---

### Post by robot_chicken_parm on 2010-06-12
i put it in and got this:

```
fdisk: invalid option- '1'

Usage:  fdisk[-b ssz] [-u] DISK              Change Partition Table
            fdisk -l [-b ssz] [-u] DISK          List Partition Table(s)
            fdisk -s PARTITION                   Give Partition Size(s) in Blocks
            fdisk -v                                    Give fdisk Version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u:  give Start and End in sector (instead of cylinder) units
-b 2048:  (for certain MO disks) use 2048-byte sectors
```

---

