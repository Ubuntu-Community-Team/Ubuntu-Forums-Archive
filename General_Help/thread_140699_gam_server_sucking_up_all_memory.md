---
title: "gam_server sucking up all memory"
date: 2006-03-06
forum: General Help
---

### Post by Prospero2006 on 2006-03-06
Anyone here know anything about the gam_server process. On more than one occasion it's completely taken up all of my system memory and swap. 
(By killing it, I effectively free up 2 gigs of system memory in an instant.)

Pros

---

### Post by hod139 on 2006-03-06
This is an [old bug]("http://ubuntuforums.org/showthread.php?t=82232") and I don't know why it hasn't been fixed.  To fix it [this site]("http://mjb.gmxhome.de/faq.html")
states "There's a nasty memleak in Ubuntu 5.10 that turns gam_server into a ram eater without limits. to prevent this from happening you have to add noinotify as an option to the bootloader, see grub for this."

and how to append kernel options to grub:

" Open /boot/grub/menu.lst in your favorite text editor as super-user (e.g. run a terminal and execute sudo gedit /boot/grub/menu.lst) and find the entry you need to edit (in most cases it should be the default one, which is by default the first). Then search for the kernel ... line and write what you want to append after it, like in kernel	/vmlinuz-2.6.12-9-686 root=/dev/hda3 ro quiet splash **noinotify**. Be sure to have it all in one line, else it won't work."

---

