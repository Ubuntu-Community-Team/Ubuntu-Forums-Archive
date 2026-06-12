---
title: "Ubuntu, Ext Hd is inviible Seagate"
date: 2010-07-04
forum: General Help
---

### Post by su-37 on 2010-07-04
Hey, recently reinstalled 10.04 and after using it for a while i was unable to see my ext hd. The hd lights up and the disk is even spinning but it doesnt show up on the desktop or when i go looking through the filesystem. Any ideas?
Thanks in advance

---

### Post by CharlesA on 2010-07-04
Does it show up in fdisk?

```
sudo fdisk -l
```

---

### Post by cariboo on 2010-07-04
Please ask support questions in the support forums. Moved to General Help.

---

### Post by su-37 on 2010-07-05
Thanks and sorry about posting it in the wrong area. I entered the code and this is what i got.



"Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001c92a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38163   306537472   83  Linux
/dev/sda2           38163       38914     6031361    5  Extended
/dev/sda5           38163       38914     6031360   82  Linux swap / Solaris

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS
"

I think the top is my hd and the bottom is the external.
ps how do you enter the code the way you did? ie recessed?

---

### Post by CharlesA on 2010-07-05
Use the [ code ] [ /code ] tags (remove spaces).

Guessing the external is the NTFS one.

You can try this:

```
sudo mount -t ntfs-3g /dev/sdc1 /mountpoint
```

I usually mount devices temporarilly to /cdrom/ since I don't use the cdrom all that much and it's easy to find. :-)

---

### Post by su-37 on 2010-07-05
Tried that and got ```

[sudo] password for james: 
NTFS signature is missing.
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

---

### Post by su-37 on 2010-07-06
Weirdly enough i looked at it on another computer and it couldn't see it, but i did see the hard drive through the disk utility.

---

