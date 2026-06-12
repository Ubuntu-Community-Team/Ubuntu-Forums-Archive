---
title: "can't locate filesystem after trying to reinstall ubuntu"
date: 2010-01-11
forum: General Help
---

### Post by john_doe_1231 on 2010-01-11
can't locate filesystem after trying to reinstall ubuntu

Hello,
My skills are not reaching far enough to solve this problem i guess.

I was trying to backup everything, format/overwrite an partition to start with a fresh start after some annoying issues with my previous installation.

I had a perfectly fine working partition table and i chose to format partition 
#1 (Ext4) partition (~50gb)
from the installation tool from the ubuntu live cd.
I had more partitions
#2 was ~5gbits swap
#3 was some unencrypted data(~20gb) (i think it was Ext3)
#4 was encrypted data (~150gb) (Ext4)
#5 unpartitioned data (~100gb)

So while doing this the installation failed somehow during the format of the disks, i tried testdisk but it couldn't locate the HDD nor any other program.

when i look at my /dev it says this (from live cd):
root@ubuntu:/home/ubuntu# fdisk -l
root@ubuntu:/home/ubuntu#

mount says:
root@ubuntu:/home/ubuntu# mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

/dev/sdxx doesn't even exist and this also doesn't seem to work:
root@ubuntu:/dev# ls -al | grep h
drwxr-xr-x   2 root   root        3240 2010-01-12 00:16 char
crw-rw----   1 root   root     10, 228 2010-01-12 00:14 hpet
crw-rw----   1 root   root     10,  56 2010-01-12 00:14 network_throughput
drwxrwxrwt   2 root   root         140 2010-01-12 00:32 shm
crw-rw----   1 root   root     10, 231 2010-01-12 00:14 snapshot

I nearly have the idea there is no hdd in my pc while i am very sure it was here some hours ago. I didn't made it fall on something hard while running or something so all inside of the box should be just fine.

I can't reach my keepassx file (stored inside the encrypted part) so i also can't log onto my workspace or anything, it is quite crippling currently, if somebody could help me out then i will send him/her a cookie if he/she wants :D. Tell me if you need more information for the fix, ill keep you posted in any possible way.

---

### Post by JC Cheloven on 2010-01-11
try with sudo:

```
sudo fdisk -l
```

---

### Post by john_doe_1231 on 2010-01-11
> **JC Cheloven said:**
> try with sudo:

```
sudo fdisk -l
```


root@ubuntu:/home/ubuntu# sudo fdisk -l

Disk /dev/sda: 2086 MB, 2086141952 bytes
65 heads, 62 sectors/track, 1011 cylinders
Units = cylinders of 4030 * 512 = 2063360 bytes
Disk identifier: 0x73696420

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?      476415      611511   272218546+  20  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(356, 97, 46) logical=(476414, 40, 59)
Partition 1 has different physical/logical endings:
     phys=(357, 116, 40) logical=(611510, 44, 23)
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?      330071      463812   269488144   6b  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 57) logical=(330070, 33, 57)
Partition 2 has different physical/logical endings:
     phys=(269, 101, 57) logical=(463811, 34, 52)
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?      133745      480733   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(133744, 17, 18)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(480732, 37, 49)
Partition 3 does not end on cylinder boundary.
/dev/sda4   *      346062      346067       10668+  49  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(87, 1, 0) logical=(346061, 29, 36)
Partition 4 has different physical/logical endings:
     phys=(335, 78, 2) logical=(346066, 48, 44)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by john_doe_1231 on 2010-01-11
thanks, it is now confirmed that there is existing something from my previous partition table :)

anyone has an idea on how to get it good again?

*edit it was cause i plugged an USB device inside my pc, without it plugged in it still returns nothing*

---

### Post by john_doe_1231 on 2010-01-11
Would it make sense to burn a GParted live CD or could an Ubuntu live CD do that same job; ive had good experiences with that Live CD

---

### Post by JC Cheloven on 2010-01-11
Well, at least some progress :-)
It can be seen that there is a real problem in your disk. The partitions having  different physical/logical beginnings and ends sounds bad. Something is messed up when you tried to setup partitions for your new install.

I can guess (from the fact that only 4 partitions are reported while you said that there was five), that you tried to create more than 4 primary partitions, which isn't possible. But somehow you got a partial "success". The way to go is creating an extended partition to include as many logical partitions as needed. 

Anyway I don't know really how to get back your disk at the previous state, or if it's possible at all. I can only give a couple of emergency ideas:

- Try to access your data from live cd, and recover as many of your personal files as you can.

- See what gparted says (also from live cd) about your disk. And yes, the functionality of gparted itself is the same from ubuntu live cd.

EDIT: let's see if the output of  "sudo sfdisk -V /dev/sda" gives us a hint...
 ... and also check out testdisk:  [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) although not sure whether it supports ext4 or not.

---

### Post by john_doe_1231 on 2010-01-12
The problem is that there is no /dev/sda or /dev/hda.


This is the output for sfdisk:
root@ubuntu:/home/ubuntu/Downloads/testdisk-6.11.3/linux# sudo sfdisk -V /dev/sda
/dev/sda: No such file or directory

sfdisk: cannot open /dev/sda for reading

Here is the output for testdisk:


TestDisk 6.11.3, Data Recovery Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

  TestDisk is free software, and
comes with ABSOLUTELY NO WARRANTY.

Select a media (use Arrow keys, then press Enter):
Disk /dev/sda - 2086 MB / 1989 MiB - usb Flash Disk
Disk /dev/sr0 - 723 MB / 689 MiB (RO) - MATSHITA DVD-RAM UJ880AS



[Proceed ]  [  Quit  ]
                                  Quit program
Note: Disk capacity must be correctly detected for a successful recovery.
If a disk listed above has incorrect size, check HD jumper settings, BIOS
detection, and install the latest OS patches and disk drivers.

Here is the logfile of testdisk


Tue Jan 12 06:41:42 2010
Command line: TestDisk

TestDisk 6.11.3, Data Recovery Utility, May 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
OS: Linux, kernel 2.6.31-14-generic (#48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009)
Compiler: GCC 4.3 - May  6 2009 14:40:08
ext2fs lib: 1.41.4, ntfs lib: 10:0:0, reiserfs lib: 0.3.1-rc8, ewf lib: 20080501
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
/dev/sr0 is not an ATA disk
Hard disk list
Disk /dev/sda - 2086 MB / 1989 MiB - CHS 1011 65 62, sector size=512 - usb Flash Disk
Disk /dev/sr0 - 723 MB / 689 MiB - CHS 353266 1 1 (RO), sector size=2048 - MATSHITA DVD-RAM UJ880AS

---

### Post by john_doe_1231 on 2010-01-12
Are there any other ideas on how i can retrieve my HDD partitions? (I know you want that cookie :o)

---

