---
title: "error: no such device"
date: 2010-01-24
forum: General Help
---

### Post by sks24 on 2010-01-24
This morning I restored the XP partition on an Acer 4220 using both the restore discs and the restore partition.  In both cases the GRUB menu loads, but, upon selecting the XP partition, I get the following error: "error: no such device: c818475e18474b20".

The 9.10 partition boots just fine.  

What's the easiest way to get XP to boot again?  I don't mind completely removing Ubuntu, reinstalling XP, and then reinstalling 9.10 again.  What, in other words, would be the easiest way to restore the laptop to its condition before I installed Ubuntu?

(Is there a more straightforward way than that shown [here]("http://ubuntuforums.org/showthread.php?t=113630")?)    

I had both operating systems booting just fine, but some problems with the .NET Framework in XP compelled me to the conclusion that I would do best to simply start from scratch with it again.  

And that's where my problems began.

Thanks in advance,
Scott

---

### Post by mcduck on 2010-01-24
Restoring the XP partition probably formatted the partition, which means that it's UUID has changed. Grub is still looking for a partition with the old UUID.

Simple thing to solve, really, just boot to Ubuntu, run "blkid" to get UUIDs for your partitions and then edit Grub's configuration file (/boot/grub/menu.lst in 9.04) to use the corrct UUID. No need to reinstall anything.

If you have configured the Windows partition to mount automatically in Ubuntu you will probaby have to also edit /etc/fstab to use the new UUID as well.

In case you are running 9.10 instead of 9.04 as your profle suggests, then simply running "sudo update-grub" shuld be enough, no need to edit any configuration files. :)

---

### Post by sks24 on 2010-01-24
I salute you, mcduck!  And thank you for your prompt advice, which worked perfectly.
  
Best,
Scott

---

