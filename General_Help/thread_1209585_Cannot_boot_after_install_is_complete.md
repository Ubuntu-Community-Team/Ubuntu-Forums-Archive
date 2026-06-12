---
title: "Cannot boot after install is complete"
date: 2009-07-10
forum: General Help
---

### Post by JeMe on 2009-07-10
Hi,

I'm new to ubuntu and i'm having issues with the installation of ubuntu 9.04 desktop edition.

The system:
HP Proliant ML 330 G3 + Xeon + 1.5GB memory
HP Smart Array 641 SCSI controller with 2x 36GB in mirror.
Adaptec 1420SA sata controller with 1x Samsung 1TB

I run the live CD and clean up all existing partitions on both drives using GParted.
Then I run the install shortcut on the desktop and follow the wizard which runs perfectly. If i come to the partitioning, i choose "use the entire disk" and pick the mirrored disk which is showing up as SCSI.CCISS (-,0,0) (cciss/c0d0) - 36.4 GB Compaq Smart Array.

Then i fill in the next screen with username etc.

After that i'm getting to the overview screen, but the strange thing there is when i click the advanced button, it shows me in the "device for boot loader installation" (hd0). If i look at the list, it shows me following options:

/dev/cciss/c0d0  Compaq...
/dev/cciss/c0d0p1
/dev/sda  ATA SAMSUNG
/dev/sda-1

when i leave this to default, the system doesn't boot (no boot device found)
when i change this to c0d0 Compaq, i cannot click the OK button
when i change this to the /dev/sda, i cannot boot either.

I'm probably doing something wrong here, but i don't know what.

does someone have any idea?

Thanks!

---

### Post by t4thfavor on 2009-07-10
I have this problem alot with older hw raid cards, and newer "fakeraid" devics. Best solution  I have found is to disable RAID in the bios, and use sw raid. Basically useless, I am looking for a general solution to the lack of RAID support for certain hardware. 

Sorry to bring the bad news.

---

