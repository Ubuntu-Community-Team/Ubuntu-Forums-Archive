---
title: "Dual boot shared home folder"
date: 2010-12-15
forum: General Help
---

### Post by joshh88 on 2010-12-15
I just recently started using the home folder as a separate partition and feel safer using as such in case of an OS failure(unlikely). I also decided to install Linux Mint LMDE(Debain Edition) on the same drive just on another partition and that is where a problem has arisen. Whatever changes I make to the gnome desktop in either OS affects the other. I don't understand why this is happening; I thought that each OS would be separate with the exclusion of my personal files in Home. If that is not the case is there a way to separate them so that each do not have to be tweeked so as to be usable.

---

### Post by dcstar on 2010-12-15
> **joshh88 said:**
> I just recently started using the home folder as a separate partition and feel safer using as such in case of an OS failure(unlikely). I also decided to install Linux Mint LMDE(Debain Edition) on the same drive just on another partition and that is where a problem has arisen. Whatever changes I make to the gnome desktop in either OS affects the other. I don't understand why this is happening; I thought that each OS would be separate with the exclusion of my personal files in Home. If that is not the case is there a way to separate them so that each do not have to be tweeked so as to be usable.

Edit the /etc/fstab file on whatever distro you don't want to share /home and comment out/delete the relevant line.

The other way is to create a admin new account on one distro and use that instead of the original which is defaulting to the same one on both systems now.

---

### Post by oldfred on 2010-12-15
I did originally create a separate /home, but quickly changed to a /data for all my files. The /home is now back inside my / (root) as it only has those hidden file & folders with user settings. I do copy some settings from one system to another, but I am usually just upgrading versions of Ubuntu and have separate / for each version (3 / in rotation-  old,current & beta). Some of the data like firefox & thunderbird I have to move from the hidden folders into my data partition to keep home small.

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
kansasnoob's sharing
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
(now changed mount to /mnt/data from /usr/...)

---

