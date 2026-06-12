---
title: "Grub error 25"
date: 2009-11-28
forum: General Help
---

### Post by chinni.joy on 2009-11-28
Hi all, 

       I have recently bought new PC,I have mention details below.I have installed ubuntu 9.04 64 bit version in my machine  I worked fine. suddenly my machine stopped working. than i restarted it.I got [COLOR="Black"][SIZE="2"]Grub error 25 [/SIZE][/COLOR]. I searched in forums for help. I tried few instructions, but didnt work. I came to know that it is better to re-install OS, I installed again. 

    After Installation.I removed CD-Rom (sata cable),connected HD,bcz I need data from that hardDisk.I mounted it & copied required data from that disk.I removed HD & added CD-ROM dvd writer.restared machine. I got again  [COLOR="Black"][SIZE="2"]Grub error 25 [/SIZE][/COLOR].

    Even I cant able to mount that disk using Live CD. it is giving Error while starting 

   ```
 05:46:23  [ 1445.288619] ata12.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
 05:46:23  [ 1445.288626] ata12.00: irq_stat 0x00060002, device error via D2H FIS
 05:46:23  [ 1445.288632] ata12.00: cmd 35/00:f8:47:dc:35/00:03:02:00:00/e0 tag 0 dma 520192 out
 05:46:23  [ 1445.288634] res 51/84:f8:47:dc:35/00:03:02:00:00/e0 Emask 0x10 (ATA bus error)
 05:46:23  [ 1445.288637] ata12.00: status: { DRDY ERR }
 05:46:23  [ 1445.288639] ata12.00: error: { ICRC ABRT }
 05:46:23  [ 1445.288649] ata12: hard resetting link
 05:46:25  [ 1447.419983] ata12: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
 05:46:25  [ 1447.429612] ata12.00: configured for UDMA/100
 05:46:25  [ 1447.429628] ata12: EH complete
 05:46:25  [ 1447.813910] sd 11:0:0:0: [sdl] Write Protect is off
 05:46:25  [ 1447.813912] sd 11:0:0:0: [sdl] Mode Sense: 00 3a 00 00
 05:46:25  [ 1447.813928] sd 11:0:0:0: [sdl] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 06:00:32  [ 2293.491350] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
 06:00:32  [ 2293.491360] ata1.00: cmd 35/00:02:43:90:7d/00:00:12:00:00/e0 tag 0 dma 1024 out
 06:00:32  [ 2293.491362] res 40/00:ff:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
 06:00:32  [ 2293.491365] ata1.00: status: { DRDY }
 06:00:32  [ 2293.794295] ata1: soft resetting link
 06:00:32  [ 2293.947277] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
 06:00:32  [ 2294.614206] ata1.00: configured for UDMA/133
 06:00:32  [ 2294.614227] ata1: EH complete
 06:00:32  [ 2294.335647] sd 0:0:0:0: [sda] Write Protect is off
 06:00:32  [ 2294.335650] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
 06:00:32  [ 2294.348472] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

 I gaveUP to ubuntu. it is just started after few minutes.but I cant able format that disk also. please help out. what to do. if got same problem what to do. plz tell how can ??.

Machine Details:
 Processor   :amd 64;
 MotherBoard :gigabyte
 Ram         :ddr2
 HardDisk    :169 gb

---

### Post by user1397 on 2009-11-28
I would try using a super grub disk [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) to try to  reinstall grub (super grub disk 2 is for grub 2, and the regular super grub disk is for grub 1, aka pre-karmic.

just download, burn image to disc, insert, reboot (make sure you have bios set to boot from cd drive first)

---

### Post by chinni.joy on 2009-11-28
Hi ,

   Thanks for reply, I will try& let you know . do we have any other way i will keep that knowledge also, if you mention.

---

### Post by adrian15 on 2010-03-02
> **chinni.joy said:**
> Hi ,

   Thanks for reply, I will try& let you know . do we have any other way i will keep that knowledge also, if you mention.

You might need to check your ATA cables because of the ATA errors in your logs.

However it might not be that, usually a GRUB ERROR 25 involves a second hard disk being detected while it is not there or a second one detected as a first one or viceversa.

You might try the Advanced tab at nearly last installation step that lets you choose the hard disks order to switch them.

adrian15

---

