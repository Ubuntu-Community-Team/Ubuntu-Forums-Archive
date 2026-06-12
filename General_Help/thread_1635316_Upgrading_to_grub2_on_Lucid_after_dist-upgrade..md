---
title: "Upgrading to grub2 on Lucid after dist-upgrade."
date: 2010-12-01
forum: General Help
---

### Post by jwbrase on 2010-12-01
A few months ago I dist-upgraded my Jaunty install to Lucid. The upgrade went fine, but it did, of course, leave the original Grub Legacy install in place. I've been thinking of upgrading to Grub2, but I've been unable to find much in the way of directions for performing such an upgrade on Lucid. The directions I've found for Jaunty/Karmic recommend chainloading Grub2 from Grub Legacy at first to test it before totally replacing Grub Legacy, which seems eminently sensible to me, but I find that on Lucid the grub2 package pulls in the grub-pc package which conflicts with the legacy grub package, and I'm a bit nervous about committing to removing Grub Legacy before I know that Grub2 will work.

Can anybody give advice on how to proceed?

---

### Post by oldfred on 2010-12-01
Grub2 has gone thru a lot of changes. Not sure if you down load grub2 now for Lucid what version you get. But I had no issues with grub2 since it came out.

You do not have to chroot if you can boot into your system. This will totally uninstall both grub & grub2 then install just grub2.
chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

