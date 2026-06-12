---
title: "What's going on with Ubuntu 9.04?"
date: 2009-08-25
forum: General Help
---

### Post by daemon3 on 2009-08-25
Laptop: Toshiba Satellite S500
Operating System: Ubuntu 9.04

The initial release of Ubuntu 9.04 for me was adequate.  I got a few kernel panics when I switched users.  However, with each upgrade thereafter, my computer has gotten noticeably worse.  Anybody else having problems? For example:
[LIST]
[*]I don't have multimedia key functionality anymore.  It used to work perfectly, work less effectively, and now not at all.
[*]I get kernel panics when I suspend to RAM and then wake up a few times.  The first time I suspend to disk I always get a kernel panic.
[*]When I try to connect to the wireless, sometimes the wireless connection is disabled everywhere on the system, including on my windows partition.
[/LIST]

For the kernel panics, is there a way to get the last output from tty7 (the screen that always crashes) so I can be helpful for developers?  Thanks.

---

### Post by daemon3 on 2009-08-25
> **daemon3 said:**
> Laptop: Toshiba Satellite S500
Sorry, I lied. :P I have a Toshiba Satellite L305D-S5934

---

### Post by flurios on 2010-05-05
> **daemon3 said:**
> Laptop: Toshiba Satellite S500


Hello there,

I got my hands on a Toshiba Satellite pro s500 today. Tried 10.4... installed quickly as hell, but screen stayed black before/at grub, just a blinking cursor.

Tried 9.10. Installed slowly as hell... same thing. Exept that I noticed that the system actually started. It was just the screen that stayed black...

any clues or hints??

---

### Post by Vaphell on 2010-05-05
try setting acpi=off in grub config present on hdd using livecd and see if you can get further.

what's your gfx

---

