---
title: "merging partitions?"
date: 2006-05-07
forum: General Help
---

### Post by Googler on 2006-05-07
i have an 80GB HDD divided into 8 partitions, my ubuntu is installed in the last partition, i need to merge some vfat partitions together.
the quistion is: is that merging will affect the booting of ubuntu and if so what should i do ?

another quistion please :?: , why ubuntu is too slow in web browsing ?, i tried other distros and they were extremely faster

regards,

---

### Post by eddie303 on 2006-05-07
It may affect booting, yes, if somehow partitions get renumbered. You will need to edit /etc/fstab and /boot/grub/menu.lst to reflect the changes.

---

### Post by Griff on 2006-05-08
[QUOTE=Googler]...why ubuntu is too slow in web browsing ?, i tried other distros and they were extremely faster

regards,[/QUOTE]
What browser/version?  The firefox in the repos is 1.0.8 I believe.  If that's what you have then you need to upgrade to 1.5.  Do a search for Automatix.  It'll install it for you.

---

### Post by aysiu on 2006-05-08
[QUOTE=Googler]why ubuntu is too slow in web browsing ?, i tried other distros and they were extremely faster[/QUOTE] It's not. I'm speaking here from having tried about 15 different distros. Firefox has been about the same speed for me on Ubuntu Breezy, Ubuntu Dapper, OS X Panther, OS X Tiger, Windows XP Professional, Windows XP Home, Mepis, PCLinuxOS, Mandriva, etc.

---

### Post by Googler on 2006-05-08
thanks to you all for responding

i'm running firefox v 1.0.8 it was realy too slow comparing with browsing with the same version in Fedora core 5 and win xp
but the problem was solved since i read an amazing thread in the HOWTO's tips and tricks forum about disabling IPv6 services i did the steps and reboot my machine , everything was fine and internet browsing  became 10 times faster !!!

---

### Post by unnes on 2006-05-08
My unsolicited observation:

Firefox 1.5 on my Ubuntu machine (P4 2.4/512MB RAM) is MUCH faster than Firefox 1.5 on my Windows XP Pro machine (P4 3.46/1GB RAM).

---

