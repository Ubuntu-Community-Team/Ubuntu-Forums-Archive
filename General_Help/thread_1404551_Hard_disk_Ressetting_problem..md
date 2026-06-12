---
title: "Hard disk Ressetting problem."
date: 2010-02-11
forum: General Help
---

### Post by cheyo on 2010-02-11
I have 2 Sata HD on my box, one is a hitachi and the other is a maxtor one. Recently i started to hear strange noises from the maxtor one. After a dmesg i have found that the HD is resseting itself over and over during the boot process:

```
exception Emask 0x10 SAct 0x0 SErr 0x50000 action 0x2 frozen 
```

I recently changed the battery on my motherboard, so i started by checking the BIOS settings and **changed the ACPI statte from ST3 to ST1** and voilá, clicking noise gone. As i browsed a lot of pages without an answer to my problem i started this thread expecting that it will solve other fellow users problems too.

My specs (on MSI k8n Neo2 platinum Motherboard):

Computer
  Processor  AMD Athlon(tm) 64 Processor 3500+
  Memory  2061MB (553MB used)
  Operating System  Ubuntu 9.10


Operating System
  Version
  Kernel  Linux 2.6.31-19-generic (i686)
  Distribution  Ubuntu 9.10
  SCSI Disks
  ATA Maxtor 6L100M0
  LITE-ON DVDRW LH-20A1S
  ATA HDT722525DLA380
  Maxtor OneTouch
   USB CompactFlash
   USB SmartMedia
   USB MMC/SD
   USB MS/MS Pro

Sorry for my bad english ;)

---

