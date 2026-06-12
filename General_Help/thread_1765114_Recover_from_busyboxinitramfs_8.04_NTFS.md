---
title: "Recover from busybox/initramfs 8.04 NTFS"
date: 2011-05-22
forum: General Help
---

### Post by goggins on 2011-05-22
I either installed Hardy heron or its predecessor by accident, but began running it exclusively. I did it way back when while trying to create a test drive disk, and I did not repartition the drive, because all my windoze NT stuff survived. I'm now 8.04. Yesterday I had a bunch of updates to do, did them, closed a ton of windows and then pulled up 3 open office files and each, when it came up said there wasn't enough space to save all needed information as they opened. I then closed them and one hung and froze the whole machine, leading me to do a reset. This is BEFORE rebooting from the updates.

Now when I boot into Ubuntu (I'm dual boot) I start to get the opening Ubuntu GUI screen but then get :
BusyBox V1.1.3 (Debian 1.1.1.3-5ubuntu12)built in shell (ash) line followed by:
 initramfs)

I'm essentially a total noob, I've rarely used command line and not for a long time. 

I made a version 11.04 live disk, and it says that the file system is clean, but will not show me any of my old files, only the NT files and directories. I have a ton of unbacked up important data in Hardy Heron so I don't want to do an install from the 11.04 CD. 

I've read several threads so far, and can't seem to find anything addressing this that I understand. The drive is a 160GB drive on an HP Pavilion dual core that has a 154GB NTFS boot partition, which is where I'm sure the Hardy Heron files are, and a 6GB FAT32 HP_RECOVERY partition that windoze lists ad drive D (the NTFS is C) The live disk says the FAT32 partition is /dev/sda1 and the NTFS is /dev/sda2 

Where should I start? I've seen stuff about booting into recovery mode, but that isn't an option when I boot from the hard drive, and the only older ubuntu disk I have is for 7.something and generates "defective CD" type error messages.

---

### Post by linuxinstalledfromhdd on 2011-05-22
Bump!!

---

### Post by goggins on 2011-05-22
I don't understand BUMP.

---

### Post by goggins on 2011-05-23
Additional Information: 
Using 11.04 live disk sudo fdisk -l says:

disk /dev/sda  160.0GB
40 heads 63 sectors/track 20673 cylinders
units = cylinders of 1520 x 512 = 7741440 bytes
sector size (logical/physical) 512 bytes/512 bytes
I/O size (minimum/optimal) 512 bytes/512 bytes
Disk identifies 0xd0c4b2ef

Device    Boot  Start    End   Blocks     Id     System
/dev/sda1           1    771   5828728+    b     W95 FAT32
/dev/sda2  *      772    20672 150451560   7     HPFS/NTFS


sudo fsck -n /dev/sda2 says

fsck from util-linux -ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: No such file or directory while trying to open /dev/sda2
Possibly non-existent device?

Trying on /dev/sda1 gives the same error message.

I used the GUI disk utility under Admin to mount /dev/sda2 which mounted at /media/HP_PAVILION

fsck -n /dev/sda2 gave same error as above, ditto /dev/sda1, but
fsck /media/HP_PAVILION said:

Attempt to read block from filesystem resulted in short read while trying to open /media/HP_PAVILION
Could this be a zero length partition?

Got the same type of error after unmounting /dev/sda2 and mounting /dev/sda1 (as /media/HP_RECOVERY)

---

### Post by jmszr on 2011-05-23
goggins,

As near as I can tell you are dual-booting using Wubi. If that is the case then the hard reset corrupted the Windows file system. I used to run 8.04 Wubi and this happened more than once. To fix: boot into Windows, go to the command prompt, run chkdsk/r . Shut Windows down properly and then you should be able to boot into Ubuntu.

Hope this works for you.

Edit: Post #6 in this thread: [http://ubuntuforums.org/showthread.php?t=1530560](http://ubuntuforums.org/showthread.php?t=1530560) has additional info (if, in fact, you're using Wubi).

---

### Post by goggins on 2011-05-23
jmszr - I'll try that right now. I was doing some clean up in win in case i found a was to mirror it and noticed that it does show ubuntu in the installed programs list, at 15,103 MB.

---

### Post by goggins on 2011-05-23
NOt good, seems worse. windoze chkdsk/r fixed some stuff, but I still get same error when trying to dual boot ubuntu. Worse, live disk now won't load, I got a multi-line panic which locked machine on the first try (10 lines) and one maybe twice that long n the next try. Since these require a hard reset, I'm afraid of trashing this os too, though I will probbly ty at lest once more. Maybe I'll try to get/make a 10.04 disk to use, though.

---

### Post by goggins on 2011-05-24
I made a 10.04 live disk and got it to boot. I had no luck with fsck, but was able to run sudo ls /media/HP_PAVILION/ after mounting /dev/sda2. I got a directory listing, of course, but it included some stuff that I hadn't seen before.

Is ubuntu 8.04 buried in here in a recognizeable place and, more importantly, are my ubuntu based data files in here where I can find them? Clueless as I am, I tried 'grep -HR '.odt' /media/HP_PAVILION? and got a blisteringly long list tht included a whole host of binaries, and not at all what I wanted. Any cludes what to look for and what commands to use to find it.

Any help would be greatly appreciated. Thanks.

---

