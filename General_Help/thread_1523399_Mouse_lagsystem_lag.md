---
title: "Mouse lag/system lag"
date: 2010-07-03
forum: General Help
---

### Post by LoonQ on 2010-07-03
Hi

I am a quite new Linux user (been using Ubuntu 9.04 for a while now) that need some help. A few days ago I decieded to try Linux Mint 9 (Gnome Edition) instead of Ubuntu 9.04. I installed it and everything works fine except from that the system or mouse/keyboard lags. The lag occurs when the hd is working (my guess). This problem did not exist in Ubuntu 9.04 and I am using the exact same hardware.

Does anyone know how to solve this?

Hardware: MSI K8NGM2-IL, AMD 3500+ (singel core), 2Gb ram, 250Gb SATA Hd, DVD-Rw (IDE), Microsoft Habu mouse (USB)

---

### Post by efflandt on 2010-07-03
This is just a wild guess.  But I have an older Athlon64 3200+ with legacy ATI X1300 video, and initially had video lag and could not go into suspend or hibernate with 10.04 (video would not shut off).  Apparently my video did not like the new default kernel mode setting (kms) video driver.  The **nomodeset** kernel boot parameter disabled kms to use the normal video modules, which made video as fast as 9.10, and then suspend/hibernate worked.  For more details see [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

That was different than an old Compaq V2000 laptop with Sempron 3300+ and integrated ATI (Mobility 200) video which experienced keyboard lag (which often dropped characters) and jumpy mouse lag in 9.10, especially during boot and disk access just after booting.  It also could not wake from suspend or hibernate in 9.10.  On that old laptop, 10.04 actually works better with rarely any keyboard or mouse lag, and suspend and hibernate work.  I am using **nomodeset** boot parameter for it, but that makes less of a difference in video speed than my desktop.

Some people apparently have been having some issues with some USB keyboards and mice in 10.04, but the Microsoft wireless mouse I tried on a different laptop this week had no issues.  I did have to edit a file for my Logitech diNovo Edge Bluetooth keyboard/mousepad to work in 10.04.

---

### Post by LoonQ on 2010-07-03
Thx for the tip! I tried the nomodeset option but it did not help :( I will keep digging into this!

---

