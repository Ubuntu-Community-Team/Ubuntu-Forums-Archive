---
title: "Ubuntu Stops Booting"
date: 2011-05-20
forum: General Help
---

### Post by Mr. Monkey on 2011-05-20
I am really struggling with Linux right now.  I have setup my laptop to dual boot Win7 and Ubuntu 11.04 a few times already.  I setup partitions for /boot (2gb) and used an LVM partition for the rest.  So, today I installed Ubuntu, I played around for a little just trying to get it set up, updated drivers and softwares, etc.  Then, I had to reboot into Win7 do to some work, and then after I tried to boot back to Ubuntu.  For some reason I am stuck at the list of boot items.  I've tried switching to terminal and tried startx but I'm getting some sort of fragmentation error.  I also noticed that my boot was freezing at AppArmor, so I did a apt-get remove apparmor.  Now it's getting stuck at the CUPS (print spooler?)

I'm getting a little frustrated.  I don't know what else to try.  Can anyone shed some light?

---

### Post by linuxinstalledfromhdd on 2011-05-20
[http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/](http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/)

Sometimes that helps..  give it a try.

---

### Post by Mr. Monkey on 2011-05-20
The Grub2 works fine... I think.  It still loads, and lets me choose what to boot.  It's after that that it freezes.  This is when Ubuntu is booting.  Does recovering Grub help with that?  Or is it my Linux image?

---

### Post by linuxinstalledfromhdd on 2011-05-20
It kinda depends on how many partition you may have, or if you are dual booting with something other than linux.  I've run a grub2 repair even though grub works fine, and it sometimes fixes that kind of issue.

---

### Post by Rubi1200 on 2011-05-21
If Ubuntu is freezing after GRUB passes control to the kernel then it is not a GRUB issue anymore.

By the way, removing apparmor was, in my opinion, a rather foolhardy thing to do. It is there to protect your system and you may have just compromised the stability too.

If you are experiencing these freezes, it may be either a graphics or a memory problem.

Posting the full specifications would be a helpful start.

---

