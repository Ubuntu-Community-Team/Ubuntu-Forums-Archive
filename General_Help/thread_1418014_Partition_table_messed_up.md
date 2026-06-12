---
title: "Partition table messed up"
date: 2010-02-28
forum: General Help
---

### Post by Bright_View on 2010-02-28
Hi all,

Could use some help.  I tried reinstalling XP because it wouldn't boot (I wasn't sure why and didn't want to try to figure it out) and it looks like I messed up my partition table doing it.  I can't boot into anything now and GParted doesn't recognize anything.  I have found threads which describe the problem, but I am hesitant to try to fix this myself.  Here are the outputs of various commands that other people have posted:

ubuntu@ubuntu:~$ sudo sfdisk -luS

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1            63  39070079   39070017  83  Linux
/dev/sda2      39070080 830126744  791056665   5  Extended
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda3   * 244188063 830126744  585938682   b  W95 FAT32
		start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda4     830126745 976751999  146625255   7  HPFS/NTFS
		start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda5      39070206 234420479  195350274  83  Linux
		start: (c,h,s) expected (1023,254,63) found (1023,2,1)
/dev/sda6     234420606 244187999    9767394  82  Linux swap / Solaris
		start: (c,h,s) expected (1023,254,63) found (1023,2,1)



ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 39070017, Id=83
/dev/sda2 : start= 39070080, size=791056665, Id= 5
/dev/sda3 : start=244188063, size=585938682, Id= b, bootable
/dev/sda4 : start=830126745, size=146625255, Id= 7
/dev/sda5 : start= 39070206, size=195350274, Id=83
/dev/sda6 : start=234420606, size=  9767394, Id=82



ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000aa355

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    39070079    19535008+  83  Linux
/dev/sda2        39070080   830126744   395528332+   5  Extended
/dev/sda3   *   244188063   830126744   292969341    b  W95 FAT32
/dev/sda4       830126745   976751999    73312627+   7  HPFS/NTFS
/dev/sda5        39070206   234420479    97675137   83  Linux
/dev/sda6       234420606   244187999     4883697   82  Linux swap / Solaris



and here is the result of 

ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda > PT.txt

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 39070017, Id=83
/dev/sda2 : start= 39070080, size=791056665, Id= 5
/dev/sda3 : start=244188063, size=585938682, Id= b, bootable
/dev/sda4 : start=830126745, size=146625255, Id= 7
/dev/sda5 : start= 39070206, size=195350274, Id=83
/dev/sda6 : start=234420606, size=  9767394, Id=82

Thanks a million to everybody who tries to bail me out of this one.

Dave.

Edit:  I should add that I wanted a 75 GB XP partition, a 300 GB fat 32 partition for sharing files, a 100 GB Home partition, 5 GB for swap, and 20 GB for the root file system.

---

### Post by garvinrick4 on 2010-02-28
IF you do a sudo update-grub do you get anything.

gparted not recognizing anything is not good though.

---

### Post by Bright_View on 2010-02-28
> **garvinrick4 said:**
> IF you do a sudo update-grub do you get anything.

gparted not recognizing anything is not good though.

I don't know.  Is this guaranteed not to mess up anything worse than it is?  Based on other posts on the forum, it seems these errors can largely be rectified provided I don't screw anything up more than I already have.  I'm waiting on somebody who really knows this stuff to tell me how to use sfdisk to fix what I've done.

Thanks for the reply.  

Dave.

Edit: Forgot to add - from the live CD I can mount all partitions except for the 100 GB partition.  Under the 'Places" menu, it is marked as 'Extended', while others are not (only say 'Filesystem').  Also, from what I understand the reason Gparted won't recognize anything is because I have a primary partition (SDA3) hidden inside an extended partition (SDA2).  I don't know how to safely change that though. . .

---

