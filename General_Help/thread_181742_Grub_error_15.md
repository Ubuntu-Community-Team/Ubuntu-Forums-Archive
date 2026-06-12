---
title: "Grub error 15"
date: 2006-05-24
forum: General Help
---

### Post by jaywhy13 on 2006-05-24
I get grub error 15. I was initially trying to remove grub. I tried installing, running lilo, liloconfig... removing grub, installing lilo, configuring lilo. Restarting after each try to still see grub. 

I also tried my luck with splash images, installed grub-splashimages from synaptec. Wrote my own /etc/grub.conf that didn't exist. Restarting to no avail.

However for some reason i had to shut down my computer, and when I start up i get error 15 from grub. No message, just error 15.

Currently I can still get back into Ubuntu via use of the install cd boot from hard disk option.

---

### Post by Sef on 2006-05-24
> 15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

It's looking for GRUB.  It has reputation for being hard to remove.  

Try this if you can download and burn:

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")

---

