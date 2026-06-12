---
title: "sata drive mapping issues"
date: 2006-06-21
forum: General Help
---

### Post by nick58b on 2006-06-21
I'm trying to install a system which will include a RAID 5 array out of 3 Samsung SATA drives. Ubuntu will be on a separate Seagate SATA drive. I connected the Seagate to SATA port 1 on my motherboard, and the 3 Samsungs to ports 2, 3, and 4. In the BIOS, these ports have the same numbers, where the Seagate is still on SATA port 1. My issue is that when I'm installing Ubuntu, the Seagate shows up as "SCSI3 sdc", and not "SCSI1 sda", like I was expecting.

Is this normal behavior? I was hoping for straight SATA port 1==sda, SATA port 2==sdb, etc. mapping so that when a drive dies, I can easily identify and replace it. This will become more important as I add more drives to this machine.

Here's some more info from my machine:

* ASUS a8n-sli deluxe
* all drives plugged into NVIDIA SATA ports, SIL SATA controller disabled.
* Installing using Ubuntu 6.06 AMD64 Server CD off of hda port (LAMP install)
* When unplugging the 3 samsungs, and leaving the Seagate on port1, it shows up as "SCSI3 sda" in the installer. Optimally it would show as SCSI1.

---

