---
title: "Kernel updates = no auto boot from grub"
date: 2010-03-27
forum: General Help
---

### Post by coyoteboy on 2010-03-27
I'm remote from my system and so have to wait 2-3 days before I can get access directly, but I've noticed that when the kernel updates automatically (or forced by me), the next reboot stops at the grub page awaiting confirmation of the kernel I want to boot. grub.conf doesnt seem significantly different from that of fedora (my previos distro for this machine) and even has the default lines and times spec'd, so I can't see what's holding it up. Any ideas how I can prevent this so I can have my system auto-updating the kernel AND safe to reboot remotely?

---

### Post by Brandon Williams on 2010-03-29
What does your /etc/default/grub file look like? Especially the GRUB_DEFAULT and GRUB_TIMEOUT values? I would expect it to work if GRUB_DEFAULT=0 and GRUB_TIMEOUT=1 (I set GRUB_TIMEOUT to 1 just to give myself a chance to press shift for the menu).

If that's not helpful, then I suggest you [look here next](https://help.ubuntu.com/community/Grub2).

---

