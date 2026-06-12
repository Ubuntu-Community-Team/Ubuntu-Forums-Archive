---
title: "boot stops halfway"
date: 2009-12-11
forum: General Help
---

### Post by jdbol on 2009-12-11
Hi all,

Forgive me if I posted in the wrong category. I guessed this one would do.

I built a media center PC with ubuntu 9.10 and XBMC. I want it work on a Samsung TV (LE32S81BX)

The video card installed is an ATI Radeon HD 3600 and it&#347; connected to my TV with a DVI to HDMI cable.

When I start the PC I see the boot screen following starting GRUB (I used automatic login in the setup for my convenience, I want to start directly in XBMC). The screen stays black, where on a normal VGA monitor I get the white ubuntu logo. When I remove the cable from the PC and insert it again the boot process continues and I get the splash screen. From thereon everything functions normally.

Anyone got an idea?

Thanks on advance.

JB

---

### Post by jdbol on 2009-12-12
Nobody? :(

---

### Post by serpantman on 2009-12-12
Are you saying that unplugging the vga cable and plugging it back in unfreezes the system? That is strange, sounds like a detection problem. I guess drivers are your best bet, or its possible there is a configuration problem. Try updated drivers if nothing else, i have no experience with a problem like that. Sorry.

---

### Post by jdbol on 2009-12-12
Working with VGA gives no problems at all. When I remove the HDMI cable from either the TV or PC unfreezes the system.

I checked the drivers (my first guess too), it's the latest catalyst suggested by ubuntu hardware drivers.

Could editing my xorg.conf be of any help? Are there log files that can give me a clue?

Thanks for your reply anyway.

JB

---

### Post by jdbol on 2009-12-14
The problem seems to occur when HDMI handshake is performing.

Anyone got an idea?

---

