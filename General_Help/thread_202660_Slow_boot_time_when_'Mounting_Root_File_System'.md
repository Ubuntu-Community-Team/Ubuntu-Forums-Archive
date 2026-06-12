---
title: "Slow boot time when 'Mounting Root File System'"
date: 2006-06-23
forum: General Help
---

### Post by Zandrox on 2006-06-23
I recently made some hardware configuration chagnes to my system.  I took a DVD-R drive and two IDE hard drives and added them to an existing system that had a single DVD-RW and a single SATA drive.  Since that time booting the system has increased by an order of magnitude.  The sequence seems to pause on "Mounting root file system".  I don't think that this should be happening, but as I am fairly new to linux I dont know.

Everything works except for the long boot time.  But since I know just enough to be dangerous to myself I am assuming that it is correct but posting what changes I have made here to be sure.  Any and all comments are appreciated.

FSTab 
```

proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /boot           ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda3	/home		ext3	defaults,errors=remount-ro 0       1
/dev/hdc1	/home/one	reiserfs	defaults	0	0
/dev/hdd1	/home/two	ext3	defaults	0	0


```

Here is what I have done.  I added three entries:  /dev/cdrom1, /dev/hdc1 and /dev/hdd1.  The drives are accessable and read and write fine.  I ran fsck -f on the two hard drives and they reported no errors.

---

### Post by LKRaider on 2006-06-23
Hmm, strange.

I would try removing one by one and see which is causing the delay.
Another place to look is the system log: type 'dmesg' in a terminal and look for drive errors, or just post it to the [pastebin](http://paste.ubuntu-nl.org/) and link it here so we can take a look.

---

### Post by Ptero-4 on 2006-06-23
A question. Why you need separate partitions within an already separate /home partition?

---

### Post by nix4me on 2006-06-23
reiserfs is slow to mount.  It shouldn't take forever but it is noticably slower than other filesystems.  Especially if its a large drive and its full.

Ive seen other posts on the forums about pausing at mounting root filesystem, try looking at those posts too.

nix4me

---

