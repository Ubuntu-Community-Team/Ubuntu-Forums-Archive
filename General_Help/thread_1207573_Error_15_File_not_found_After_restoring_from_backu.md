---
title: "Error 15 File not found After restoring from backup"
date: 2009-07-08
forum: General Help
---

### Post by deepakbm on 2009-07-08
I ve encountered some problem after backing up and restoring
Here is what i did
i followed the steps in This link 
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)


I used these codes

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/media /

And used 
this to restore
tar xvpfj backup.tar.bz2 -C /

only exception was that i excluded the media drive .
I reinstalled ubuntu 8.10 and restored it usung the tar file in /
After i rebooted and selected ubuntu from grub it shows an error

Error 15 File not found
any way i can access windows
I tried installing grub,but didnt work
Please help

---

### Post by Jebtrix on 2009-07-08
Take a look at [http://ubuntuforums.org/showthread.php?t=644773](http://ubuntuforums.org/showthread.php?t=644773)

Next time I highly recommend you try using Remastersys to 'backup' (a completely working system of course)
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

---

