---
title: "Increasing Partition Size"
date: 2009-10-18
forum: General Help
---

### Post by Quarkrad on 2009-10-18
If one has Ubuntu on an ext4 partition (say sda1) - is it possible to increase the size of that partition (as you could do with windows using something like partition manager, or partition magic) without effecting/damaging your Ubuntu system on sda1?  Obviously assuming you have spare space on your HD to add to sda1.  With windows partition managers you can do all sorts of things to partitions (add, merge, delete, resize) and 99% of the time without effecting your windows OS - can the same be done in the Linux world when after a few months HD space becomes a bit tight?

---

### Post by MartinEve on 2009-10-18
According to this thread - [http://www.linuxquestions.org/questions/fedora-35/growing-ext4-733678/](http://www.linuxquestions.org/questions/fedora-35/growing-ext4-733678/) - yes, you can.

Have a look at [http://en.wikipedia.org/wiki/Resize2fs](http://en.wikipedia.org/wiki/Resize2fs) which should do what you require.

---

### Post by Paqman on 2009-10-18
Yes, simply boot up into the LiveCD and go to System >Admin > Partition Editor. Make sure everything is umounted (including swap, right click and "swapoff" if required) and you should be able to modify any partition.

---

### Post by Quarkrad on 2009-10-18
pacman -thanks, but will the 'original' OS be intact?  I might experiment with this when I do a fresh install of 9.10 in a few weeks time.  If I mess up my installation of 9.04 it will not matter.  I guess(?) you have to do this via a live CD rather than using Partition Editor within Ubuntu on sda1.  (With Windows Partition Magic you can set things up as you want within the windows environment and if necessary it (P Magic) will reboot the machine, do the changes and then boot into the OS with the changes made).  Very good at partition editing with excellent graphics.

---

### Post by Paqman on 2009-10-18
> **Quarkrad said:**
> pacman -thanks, but will the 'original' OS be intact?


Yes. The LiveCD can do lots of things besides installing the system.

The reason to use the LiveCD is that the partition editor (called Gparted) will refuse to make any changes to a partition which is in use. Which is quite sensible, really. Your Windows tool would have done it at boot time for the exact same reason.

However, no matter what tool you use, it's always advisable to update your backups before modifying any partitions. Just in case.

---

