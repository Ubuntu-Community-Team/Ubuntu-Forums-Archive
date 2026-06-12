---
title: "UNE .iso install goes black"
date: 2010-05-15
forum: General Help
---

### Post by mistertee on 2010-05-15
Hi, I am running Linux Mint 8 and I would like to move over to UNE 10.04  I installed it as a test on a Thinkpad at work and the .iso I burnt worked there but when I try to install it on my home laptop it shows the ubuntu progress sequence and then (when I assume it goes to the installation process) it flashes and goes black.  So, is there a way to install UNE from the CLI from Mint?  Any other ideas?  I can copy the .iso to the hard drive if there's any way to use it from there.
thanks!

---

### Post by kio_http on 2010-05-15
> **mistertee said:**
> Hi, I am running Linux Mint 8 and I would like to move over to UNE 10.04  I installed it as a test on a Thinkpad at work and the .iso I burnt worked there but when I try to install it on my home laptop it shows the ubuntu progress sequence and then (when I assume it goes to the installation process) it flashes and goes black.  So, is there a way to install UNE from the CLI from Mint?  Any other ideas?  I can copy the .iso to the hard drive if there's any way to use it from there.
thanks!

I had a similar issue with Kubuntu one day and the solution was to use a different DVD drive!

The same DVD drive actually seemed to work for everything else, Windows Xp, vista, 7, all other stuff but that one Kubuntu cd whic was a cd in perfect condition.

Alternatively, you can create a bootable USB disk with a program called Unetbootin.

---

### Post by mistertee on 2010-05-15
ahhhh the frustration continues.  unetbootin built the bootable drive but bios didn't recognize any bootable media when I tried booting to the usb drive.  if anyone has any other guesses I would be stoked to give something else a try.

---

### Post by kio_http on 2010-05-15
> **mistertee said:**
> ahhhh the frustration continues.  unetbootin built the bootable drive but bios didn't recognize any bootable media when I tried booting to the usb drive.  if anyone has any other guesses I would be stoked to give something else a try.

No problem. This is a motherboard or USB drive issue.

If you have Vista or Windows 7, EasyBCD 2 Beta can be used to boot an iso using Windows bootloader.

---

### Post by mistertee on 2010-05-20
It turns out the problem was the intel video driver issue discussed in other threads.  I downgraded back to 9.04 and worked my back to 10.04 from there...not fun, time for a newer laptop i guess.

---

