---
title: "Disabling splash screen in grub (watching boot process)"
date: 2012-05-05
forum: General Help
---

### Post by RoadEnds on 2012-05-05
I am troubleshooting some startup issues - however the purple splash screen from grub is masking my boot process.  I have been trying to disable the splash screen and display the full boot process (similar to how Debian works).

I have edited the GRUB_CMDLINE_LINUX_DEFAULT variable in /etc/default/grub file and removed the quiet and slash entries.  This achieved 1/2 of my goal.  I can now see a partial boot process on the screen (similar to what is logged in /var/log/boot.log).

I am still unable to display the first half of the boot process on my screen (i.e. similar to what is captured in dmesg).  After selecting my desired boot entry in grub, I am left at a blank purple screen for a number of seconds.  This is the screen I wish to disable.

Thanks in advance for help.

---

