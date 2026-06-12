---
title: "iPhone issue but not the normal problem?"
date: 2010-01-25
forum: General Help
---

### Post by pengy_666 on 2010-01-25
Hello all. Im a novice old school linux user.

Decided to migrate my laptop entirely to ubuntu 9.10 karmic, Everything has gone well.

Managed to sort my home network out and also setup a remote desktop connection to home server running windows 7 ultimate 64 bit.

I am having a complete nightmare with my iphone, I can plug it in and I get a camera icon on my desktop and the picture directory is mounted.

I cannot connect it to GTKPod.

I have tried searching for the usb rules in /etc/fstab/ but I am confused as to wether its reading it or my usb?

dmesg produces this?

```
[  960.692439] usb 2-1: USB disconnect, address 2
[ 3402.628071] usb 2-1: new high speed USB device using ehci_hcd and address 3
[ 3402.767335] usb 2-1: configuration #1 chosen from 4 choices

``````
[    2.047052] usb 1-2: configuration #1 chosen from 1 choice
[    2.160063] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    2.284048] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.297940] usb 2-1: configuration #1 chosen from 4 choices
[    2.305589] hub 3-0:1.0: over-current change on port 1
[    2.668977] ata1.00: ATA-8: TOSHIBA MK1246GSX, LB213M, max UDMA/100
[    2.668981] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.669892] ata1.00: configured for UDMA/100
[    2.684225] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1246GS LB21 PQ: 0 ANSI: 5
[    2.684363] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.684407] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    2.684458] sd 0:0:0:0: [sda] Write Protect is off
[    2.684461] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.684488] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.684635]  sda: sda1 sda2 < sda5 >
[    2.755166] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.004071] ata2: SATA link down (SStatus 0 SControl 300)

```sudo grep ' sd' /var/log/dmesg produces this, 

```
[    2.684363] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.684407] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    2.684458] sd 0:0:0:0: [sda] Write Protect is off
[    2.684461] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.684488] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.684635]  sda: sda1 sda2 < sda5 >
[    2.755166] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.609147] kjournald2 starting: pid 402, dev sda1:8, commit interval 5 seconds
[    6.848776] EXT4-fs (sda1): internal journal on sda1:8 

```I dont know a lot but following a lot of info from this forum, I have been trying to mount the sda for my ipod but as you can see it just isnt there??


Where am I going wrong?

What other info can I provide to help?

Thanks in advance for your help.

---

### Post by pengy_666 on 2010-01-26
I was hoping someone might shed some info?

---

### Post by philcms1 on 2010-01-26
Hi,

I just went through the process of making Ubuntu work with my iPhone. This tutorial worked for me (with Karmic):

[http://www.ubuntugeek.com/ipod-touch-3g-sync-over-usb-without-jailbraking-in-ubuntu-karmic.html](http://www.ubuntugeek.com/ipod-touch-3g-sync-over-usb-without-jailbraking-in-ubuntu-karmic.html)

Hope this helps.

Phil

---

