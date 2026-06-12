---
title: "Something very bad has happened to me! GRUB error 5..."
date: 2009-08-10
forum: General Help
---

### Post by quadranoid on 2009-08-10
Hi,

I was running Vista and 8.04LTS via GRUB, and then installed 9.04 via the boot CD, under a separate partition. I wanted to get rid of 8.04 and tried to fiddle with the partitions in Vista, and then when I rebooted I got an error #5 at the GRUB boot stage.

This is what happens when I do sudo fdisk -l


ubuntu@ubuntu:~$ sudo fdisk -l
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x9090 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7677c6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10485760   27  Unknown
/dev/sda2   *        1306       20116   151089152    7  HPFS/NTFS
/dev/sda3           20116       29522    75553788    7  HPFS/NTFS
/dev/sda4           38504       38913     3293325    f  W95 Ext'd (LBA)
/dev/sda5   ?      189477      340451  1212696648   90  Unknown
ubuntu@ubuntu:~$ 

I would like to be able to run Vista and 9.04 via GRUB, can anyone help me please? I'm pretty new to Ubuntu.

---

### Post by dnrmusic on 2009-08-10
i am also very new to ubuntu so don't take everything i say as gospel, however i had a similar problem today.
 
i have vista and ubuntu 9.04 on dual boot, i tried to be smart and ended up installing a second ubuntu on my drive.  i went into the format settings in ubuntu and formatted the new install thinking this would delete it, however when i tried to log in i got grub error 2 and neither system would load up.  i booted from the disk  and installed another ubuntu only using the minimum space required and this installs new grub settings and overrode my problem.  i obviously have a version of ubuntu that i don't need but at least i can get into the computer and use either windows or ubuntu.  i will now try and find out how to correctly delete this other version in the future.
 
hope this helps
 
cheers
 
D

---

### Post by merlinus on 2009-08-10
According the the results of fdisk, it looks like your ubuntu installation is hosed.  You can use testdisk to try and reconstruct the partitions.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

It is never a good idea to use windows-based tools to work on linux partitions.

---

### Post by dnrmusic on 2009-08-10
just read a computer magazine with a troubleshooting section for ubuntu and it tells you to fix boot problems download supergrub from [www.supergrubdisk.org]("http://www.supergrubdisk.org") and choose the cd image and burn it to cd, restart pc with cd in drive and choose fix boot of gnu/linux, when you reeboot without cd the grub boot menu should be restored.

---

### Post by quadranoid on 2009-08-11
Thanks for the advice - only thing is that I can't burn a supergrub disk because I'm running off a live disk to access the internet!
At this point, all I want to do is get back to using my computer with Vista and forget Ubuntu entirely, but I'm not sure how to go about that either... Any tips?

---

### Post by Cato2 on 2009-08-11
Try using the Ubuntu USB Creator with a USB flash drive and put SuperGrubDisk on that (or SGD may have its own USB flash support anyway).  A bit more hassle but should work.

See my posting at [http://ubuntuforums.org/showthread.php?p=7769865](http://ubuntuforums.org/showthread.php?p=7769865) for some other ideas.

---

### Post by dnrmusic on 2009-08-12
use this link it tells you how to delete ubuntu altogether  [http://members.iinet.net.au/%7Eherman546/p18.html](http://members.iinet.net.au/%7Eherman546/p18.html)

---

### Post by madhavhmk on 2009-08-12
I think you need to reinstall grub and all would be fine....

just boot from live cd, 
>sudo grub
grub> find /boot/grub/stage1

it will return someting like (hdo,1)

now type :
setup (hdo)


and reboot (boot from HDD now)

atleast you must be able to see the list of operating systems now....

from your fdisk output it appears you have windows on sda2

so select windows from the operating systems list, type e to go to edit,
and enter (hd0,1)

atleast windows should work now..!!!!



A slightly different thing happened to me ystdy, and it worked for me...

check this link too :
[http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

---

### Post by madhavhmk on 2009-08-12
I also found this link....hope its useful

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

