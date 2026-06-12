---
title: "giant bug"
date: 2011-09-13
forum: General Help
---

### Post by sn0m on 2011-09-13
Hi
got a new laptop, an asus K53E
I've installed natty but the system is so unstable, I'm having kernel panic crushes at random regularly.
I do not know how to collect the information to report it to launchpad, all I can do is stare at it in despair and take pictures.
Is there someone that knows how to get this kind of error message and report it to launchpad.
Please have a look at attached picture and apologise for the quality but couldn't do any better I'm afraid.
thanks
Sokol

---

### Post by dino99 on 2011-09-13
boot on recovery mode (hold 'shift' key down at bios end process to get the grub menu, then select the second line) then select 'repair packages'

then look at /var/crash/ and /var/log/ about errors (/home/user/.xsession-errors too)

---

