---
title: "System locks solid during disc writes"
date: 2010-06-09
forum: General Help
---

### Post by philpem on 2010-06-09
System spec:
  Core 2 Quad, Q6600, 2.4GHz OC'd to 3GHz
  Asus Rampage Formula m/b
  2x WD RE2 500GB HDDs ("linux boot" and "winxp boot")
  1x Seagate Barracuda HDD ("boneyard")
  4GB DDR2-800 RAM

  Ubuntu 10.04 LTS

I'm having a really annoying problem with disc activity on my desktop system. Basically, if anything is writing a large amount of data to the hard drive (say, 10MB or over), the machine basically freezes solid. The mouse goes jittery (you move it and it takes a second then moves in one big leap).

For instance, if I try to image a USB hard drive to a file:
# dd if=/dev/sdh of=usbdrive_dump bs=1G

Effectively this works in two portions: it reads 1GB of data to RAM, then blats it out into a file. The machine is perfectly responsive while the USB drive is getting thrashed, but locks solid when the internal SATA drives are in use.

Writing to USB HDDs doesn't seem to have the same effect -- I can copy 1GB files to/from them all day long and the machine is perfectly happy.

Can any HDD gurus tell me what's going on here, or maybe suggest some things I could check?

Thanks

---

### Post by dcstar on 2010-06-10
> **philpem said:**
> System spec:
  Core 2 Quad, Q6600, 2.4GHz OC'd to 3GHz
  Asus Rampage Formula m/b
  2x WD RE2 500GB HDDs ("linux boot" and "winxp boot")
  1x Seagate Barracuda HDD ("boneyard")
  4GB DDR2-800 RAM

  Ubuntu 10.04 LTS

I'm having a really annoying problem with disc activity on my desktop system. Basically, if anything is writing a large amount of data to the hard drive (say, 10MB or over), the machine basically freezes solid. The mouse goes jittery (you move it and it takes a second then moves in one big leap).

For instance, if I try to image a USB hard drive to a file:
# dd if=/dev/sdh of=usbdrive_dump bs=1G

Effectively this works in two portions: it reads 1GB of data to RAM, then blats it out into a file. The machine is perfectly responsive while the USB drive is getting thrashed, but locks solid when the internal SATA drives are in use.

Writing to USB HDDs doesn't seem to have the same effect -- I can copy 1GB files to/from them all day long and the machine is perfectly happy.

Can any HDD gurus tell me what's going on here, or maybe suggest some things I could check?

Thanks

Have a play with the SATA emulation/AHCI settings in your BIOS and see if it makes a difference.

---

### Post by philpem on 2010-06-10
> **dcstar said:**
> Have a play with the SATA emulation/AHCI settings in your BIOS and see if it makes a difference.

I've got it set to AHCI already:

Configure SATA as [AHCI]    (can also set this to RAID or IDE)
HDD Write Protect [DISABLE]
SATA Detect Timeout (secs) [35]
AHCI Port 1 [HDD]
AHCI Port 2 [HDD]
AHCI Port 3 [HDD]

---

