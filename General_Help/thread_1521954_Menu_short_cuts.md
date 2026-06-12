---
title: "Menu short cuts"
date: 2010-07-01
forum: General Help
---

### Post by rules on 2010-07-01
Hi all

I would like to find out if you can change the short cut locations in the "Places" menu. I primarily use a dedicated Fat32 partition to store all my data (music, files, pics etc.) and would like to modify the default short cuts to point to the folders on my data partition.

Can it be done?

Cheers.

---

### Post by oldfred on 2010-07-01
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)


I do not recommend FAT anymore. NTFS is better if you want to share with windows. NTFS has journaling and can store files over 4GB. 

I use linking for all my data folders in /home but from a ext3 /data partition.
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

