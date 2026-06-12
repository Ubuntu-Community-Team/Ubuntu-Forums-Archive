---
title: "/home SD card not mounting at startup"
date: 2009-08-30
forum: General Help
---

### Post by Barijazz on 2009-08-30
I have an EeePC 900A and have my SD card (sdb1) mounted to /home.  During boot on AC power, e2fsck exits status 8 failing to read the superblock.  During boot on battery power Ubuntu starts until the Gnome loads and I get a error that the /home directory can't be found.  In both cases I can flip to a terminal and sudo mount -a to successfully mount /dev/sdb1 to /home.  Boot continues normally and all is well.  If booting on AC power and Ubuntu runs full disk check is automatically during boot, sdb1 seems to mount properly, the check passes, and everything loads as it should.

I've read forum posts ad nauseam to no avail.  I was previously running Easy Peasy 1 & 2 (Intrepid & Jaunty) with no problems.  This problem starting after immediately after installing Jaunty UNR.  I believe it may be a problem with the SD card slot not initiallizing soon enough or fast enough to allow the SD card to be read during boot.

I apologize for my first post being a novel, but I've yet to find this issue addressed elsewhere.  I've included my fstab just for kicks.  BTW, in trying to fix this issue I removed UUIDs from fstab.

Thanks for looking!

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# Internal SSD /dev/sda1
/dev/sda1    /               ext2    noatime,errors=remount-ro 0       1
# SDHC card /dev/sdb1
/dev/sdb1    /home           ext3    noatime,nodev,nosuid    0       2
#File systems placed in RAM
tmpfs        /tmp        tmpfs    defaults,noatime,mode=1777    0 0
tmpfs        /var/tmp    tmpfs    defaults,noatime,mode=1777    0 0
tmpfs        /var/log    tmpfs    defaults,noatime,mode=0755    0 0


---

### Post by ppirilla on 2009-08-30
I did a google search of "e2fsck status 8" and came across [http://ubuntuforums.org/archive/index.php/t-481742.html](http://ubuntuforums.org/archive/index.php/t-481742.html)

in sum, try changing your /etc/fstab line to 
```
# SDHC card /dev/sdb1
/dev/sdb1    /home           ext3    noatime,nodev,nosuid    0 0
```

---

### Post by tgeer43 on 2009-08-30
I have read that on the EeePC the SD card is usually sdc1.
Also, are you sure that the SD card is formatted as ext3 and not vfat?

If you are unsure of either question, open a terminal and look at the output of these two commands:
```
sudo fdisk -l
sudo blkid
```tgeer

---

### Post by Barijazz on 2009-08-31
Thank you for the quick responses.

ppirilla - I believe I ran across that solution before, but its doesn't fix my problem.  By skipping disk checking it gives me the same behavior on AC power that it does on battery power: a GUI error dialogue that it can't find my /home directory and would I like to login with home as /? After mounting via terminal, I click "No", I get the login prompt, and all is well.

tgeer43 - Some EeePCs have a spot for a second internal SSD.  The model I bought is very basic so has only internal SSD, but it is not soldered in as many primary SSDs are on EeePCs.  And I'm positive the SD card is formatted ext3 because I formatted it myself.  sudo mount -a sucessfully mounts my SD card to /home, but here is the output to both commands you mentioned.

> [sudo] password for christian: 

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x892d892d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         490     3935893+  83  Linux

Disk /dev/sdb: 16.2 GB, 16288579584 bytes
255 heads, 63 sectors/track, 1980 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006b14b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1980    15904318+  83  Linux

christian@eeechristian:~$ sudo blkid
/dev/sda1: TYPE="ext2" UUID="61c48118-7398-4cfe-8cc6-86a49a5e86fd" 
/dev/sdb1: TYPE="ext3" SEC_TYPE="ext2" UUID="05564e8a-5c19-4d9a-b56c-63a3a72b9481"

---

