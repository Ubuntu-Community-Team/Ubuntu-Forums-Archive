---
title: "RocketRaid JBOD 1740?  Sees two devices. ."
date: 2009-08-28
forum: General Help
---

### Post by patrad on 2009-08-28
I'm trying to setup two 1 TB drives in a JBOD configuration for backup.  The issue is that gparted is showing me the two indiviuals drives (sdb, sdc) connected to the SATA card.  I want it to see it as one logical, JBOD 2TB disk and mount it as such.

I'm installed Ubuntu 9.04, it's a P4 2.8.  The OS is installed and running fine on a separate 80 GB IDE drive.

I have a High Point RocketRaid 1740 installed and the two SATA drives connected to it ports 1 and 2.

In the RocketRaid BIOS I have them configured in a 2TB JBOD.

I installed the Ubuntu drivers from HighPoint for the card.

lspci shows it installed and recognized.  
02:02.0 SCSI storage controller: HighPoint Technologies, Inc. RocketRAID 1740 (rev 02)

dmraid -r shows me:
no raid disks

I was under the impression that I configure the raid device in the HighPoint BIOS.  Not sure how Ubuntu can see the two seperate drives. . .

---

### Post by beadrifle on 2010-04-17
Bump.

I need help on the same issue too; more fundamental actually.

I'd appreciate it if someone explained the process of setting up JBOD on Ubuntu Server, there does not seem to be a thread explaining this lucidly enough.

---

### Post by patrad on 2010-04-17
I'm not sure if you are using the same controller, but I found in my situation, with the 1740, that it's actually not a true RAID controller!  It would need software RAID to support JBOD which in Unbuntu is not possible.  I think the use of JBOD with Unbuntu is controller specific and you need to ensure that your specific controller supports JBOD on the hardware

---

