---
title: "Keyboard/mouse not working after upgrade"
date: 2011-08-10
forum: General Help
---

### Post by rts on 2011-08-10
(Starting a new thread so I can put [SOLVED] in front of it)

If you're having problems with your keyboard/mouse not working as in:

[http://ubuntuforums.org/showthread.php?t=1812741](http://ubuntuforums.org/showthread.php?t=1812741)

Here's what I had to do:

Boot the 11.04 Live CD.

Switch to a terminal with Ctrl-Alt-F1.

Follow these instructions to mount your HD and get all the necessary /dev entries in a chroot environment:

[http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/](http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/)

Next, edit /etc/default/grub and comment out the line GRUB_HIDDEN_TIMEOUT=0

Run update-grub

Reboot. Now the SHIFT key *will* bring up the grub menu; hold SHIFT after your BIOS POST.

Select an older kernel. For me, 2.6.38-8 worked.

Your keyboard should now work. Go and do an update with the update manager to get the latest kernel.

Edit /etc/default/grub and put the line GRUB_HIDDEN_TIMEOUT=0 back in. Run update-grub. Reboot.

Worked for me. Your mileage may vary.

---

