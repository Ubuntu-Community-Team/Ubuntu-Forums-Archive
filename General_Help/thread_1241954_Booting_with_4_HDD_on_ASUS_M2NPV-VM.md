---
title: "Booting with 4 HDD on ASUS M2NPV-VM"
date: 2009-08-16
forum: General Help
---

### Post by Envel on 2009-08-16
Hi all,
I have a problem with my server (ASUS M2NPV-VM motherboard) running ubuntu 9.04 amd64.
The problem is that I can't boot linux without unplugging all disk except one (the root). Otherwise root partition cannot be mounted (an error like "bad inode") and boot stops and I see busybox. In that case I can see only devices names (sda, sdb, sdc, sdd) but no partitions in /dev.
I try to boot from livecd and I can't mount anything on my internal SATA controller, I get "device is busy or already mounted", which is not.

The thing of interest is that when I boot my system with only one HDD connected I can hot-plug in all other devices and all works OK.

The same thing with ubuntu 8.10, debian lenny. BIOS bug or what?

---

### Post by sigixv on 2009-08-16
i'm not too familiar with it but could it be that you installed and added/changed the other drives afterwards?
If that would be the case it is configuration related: check your jumper-configuration on each HDD and how they are recognized inside BIOS. When using IDE drives, check master/slave on the cable. Also make sure that if you use jumpers on your HDD, that BIOS is not set to configure jumper-free.

I personally always set everything jumperfree and make all settings inside bios.

---

### Post by Envel on 2009-08-17
On SATA-disks there is only a jumper for switching between SATA/SATAII.

---

