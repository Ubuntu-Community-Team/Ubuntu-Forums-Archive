---
title: "Grub not working.  It says 'device not found!'"
date: 2012-10-06
forum: General Help
---

### Post by Mack1234567890 on 2012-10-06
I had a hard drive sitting in my basement, 500GB SATA2.  Tried to use it and after the mobo screen it goes to a black screen prints some stuff out then says, device not found!  and then please insert bootable disk or something like that.

Using an ubuntu live cd I can see that theres a 144GB block at the start named unusable, then a linux partition, swap partition, xp partition, and win 7 partition.  So I know theres os's on the drive but they cant boot for some reason.

I tried installing grub with boot-repair.  I just did the recommended repair and it said it worked, then restarted and same thing happened, device not found!

Then I tried installing windows 7 and it couldn't locate a hard drive at all.

Then I tried installing Ubuntu 11.04 and it seemed like it worked.  I just selected erase all and install hoping it would fix itself.  But when i restarted I still got the same thing 'device not found!'

Is this hard drive just bricked or can I make it work again?  I am able to read its files and make backups of them but it just wont boot.

---

### Post by oldfred on 2012-10-06
Welcome to the forums.

How did you install? We have seen some issues where users install to large hard drives with just a single large / (root) partition. Better to use a 25GB / (root) and make the rest /home.

Windows will not see a drive that is Linux formated. It needs to see either a formatted NTFS partition with the boot flag or unallocated space with available primary partition(s). 

From Disk Utility does hard drive show as ok under Smart Data? Smart data can run a lot of tests, but all I really know is green is good.

---

### Post by Mack1234567890 on 2012-10-07
Never mind figured it out.  Thanks for your help anyways though i appreciate it.

Sata cable was plugged into sata raid port instead of just regular sata port.

---

