---
title: "Re-installing the GRUB loader"
date: 2010-08-26
forum: General Help
---

### Post by Edward in CT on 2010-08-26
I need to re install the grub loader on a Acer Netbook. I made a Live CD and tried to follow the directions given in the documentation but I am having no luck. Does anyone know a reasonably straight forward way to re-install GRUB back onto the native Hard Drive. I'm a little new to Ubuntu, but I can usually follow instructions pretty well.
Thanks in advance.

---

### Post by ajgreeny on 2010-08-26
If you are using ubuntu 9.10 or 10.04 follow the instructions below, though it will not be a live CD, but a live USB; the same thing to your system as far as doing this is concerned.

Ubuntu 9.10 uses Grub 2, so you need to find out what your drives are using live CD:
    ```
sudo fdisk -l
```From that you need to find the device name of your Ubuntu drive, something like &#8220;/dev/sda2&#8243;.  Ask here again if it is all gobbledegook to you.
Still in the terminal, type:
    ```
sudo mkdir /media/sda2
sudo mount /dev/sda2 /media/sda2
```To reinstall grub:
   ```
 sudo grub-install --root-directory=/media/sda2 /dev/sda
```Push enter and you&#8217;re done! Of course you need to replace &#8220;/dev/sda2&#8243; and &#8220;/dev/sda&#8221; with what you found in the fdisk output.

---

### Post by Edward in CT on 2010-08-27
Here is what happened when I tried what you suggested.  I'm a beginner.  What do I do next?
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdcaa3f7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12586896   27  Unknown
/dev/sda2   *        1568        1580      104422+   7  HPFS/NTFS
/dev/sda3            1581        6444    39069336    7  HPFS/NTFS
/dev/sda4            6444       19457   104527201+   5  Extended
/dev/sda5           19332       19457     1012063+  82  Linux swap / Solaris

---

### Post by rawlins02 on 2010-08-27
You need to simply mount your linux partition(s) and do the grub-install.  First, to be sure which partition to mount.  Post the output of each of these two commands:

> df -h

> blkid


Your install may be as simply as issuing the commands ajgreeny gave, with sda2 replaced with sda4. We'll know more once you post the output of df and blkid.

---

### Post by richlyn9 on 2010-08-27
check [http://rxezlqu.wordpress.com/2009/07/16/making-a-dedicated-grub-partition/](http://rxezlqu.wordpress.com/2009/07/16/making-a-dedicated-grub-partition/)

---

### Post by oldfred on 2010-08-27
The fdisk is not showing a linux partition but this:

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12586896   27  Unknown

This says there is  a partition issue of some sort with sda1 which I assume is the Linux install.

I would try this first.

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sda1
if errors:
sudo e2fsck -f -y -v /dev/sda1

---

### Post by Edward in CT on 2010-08-27
I tried what you said and here is what I got...ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by oldfred on 2010-08-27
You can try this:
[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Part of testdisk which is in the repositories or most recovery CDs. 
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)
[http://ubuntuforums.org/showthread.php?t=1443110](http://ubuntuforums.org/showthread.php?t=1443110)

---

