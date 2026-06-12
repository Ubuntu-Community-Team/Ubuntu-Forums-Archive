---
title: "Access Linux Partition from Windows"
date: 2012-05-12
forum: General Help
---

### Post by antisomnic on 2012-05-12
I am dual booting Windows 7 and Ubuntu 12.04. I installed Ext2fsd to access the ubuntu volume from Windows. I am storing my music in the Linux partition and I would like iTunes to have access to it and the ability to add files I download. I can't do that because I do not have root access. Is there a way to get it or another program that allows you to put in your username and password or something to gain root access?

---

### Post by oldfred on 2012-05-12
No. I do not recommend writing from one system into another systems root or system partition. Best even in Ubuntu to set Windows as read only. You see all the hidden files that Windows tries to hide from Ubuntu and it then is easy to accidentally move or edit something you maybe should not. (from experince :) )

Best is to create a shared NTFS partition and put anything you may want in both systems in the shared partition. While I do not boot XP anymore my Firefox & Thunderbird profiles are still in the shared partition as I wanted the same email & bookmarks in both systems.

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

