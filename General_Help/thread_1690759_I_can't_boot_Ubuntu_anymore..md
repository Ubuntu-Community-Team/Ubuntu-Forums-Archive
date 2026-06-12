---
title: "I can't boot Ubuntu anymore."
date: 2011-02-18
forum: General Help
---

### Post by iguanaboy on 2011-02-18
Sorry this is a repost.

I've been using Lynx for quite some time without trouble. However, I turned off my laptop for the first time in weeks a few days ago, and now it won't boot anymore. I don't know if that's related, but a week or so ago Ubuntu suggested that I delete a program that wasn't working well (can't remember what it was, though) and I did - expecting that the next update would give me a new and improved version of that faulty program.

Anyway, here's what I get when I try to launch Ubuntu:

[long list of numbers and unrecognized commands]
[Killed]
[mount: mounting /devbon /root/dev failed: no such file or directory]
[mount: mounting /devbon /root/sys failed: no such file or directory]
[mount: mounting /devbon /root/proc failed: no such file or directory]
[Target filesystem doesn't have /sbin/init.]
[No init found. Try passing init= bootarg]

[BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)]
[Enter 'Help' for a list of built-in commands.]

[(initramfs) [(some numbers)] ieee1394: Host added: ID:BUS[0-00:1023] GUID[(some letters and numbers)]



Is there a way to re-open Ubuntu in "safe mode" or something, and extract my files (and hopefully Firefox bookmarks) before re-installing Ubuntu? Even better, is there a way to simply fix the problem?

Any help much appreciated.

---

### Post by Quackers on 2011-02-18
If Ubuntu is the only installed operating system, hold down the shift key whilst booting. That should give you the grub menu. The second option will be a recovery option, try that. I'm not sure it will help with the mounting problem though. You may need further assistance.
You could also try booting from the live cd/usb and selecting "try ubuntu" and when the desktop loads try the Places menu to see if the Ubuntu partitions mount.

---

