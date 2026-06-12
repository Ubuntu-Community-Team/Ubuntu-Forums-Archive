---
title: "/boot/grub has only 'grubenv' file"
date: 2010-12-06
forum: General Help
---

### Post by Eric in San Diego on 2010-12-06
Hi all -
 
I've been running Ubuntu for about a month now, loving it so far, but I have encountered a problem.
 
On my last reboot, I got an error message; something like 'unknown command (loadfont). File not found. Then it stalls out and won't boot.
 
This thread seems to address the issue:
 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10158646#post10158646](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10158646#post10158646)
 
 
which suggests that I edit the /boot/grub/grub.cfg file. But when I boot from disk, my /boot/grub/ directory has exactly one file: grubenv - whose content does not seem to be human-readable.
 
This is Ubuntu 10.10. On an HP Tx2. Dual boot from Wubi.
 
So what does this mean, and what can I do?
 
Many thanks,

---

### Post by bcbc on 2010-12-06
Boot an Ubuntu live CD and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results back here as described in the link.

---

