---
title: "sata port disabled: ignoring"
date: 2011-11-06
forum: General Help
---

### Post by jeabraham on 2011-11-06
Hi.

I just installed a new hard drive but can't see it in any of the admin tools like parted, fdisk, webmin.

Following a hint in this form, I typed 

```
sudo cat /var/log/dmesg | grep ata

```and see that ata2 is disabled.  The new hard drive is physically on ata2.

Could this be a bios setting?  Or is it something in the linux settings?  Or is it a hard drive problem?

(Although I have physical access to the machine right now, I'm at the remote "data centre", i.e. vacation home, and don't have any VGA monitor or USB keyboard to enable me to access the bios during boot.)

Below is the full output of grepping dmesg.  Thanks in advance for any help.

John 

```
[    0.000000]  BIOS-e820: 000000003f6f2000 - 000000003f6ff000 (ACPI data)
[    0.000000] PERCPU: Allocating 41952 bytes of per cpu data
[   24.149640] Memory: 1010156k/1039360k available (2523k kernel code, 27112k reserved, 1331k data, 328k init)
[   26.773046] libata version 3.00 loaded.
[   27.235771] ata_piix 0000:00:1f.1: version 2.12
[   27.237148] scsi0 : ata_piix
[   27.238776] scsi1 : ata_piix
[   27.239221] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x20b0 irq 14
[   27.239225] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x20b8 irq 15
[   27.595168] ata1.00: ATAPI: SONY    CD-ROM CDU5225, NYS4, max UDMA/33
[   27.814748] ata1.00: configured for UDMA/33
[   27.814807] ata2: port disabled. ignoring.
[   27.825896] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   27.827634] scsi2 : ata_piix
[   27.829252] scsi3 : ata_piix
[   27.829931] ata3: SATA max UDMA/133 cmd 0x20c8 ctl 0x20ec bmdma 0x20a0 irq 19
[   27.829935] ata4: SATA max UDMA/133 cmd 0x20c0 ctl 0x20e8 bmdma 0x20a8 irq 19
[   28.024662] ata3.00: ATA-8: ST31000340AS, SD15, max UDMA/133
[   28.024667] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   28.074153] ata3.01: HPA unlocked: 3907029168 -> 0, native 18446744073321613488
[   28.074158] ata3.01: ATA-8: ST2000DL003-9VT166, CC3C, max UDMA/133
[   28.074160] ata3.01: 0 sectors, multi 16: LBA NCQ (depth 0/32)
[   28.114518] ata3.00: configured for UDMA/133
[   28.154426] ata3.01: failed to set max address (err_mask=0x1)
[   28.154429] ata3.01: device aborted resize (0 -> 268435455), skipping HPA handling
[   28.154439] ata3.01: configured for UDMA/133
[   30.890068] EXT3-fs: mounted filesystem with ordered data mode.


```

---

### Post by dcstar on 2011-11-06
> **jeabraham said:**
> Hi.

I just installed a new hard drive but can't see it in any of the admin tools like parted, fdisk, webmin.

Following a hint in this form, I typed 

```
sudo cat /var/log/dmesg | grep ata

```and see that ata2 is disabled.  The new hard drive is physically on ata2.
.........

Really, it is a an old IDE drive connected to the second IDE channel is it?

---

### Post by jeabraham on 2011-11-06
> **dcstar said:**
> Really, it is a an old IDE drive connected to the second IDE channel is it?

No it is a brand new 2TB drive on the #2 SATA port.

---

### Post by jeabraham on 2011-11-06
> **dcstar said:**
> Really, it is a an old IDE drive connected to the second IDE channel is it?

Ok I see your point, ata1 is my CD Rom, not my first SATA drive.  And it's using the PATA interface, not SATA.

I don't know where my first SATA drive is, I suppose it might be ata3 in dmesg.  Then ata4 might be my SATA 2 port on the motherboard?  How would I know?

I see a /dev/sda which is my working hard drive, and a /dev/sdb which is the other, but when I do

```
sudo fdisk /dev/sdb
```I just get
```
Unable to read /dev/sdb
```--
John

---

