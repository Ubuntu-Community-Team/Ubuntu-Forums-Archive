---
title: "DD Command Issue"
date: 2011-05-31
forum: General Help
---

### Post by likelylad on 2011-05-31
I am completely new to Linux, so please pardon my ignorance on the subject. 
 
I am copying to make an exact copy of a Windows formatted 1.44 HD (High Density) floppy disk. From what I have read the DD command in Linux will do the job for me.
 
I am trying to make an exact copy from 1 floppy disk to another floppy disk.
The floppy disk drives are USB one's.
 
Once I put the disks into the drives, they are showing up in:
/media/BOOTDISK and /media/disk
 
I have tried the following comand
dd if=/media/BOOTDISK of=/media/disk
 
but absolutely nothing happens, it just says "/media/disk exists"

---

### Post by m_duck on 2011-05-31
I think with dd you would need to refer to the device names rather than the mount points. I also think that you will need to unmount them before this is possible.

Run the command ***mount*** to see what the device names for the disks are, then you can probably do the backup like this:```
dd if=/dev/fd0 of=/dev/fd1
```Where /dev/fd0 and /dev/fd1 are the devices you found in the previous step.

If you were going to be copy the disk multiple times it would probably be easiest to make an on-hard-disk backup of the floppy, using two commands - one to save the floppy image, and the next to write it to the floppys:```
dd if=/dev/fd0 of=~/floppy.img
```
```
dd if=~/floppy.img of=/dev/fd1
```

Be ***[COLOR="Red"]VERY CAREFUL[/COLOR]*** when using dd and devices though since it's would not be difficult to kill your installation/lose all your files if you used the wrong identifiers! Make sure you are positive which devices you want to use [/covering my backside].

---

### Post by likelylad on 2011-05-31
Perfect thank you.:P
 
1) Ran the mount command to see the drives
2) unmounted them
3) had to use sudo dd if=/dev/sdb of=/dev/sdc

---

