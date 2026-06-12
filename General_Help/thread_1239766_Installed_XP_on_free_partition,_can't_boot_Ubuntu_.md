---
title: "Installed XP on free partition, can't boot Ubuntu drive?"
date: 2009-08-13
forum: General Help
---

### Post by wastingpenguins on 2009-08-13
Hi guys,

Been using Ubuntu for about a month, dual-booting with Vista . For various reasons, I cleared my Vista partition to make Ubuntu my sole operating system. Today, I realized that I needed Windows for something specific, so downloaded XP and installed it on my old XP partition.

That went fine, but now I can't figure out how to boot Ubuntu. When I start my computer, XP boots automatically. When I view disk management in windows, I can see that all my Ubuntu stuff is still there on a logical drive. Unfortunately, I have no idea how to make that drive bootable again. Many sources online say that I can choose which drive to boot from in BIOS, but my if it's there I do not see the option. After much searching and failed tinkering, I have to ask you guys for help. Thoughts?

---

### Post by Grannun on 2009-08-13
The problem is that the windows bootloader doesn't recognize linux, but the opposite is untrue.  Basically, you need to reinstall GRUB or some other bootloader.  This is slightly old, however it is still a very detailed explanation of how to do so

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by yabbadabbadont on 2009-08-13
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

