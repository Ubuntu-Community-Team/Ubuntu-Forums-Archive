---
title: "Grub menu labels..."
date: 2009-11-29
forum: General Help
---

### Post by Kizzume on 2009-11-29
I am trying to set up a computer for someone that isn't very computer savvy, and I've set it up to dual boot so they boot to Windows for games (with all easy icon access to web browsers removed) and boot to Ubuntu for everything else.

Everything seems good--in Grub I've gotten it down to two entries (grub_disable_linux_uuid=true and sudo chmod -x /etc/grub.d/20_memtest86+), but I can't seem to find a way to edit how those entries will show up on the menu.

When I look at the documentation, the entry for "GRUB_DISTRIBUTOR" is supposed to affect the name, but right now it says "echo Debian'" but it doesn't show up in the menu as Debian, it shows as "Ubuntu, Linux 2.6.31-14-generic" and the windows entry shows up as "Microsoft Windows XP Professional (on /dev/sda1)".

I'm wanting the Ubuntu entry to simply show as "Internet and Email" and the Windows entry to show up as "Games"--I want it to be really simple for the person I'm setting this computer up for.

Is this possible to do?

---

### Post by oldfred on 2009-11-29
I just saw this, something very similiar:

[http://ubuntuforums.org/showthread.php?t=1296225](http://ubuntuforums.org/showthread.php?t=1296225)

---

