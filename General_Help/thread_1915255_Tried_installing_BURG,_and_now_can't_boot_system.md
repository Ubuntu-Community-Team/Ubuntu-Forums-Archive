---
title: "Tried installing BURG, and now can't boot system"
date: 2012-01-25
forum: General Help
---

### Post by Jamie_Edwards on 2012-01-25
Hey guys,

OK, here's the thing...

I'm running a dual boot system with

MS Windows XP,
And Ubuntu 11.04.

I recently changed my Ubuntu included bootloader ( which I am unsure whether it's GRUB or GRUB2) to BURG (Brand new Universal loadeR from Grub) only now I'm unable to boot into either of the systems. All I'm greeted by is a Grub Rescue terminal type thing.

Also if I try to boot from my usb stick (which has the live cd on it) it says /casper/initrd.lz

What have I done wrong? And how can I fix it? (if it's even possible without installing a new copy of Ubuntu)

Thanks in advance!

Jamie

---

### Post by drs305 on 2012-01-25
How are you booting now?

The /casper may be part of the USB stick's syslinux.

If you can get to a linux Desktop, I'd recommend installing/running the Boot Repair app (see sig link). You can download/run it from the Ubuntu Desktop if you can get there. 

If it can't fix your system, it has an option to run the boot info script, which is also available here:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Posting the contents of RESULTS.txt which the script generates will help us figure out what is happening.

In any case, you will need to be able to boot to linux or a boot repair utility disk such as supergrub2 to fix things.

---

### Post by Jamie_Edwards on 2012-01-26
I'm getting nothing, I guess there is one thing left to do lol, I guess I won't be doing the same thing again in a little while XD

Thank you for your help anyway!! Much appreciated!

---

