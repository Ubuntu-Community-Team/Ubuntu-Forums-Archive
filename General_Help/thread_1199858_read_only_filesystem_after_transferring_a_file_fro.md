---
title: "read only filesystem after transferring a file from ntfs"
date: 2009-06-29
forum: General Help
---

### Post by pizzystrizzy on 2009-06-29
I'm a beginner, so I don't know where to get whatever error messages that would be most helpful to figure out how to fix my problem.

I have the 64 bit ubuntu 9.04 on an ext3 partition.  It was working fine until I copied some music files from my NTFS partition and saved them on my ext3 partition.  At that point, the partition became a "read only filesystem" and all applications stopped working.  When I tried to reboot, after I select Ubuntu from the boot menu, it just stops on a black screen. When I click on recovery mode, it gets stuck when it starts attempting to mount drives, saying that the various directories do not exist.

Is there a way I can fix this without reinstalling?  The bootloader is still working and my vista partition is still working as well (I am using it now to post this).

Thanks for any help,

Paul

---

### Post by iponeverything on 2009-06-29
Boot a live CD. Then open a terminal and run 

```
sudo fsck.ext3 /dev/<your device and partition>
```

If you not sure run:

```
sudo fdisk -l
```

to see a list of the partitions.

---

### Post by pizzystrizzy on 2009-06-29
Thanks!  I am downloading the ubuntu disk as we speak (I gave away the one I used to install).  In the meantime, I ran mountdiag in vista and got the following message:

"The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.11 software did not mount it because there is at least one incompat feature flag set.  The Ext2 IFS software does not implement:  
*needs_recovery*
Here we have an Ext3 file system which has transactions left in its journal.  A pure Ext2 driver must not access such a volume which is in that state (to prevent data loss!).  You may solve it by mounting it on Linux (which has a kernel with Ext3 support).  Be sure that you cleanly dismount it, before you shutdown Linux."

Is this useful information?  Does it change what I need to do to fix the problem?

---

### Post by Greyfox_75 on 2009-06-29
Basically something has been done that may have corrupted for ext3 filesystem.  IFS in Windows does not have the ability to "check" (fsck) your filesytem for these errors, so you need to do this from Linux.

Did you copy these files while you were in Vista or when you were in Ubuntu?  If transfering files in Windows caused this to happen you may want to consider removing the IFS driver to stop Vista from corrupting your Linux filesystems.

---

### Post by pizzystrizzy on 2009-06-29
I was in ubuntu.  I didn't even realize I was copying files -- I was just trying to play .wma music files that were on my ntfs directory.  It played like 3 and then everything stopped working.

---

### Post by iponeverything on 2009-06-29
I have never had an ext3 file system get corrupt on me. (I have seen several treads here on ext4 corruption) 

You may run some test on you hard drive to see if it reporting any errors.

---

### Post by Greyfox_75 on 2009-06-29
"It played like 3 and then everything stopped working"

Ouch maybe sounds more like hard drive failure then

```
sudo apt-get install smartmontools
sudo smartctl --all /dev/<yourdrive ex. sda>
```

---

