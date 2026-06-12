---
title: "repairing grub from within windoes"
date: 2009-12-07
forum: General Help
---

### Post by nbv4 on 2009-12-07
I am a long time ubuntu user. I thought I'd try out windows 7 just to see what it's all about. It turns out my wireless card is not supported in Windows, so back to Ubuntu I go. The only problem is that the windows installer overwrote grub, and so my linux partitions are not accessible. I tried to boot from an old Ubuntu Live CD, but for some retarted reason, my computer won't boot any any CD. The CD ROM works fine and dandy when Windows is running, but at boot time it's like the CD ROM is not even there. And yes, I've tried jiggling every single BIOS option relating to the CD ROM.

I also tried to create a USB drive with the latest Karmic Live CD, but it won't load either. The disk is made correctly because I tried it on my sister's computer and it boots there fine. I also tried making a USB disk for Arch and Damn Small Linux, but I get the same thing. This is stupid because just yesterday I was able to install Windows 7 from a USB disk, and a few weeks before that, I was able to install Karmin from a USB drive as well. Now all the sudden it doesn't work.

Is there any kind of utility that I can run from within windows that accesses grub and allows me to repair the boot record so that Linux gets loaded instead of windows?

---

### Post by Mark Phelps on 2009-12-07
> **nbv4 said:**
> Is there any kind of utility that I can run from within windows that accesses grub ...
Basically -- no.

>  and allows me to repair the boot record so that Linux gets loaded instead of windows?

However ... you can download and install EasyBCD from NeoSmart Technologies forum and use it to add an entry to the Win7 boot loader for Ubuntu.  It will install GRUB4DOS and allow you to use that to boot into Ubuntu.

---

