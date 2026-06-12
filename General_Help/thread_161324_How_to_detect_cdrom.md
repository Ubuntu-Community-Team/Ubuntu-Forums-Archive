---
title: "How to detect cdrom?"
date: 2006-04-16
forum: General Help
---

### Post by jsmidt on 2006-04-16
I bought a new cdrom a SATA cdrom.  Soundjucer says it can't detect it and I can't mount anything from it.  It gives this error: mount: special device /dev/scd0 does not exist.  

1.) How do I configure the computer to detect a cdrom.  Somebody told me it should automatically detect it but for some reason it isn't.

2.)  Are there any commands I could run or tests I could do to provide more info?  

Here is lspci:

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:05:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)0000:07:06.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:07:06.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
0000:07:06.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:07:06.3 0805: Texas Instruments: Unknown device 803c
0000:07:08.0 Ethernet controller: Intel Corporation: Unknown device 1092 (rev 02)

---

### Post by pitkali on 2006-04-16
Is your cdrom present in the output of dmesg command? I assume you have a default kernel? If not, does it have SCSI cdrom support enabled?

---

### Post by jsmidt on 2006-04-16
I don't see anything about a cdrom when I ran dmesg.  I found these lines that contain sata.  I don't know if that is it.  What is this about configuring SCSI?  I am new to this

ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0x18B0 irq 14
ata1: dev 0 cfg 49:2f00 82:746b 83:7d09 84:6023 85:7469 86:3d09 87:6023 88:203f
ata1: dev 0 ATA-6, max UDMA/100, 195371568 sectors: LBA48
ata1: dev 0 configured for UDMA/100
scsi0 : ata_piix
  Vendor: ATA       Model: TOSHIBA MK1032GS  Rev: AS02
  Type:   Direct-Access                      ANSI SCSI revision: 05
ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x18B8 irq 15
ata2: dev 0 cfg 49:0f00 82:0000 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407
ata2: dev 0 ATAPI, max UDMA/33

---

### Post by pitkali on 2006-04-16
What's that Toshiba thing? Hard drive or cdrom? And btw, I just learnt about lshw command - can you find cdrom there?

---

### Post by jsmidt on 2006-04-16
The toshiba thing is a hard drive I think.  The computer is a toshiba compuer.  The lshw command says is not found

---

### Post by pitkali on 2006-04-16
Well, if it is not in dmesg, the kernel can't see it... which is strange, because it does recognise the SATA controller, so it shouldn't have trouble with the device connected.. Nevertheless, I've run out of ideas :(

---

### Post by jsmidt on 2006-04-16
Thanks allot pitkali.  I appreciate your help.  I am new enough that dmesg might be detecting it I just don't know what to look for.  If it was detecting is there something I could do?  The cdrom appears in the computer folder, it just wont mount anything and soundjuicer doesn't detct it. :(

---

### Post by krismatth3 on 2006-04-16
edit: nvm, reread post. 

Can you post a link to the cdrom drive you got? (e.g. compusa/etc description of it)

---

### Post by jsmidt on 2006-04-16
This is the exact computer I bought: 

[http://www.mobilewhack.com/reviews/toshiba_satellite_a105-s4004_notebook.html](http://www.mobilewhack.com/reviews/toshiba_satellite_a105-s4004_notebook.html)

---

### Post by krismatth3 on 2006-04-17
I see. Why do you say it's an SATA cd-rom drive? Those are very rare. Have you tried the devices /dev/hda - /dev/hdd? In every SATA equipped computer I've seen, the cdrom drive still uses IDE.

Edit 2: Can you post the output of "sudo lshw"? Easiset to do is: "sudo lshw > info.txt" then open up info.txt and paste its contents.

---

