---
title: "On Startup Ubuntu keeps looking for USB Thumb Drive"
date: 2010-06-19
forum: General Help
---

### Post by oaxacamatt1 on 2010-06-19
Hi All,
So I was goofing around with my USB thumb drive and yanked it out by mistake instead of unmounting it and removing it the correct way.  So now on start up Ubuntu says it is looking for a mounted drive (/dev failed...) and gives me the options to either a) skip it b) keeping looking for it...  So I know I have to change the Fstab but dont remember what to change.  Is that correct (Fstab?) and what do I need to do?
Cheers,
M

Yes I forgot that was helpful... (from /etc/fstab)

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc      nodev,noexec,nosuid  0  0  
# / was on /dev/sda1 during installation
UUID=624823f7-d166-4995-b255-f150e19ec495  /            reiserfs  notail               0  1  
# swap was on /dev/sda6 during installation
UUID=d410a09b-0b98-4225-896a-247bcd7d11d4  none         swap      sw                   0  0  
# /dev/sdc1                                  /media/sdc1  vfat      defaults             0  0  

>> sudo fdisk -l:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x54397b20

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2802    22507033+  83  Linux
/dev/sda3            2803       11223    67634283    7  HPFS/NTFS
/dev/sda4           11223       19457    66139606    5  Extended
/dev/sda5   *       11224       19396    65649622+  83  Linux
/dev/sda6           19397       19457      489951   82  Linux swap / Solaris


> sudo blkid:
/dev/sda1: UUID="624823f7-d166-4995-b255-f150e19ec495" TYPE="reiserfs" 
/dev/sda3: UUID="4436E16D6A21BE4B" TYPE="ntfs" 
/dev/sda5: UUID="d4bd87be-8041-4765-beb2-00cf36164a11" TYPE="ext4" 
/dev/sda6: UUID="d410a09b-0b98-4225-896a-247bcd7d11d4" TYPE="swap"

---

### Post by Penguin Guy on 2010-06-19
Could you please post the results of [FONT="Courier New"]sudo fdisk -l[/FONT] , [FONT="Courier New"]sudo blkid[/FONT] and the contents of [FONT="Courier New"]/etc/fstab[/FONT].

---

### Post by oaxacamatt1 on 2010-06-19
Sorry about that see first message...
Cheers,
M

---

### Post by Penguin Guy on 2010-06-19
[@oaxacamatt1]("http://ubuntuforums.org/showthread.php?p=9482902#post9482902"), it usually aids readability if you put stuff in code boxes as so:
```

# fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
**...**

```

As for your problem, it can't be FSTab's fault because your thumb drive isn't listed. Perhaps if you could post a screenshot of the error message I may be able to give you a bit more help.

---

### Post by fragos on 2010-06-19
try plugging the USB and if seen unmount correctly.

---

