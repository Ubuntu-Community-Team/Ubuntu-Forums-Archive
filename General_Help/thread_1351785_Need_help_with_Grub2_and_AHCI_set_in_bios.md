---
title: "Need help with Grub2 and AHCI set in bios"
date: 2009-12-10
forum: General Help
---

### Post by krash1220 on 2009-12-10
I have a brand new computer AMD Phenom II X4 810 Processor with 8 GB ram. It came with one SATA hard drive and a SATA DVD drive. It was set to Raid in the bios and of course had Windows 7 preinstalled. I added a second SATA hard drive and a second SATA DVD drive. Set the bios to AHCI because I don't even know how to use raid and installed Windows 7 to the first hard drive, sda1, and in own way without all the crap that comes with a preinstalled OS. I then installed Ubuntu 9.10 to the second hard drive, sdb1. I let grub2 install to the mbr. When I reboot I get Grub Read Error and it just hangs there. I've tried installing Grub2 to the second hard drive mbr, I tried installing it to a partition, etc. etc.  the only way I could boot with Grub2 was to install it to a USB Flash drive. Next I reinstalled Ubuntu 9.10 without installing Grub2 and then installed Grub and that works fine as well. But I wanted to use the new Grub2. So I set my bios to IDE mode, reinstalled Windows 7 to first hard drive, Ubuntu to second hard drive, installed Grub2 to mbr and it works just fine. Now I don't know anything about how to set up Raid and I don't really want to but my question is, what is the point of having all SATA drives if you have to run them in IDE mode? I thought the whole point of SATA was the fact that they read and write faster. So will my drives be slower set to IDE mode or is the Raid and AHCI mode just for setting up Raid drives? Or am I installing Ubuntu the wrong way. Do I need to install it with an alternative way? I could really use some help.

Thanks,
Krash

---

