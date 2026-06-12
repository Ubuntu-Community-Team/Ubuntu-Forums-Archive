---
title: "Any File Copy operation is dead slow...."
date: 2010-01-02
forum: General Help
---

### Post by unique2224 on 2010-01-02
Havent experienced this b4...
After installing Ubuntu 9.10, copying files of size around 700mb is taking a lot of time.
Copying takes more time for both SATA HDD to USB and between SATA mounted NTFS partitions... Starting Speed is at 10 Mbps.. System hangs for a while periodically wit copying speed at 3 Mbps.. I have a Swap partition of 1 GB
My System Specifications...
Intel Pentium 2.80GHZ Dual Core Processor
Intel D945GNT Motherboard
512MB DDR2-533 RAM
80GB SATA HDD

File copying worked fine in Windows XP SP3...
Copying files between partitions was really fast in XP and to USB , speed was gud at 10-12 Mbps when i was using XP.
Bt file copying in Ubuntu 9.10 is a headache and the window freezes and become dull indicating tat system s hanged bt CPU and swap usage is shown as normal when system hangs..!!!
Please Help me..

---

### Post by umutert on 2010-04-15
I am having the same headache problem. ubuntu copies with only 7MB/psec on Ubuntu and about 40MB/psec on XP.
:(:confused:

---

### Post by perham on 2010-04-15
> **umutert said:**
> I am having the same headache problem. ubuntu copies with only 7MB/psec on Ubuntu and about 40MB/psec on XP.
:(:confused:

maybe it's not recognizing your sata controller and is working in pio mode? what kind of motherboard do you have?

---

### Post by umutert on 2010-04-15
> **perham said:**
> maybe it's not recognizing your sata controller and is working in pio mode? what kind of motherboard do you have?

I have amd 2500 32bit on asus kt6 something board. how can i find out if it is running on pio mode?

---

### Post by perham on 2010-04-15
> **umutert said:**
> I have amd 2500 32bit on asus kt6 something board. how can i find out if it is running on pio mode?

post the outputs of these commands:

```

lspci
dmesg | grep dma
dmesg | grep pio

```

---

