---
title: "lost dual boot after upgrading XP to Vista"
date: 2010-07-12
forum: General Help
---

### Post by om3g@ on 2010-07-12
I threw 10.04 on an old box just to poke around but lost the dual-boot functionality when I upgraded the XP HD to Vista. Here is the order of events:

1 - Started with a single HD with XP
2 - Added a second physical HD, installed 10.04 on it. I don't know jack about linux file systems, so I just chose the "newest sounding" one, ext4. In order to get dual boot to work I had to make sure that the XP HD was set as primary in BIOS. At this point, dual boot works fine, I can access both OS's with no issue.
3 - Using a legal copy of Vista, I upgraded the XP HD. Now PC just boots straight to Vista like the other OS doesn't even exist.

---

### Post by audiomick on 2010-07-12
Hi.
I guess that the windows update overwrote the MBR (master boot record). You will probably have to re-install Grub, the linux boot loader.

There are instructions for that here
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

