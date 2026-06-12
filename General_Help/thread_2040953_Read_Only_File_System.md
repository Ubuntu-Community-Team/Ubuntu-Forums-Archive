---
title: "Read Only File System"
date: 2012-08-11
forum: General Help
---

### Post by icecube45 on 2012-08-11
Recently, I was booting ubuntu off of my usb, which was acting as a hard drive..
I was in the middle of a skype conversation when ubuntu crashed on me...
I tried to reboot, but got the message
Error: hd0 out of disk press any key to continue...

However pressing any key doesnt continue anything...
When i plug the usb into windows, or try to access it using a live cd, i get "can not mount, filesystem is read only" and on windows, i get that write protection is on...

Is there anyway I can fix this, or format my USB? I can't format because of read only...

Used live cd to post this, help please

---

### Post by icecube45 on 2012-08-11
please help...  Sorry, I really want this fixed!

---

### Post by ajgreeny on 2012-08-11
Using your live CD, but with the USB attached, run the command ```
sudo fdisk -l
``` to find out the device name of the USB drive and its partitions, eg /dev/sdb1, then run ```
sudo e2fsck /dev/sdb1
```making sure you get the correct device shown in the previous command for the root partition of your ubuntu.

---

### Post by icecube45 on 2012-08-11
here are my results:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 7398 MB, 7398752256 bytes
255 heads, 63 sectors/track, 899 cylinders, total 14450688 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 22 sectors/track, 4137 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7827455     3909696    b  W95 FAT32

Disk /dev/sdc: 8004 MB, 8004304896 bytes
247 heads, 62 sectors/track, 1020 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000276cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    13672447     6835200   83  Linux
/dev/sdc2        13674494    15632383      978945    5  Extended
/dev/sdc5        13674496    15632383      978944   82  Linux swap / Solaris


ubuntu@ubuntu:~$ sudo e2fsck /dev/sdc1
e2fsck 1.42 (29-Nov-2011)
e2fsck: Read-only file system while trying to open /dev/sdc1
Disk write-protected; use the -n option to do a read-only
check of the device.
ubuntu@ubuntu:~$ sudo e2fsck -n /dev/sdc1
e2fsck 1.42 (29-Nov-2011)
Warning: skipping journal recovery because doing a read-only filesystem check.
/dev/sdc1: clean, 221418/427392 files, 1503038/1708800 blocks

---

### Post by ajgreeny on 2012-08-11
I am not sure if it will help, but I forgot to tell you to make sure that the USB drive is unmounted when you try to run e2fsck.

There is also some info that may help at [https://help.ubuntu.com/community/Mount/USB/#Device_become_suddenly_read_only](https://help.ubuntu.com/community/Mount/USB/#Device_become_suddenly_read_only).

However, I suspect you may need to format the drive, which should be possible with gparted on the live CD.  If there are any files on the USB drive that you need you should be able to copy them to another USB using the live CD.  You may even need to create a new partition table with gparted, using the **Device** menu.

---

### Post by icecube45 on 2012-08-11
I've already tried to format the drive, both in gparted and in disk utility, I even tried in windows, all gave the same error, write protection is on (read only filesystem in ubuntu..)

---

### Post by azmyth on 2012-08-11
I would zero fill the usb device

[http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux](http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux)

Be very careful! Make sure you put the correct device or you can lose all the data on your HD.

You'll the have to create a new partition on the USB with something like gparted.

---

### Post by wildmanne39 on 2012-08-11
Hi, from what I know of that error it occurs when the drive is failing.
Thanks

---

