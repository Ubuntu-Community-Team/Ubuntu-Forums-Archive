---
title: "USBuntu"
date: 2009-07-14
forum: General Help
---

### Post by Poalman on 2009-07-14
Hi,

I’m was wondering if anyone has seen this type of problem before,

A while ago on Intrepid I took an unused 4GB usb stick and decided to try the option in System Admin I think it is to create a Bootable USB drive from my laptop, I partitioned the entire 4GB, and I tried it on my desktop but after checking, I found the bios on my desktop didn’t support booting from USB so I forgot all about it.

I just recently remembered about the USB drive and gave it to my dad to try on his PC as he fancied trying ubuntu, he stuck it in and I think initially booted into XP by mistake, I guess he got the boot order wrong in the bios. But as windows was loading up he got a BSOD and the machine reset, so he took out the USB and now XP crashes upon start up and resets every time, even in safe mode.

I realise this is more of a windows issues rather than ubuntu but I hoped there was a chance that someone has seen the same problem, and may have some suggestions for fixing XP or recovering data from the hard drives.

I’m now currently being held responsible for destroying my dads computer lol.

Cheers guys,

Paul.

---

### Post by Poalman on 2009-07-22
Fianlly got to the bottom of this..

The errors were different and less frequent if I tried with only 1 RAM stick or if I put the RAM into different ports. So I thought it might be a hardware issue.

But the problem seems to be with BIOS, I'm not sure what happened but returning the BIOS to its default settings seems to have solved the problem.

I think orignally the boot order was set to USB FDD instead of USB HDD when trying to boot the USB stick, so I don't know if that is an issue with ubuntu- I don't want to try and see if I can recreate the problem.

I'm replying incase anyone happens to search here or i guess someone may have subscribed. hmm.

Cheers,

Paul.

---

### Post by j7%&lt;RmUg on 2009-07-22
Have a dig around on google and in the tutorials board here, i beleive that thier are some good guides that explain how to make USB boot drives the best way, or the way with the least problems.

---

