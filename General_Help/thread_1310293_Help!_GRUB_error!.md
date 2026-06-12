---
title: "Help! GRUB error!"
date: 2009-11-01
forum: General Help
---

### Post by MonoBrow_063 on 2009-11-01
Ok, ran Xubuntu for some time on an old computer of mine to act as a server...

As such it sits next to my router with an ethernet link and power. It had previously been setup with XDMCP, telnet and samba for access.

Clean install of Karmic though and it all goes wrong. All installed, XDMCP and telnet sorted so take it away to it's "home" and run it up. Cannot connect to the box.

Bugger.

So I unplug, move to the monitor and watch what happens. It hangs loading grub then complains about UUID's and shows the menu. Boot the live CD and confirm the UUID is the same as in /boot/grub/grub.cfg

Reboot and it appears to now work.

Switch off, remove to the router again and try again. Symptoms are exactly as before! Cannot access and the computer appears to hang!

Please don't tell me I need to have a keyboard attached!!!

Anyone else come across this problem? I tried searching but got nothing I could pick out as related.

Cheers.

---

