---
title: "help installing windows on ubuntu only computer"
date: 2011-09-25
forum: General Help
---

### Post by gymillionaire on 2011-09-25
my windows failed on me and i couldent seem to get anywhere so now all i have is ubuntu how can i re install windows this is the error i get "windows cannot be installed to this hard disk space. windows must be installed to a partition formatted as NTFS" where do i go from here? thans

---

### Post by lordbux on 2011-09-25
> **gymillionaire said:**
> my windows failed on me and i couldent seem to get anywhere so now all i have is ubuntu how can i re install windows this is the error i get "windows cannot be installed to this hard disk space. windows must be installed to a partition formatted as NTFS" where do i go from here? thans

I assume that there is only a single partition in this case you have to use the format option in the windows install CD to format the ext3/ext4 partition to NTFS or FAT32 as windows wont work on them.

But this will cause ubuntu to get removed along with all data in that drive.

If you have more than one drive : ie: drive is partitioned, just format one of the drives which is not / .

In this case you will have to reinstall grub.

FORMATING from INSTALL DISK: [http://how-2-do.blogspot.com/2008/05/how-to-format-install-windows-xp.html](http://how-2-do.blogspot.com/2008/05/how-to-format-install-windows-xp.html)

RE-INSTALLING GRUB: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

:popcorn:

---

### Post by haqking on 2011-09-25
> **gymillionaire said:**
> my windows failed on me and i couldent seem to get anywhere so now all i have is ubuntu how can i re install windows this is the error i get "windows cannot be installed to this hard disk space. windows must be installed to a partition formatted as NTFS" where do i go from here? thans


use your Windows 7 disk or restore to factory settings if your laptop supports it and you havent at some point removed the recovery parition.

depending on your laptop press ctrl+f11 or press f8 to a get a menu. How you do that or if it is an option depends on your laptop and what you have done.

you can follow these steps to see how to install and delete your partitions during install etc.

[http://www.techtalkz.com/windows-7/514412-windows-7-installation-guide-tutorial.html](http://www.techtalkz.com/windows-7/514412-windows-7-installation-guide-tutorial.html)

---

