---
title: "Boot Device Problems!"
date: 2010-05-24
forum: General Help
---

### Post by Theory5 on 2010-05-24
I have been having an all around bad time trying to install Ubuntu server edition. One problem and then another. I finally fixed the blank screen problem after booting a live cd which gave me the same problem. I found that enabling that nomodeset command at startup will work. I just have to figure out how to enable it on the HDD server edition. 
But my other problem is with Grub2.  I tried to reinstall it, but it keeps failing when I try to install it to my HDD. 
I tried uninstalling GRUB2 and installing LILO but It tells me I have a problem with fstab. it says that my device doesnt look like a regular block device and It needs to be fixed. 

Any help? Here is the forum thread from my post on Linux Questions, it also has the output of the commands: 
lspci
fdisk -l
dmesg
dd if=/dev/sda bs=512 count=1 of=/tmp/sda_mbr.dat && file /tmp/sda_mbr.dat

 
[After installation of Ubuntu 10.4 server edition screen shuts off]("http://www.linuxquestions.org/questions/showthread.php?p=3978944#post3978944")


I also need help rewriting my fstab file. I tried to fix it but I couldn't figure out what mount points goes to the partitions and file system. I need help.

---

