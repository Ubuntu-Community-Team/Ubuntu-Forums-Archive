---
title: "Hard drive help please"
date: 2006-03-18
forum: General Help
---

### Post by Clark_Bent on 2006-03-18
After installing Kubuntu, I was amazed at how great it went. But I am having one problem that I am hoping one of you could help me with. I can't seem to get one of my drives recognized. I have a drive that is hanging off a PCI controller. 

me@ubuntu:/$ lspci | grep -i ide
0000:00:1f.1 IDE interface: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) UltraATA-100 IDE Controller (rev 02)
me@ubuntu:/$              

I think this is the controller. Some info from dmesg too:

me@ubuntu:/$ dmesg | grep -i ide
[4294673.881000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.881000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294673.881000] ACPI: bus type ide registered
[4294673.887000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[4294673.887000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[4294673.887000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:DMA
[4294673.887000] Probing IDE interface ide0...
[4294674.458000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.459000] Probing IDE interface ide1...
[4294675.437000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.437000] Probing IDE interface ide2...
[4294675.950000] Probing IDE interface ide3...
[4294676.462000] Probing IDE interface ide4...
[4294676.974000] Probing IDE interface ide5...
[4294677.505000]  /dev/ide/host0/bus0/target0/lun0: p1
[4294677.530000]  /dev/ide/host0/bus0/target1/lun0: p1 p2 < p5 >

HDA is a windows drive. This isn't the drive I am having trouble with. HDB is the drive I installed Kubuntu too. And HDD is my dvd writer. Would be most grateful for any help. I'm really stumped on this one.

---

### Post by Steve1961 on 2006-03-18
> **Clark_Bent]After installing Kubuntu, I was amazed at how great it went. But I am having one problem that I am hoping one of you could help me with. I can't seem to get one of my drives recognized. I have a drive that is hanging off a PCI controller. 

me@ubuntu:/$ lspci | grep -i ide
0000:00:1f.1 IDE interface: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) UltraATA-100 IDE Controller (rev 02)
me@ubuntu:/$              

I think this is the controller. Some info from dmesg too:

me@ubuntu:/$ dmesg | grep -i ide
[4294673.881000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.881000] ide: Assuming 33MHz system bus speed for PIO modes said:**
>  ACPI: bus type ide registered
[4294673.887000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[4294673.887000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[4294673.887000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:DMA
[4294673.887000] Probing IDE interface ide0...
[4294674.458000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294674.459000] Probing IDE interface ide1...
[4294675.437000] ide1 at 0x170-0x177,0x376 on irq 15
[4294675.437000] Probing IDE interface ide2...
[4294675.950000] Probing IDE interface ide3...
[4294676.462000] Probing IDE interface ide4...
[4294676.974000] Probing IDE interface ide5...
[4294677.505000]  /dev/ide/host0/bus0/target0/lun0: p1
[4294677.530000]  /dev/ide/host0/bus0/target1/lun0: p1 p2 < p5 >

HDA is a windows drive. This isn't the drive I am having trouble with. HDB is the drive I installed Kubuntu too. And HDD is my dvd writer. Would be most grateful for any help. I'm really stumped on this one.


Does it show up when you type sudo fdisk -l in a terminal?

---

### Post by Clark_Bent on 2006-03-18
No...wish it did:

me@ubuntu:/$ sudo fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14216   114189988+  83  Linux
/dev/hdb2           14217       14593     3028252+   5  Extended
/dev/hdb5           14217       14593     3028221   82  Linux swap / Solaris
me@ubuntu:/$

---

### Post by Steve1961 on 2006-03-18
[QUOTE=Clark_Bent]No...wish it did:

me@ubuntu:/$ sudo fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14216   114189988+  83  Linux
/dev/hdb2           14217       14593     3028252+   5  Extended
/dev/hdb5           14217       14593     3028221   82  Linux swap / Solaris
me@ubuntu:/$[/QUOTE]


In that case it looks like your PCI card controller might not be supported, and to be honest I'm not sure what to suggest.  Anybody have any ideas?

---

### Post by Clark_Bent on 2006-03-18
I suspect it most likely is supported...but the only reason I say that is because it was working under FreeBSD. I'm just assuming.

---

### Post by Clark_Bent on 2006-03-18
Well, I think I have this figured out. I was running the stock kernel that is installed. Decided what the heck. I'll go download the latest sources from kernel.org and install using steps detailed within the wiki on this site (thanks to the author...awesome job). I think I hit pay dirt:

 Vendor: ATA       Model: WDC WD4000KD-00N  Rev: 01.0
  Type:   Direct-Access                      ANSI SCSI revision: 05
e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
e100: Copyright(c) 1999-2005 Intel Corporation
ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 21
e100: eth0: e100_probe: addr 0xfeafd000, irq 21, MAC addr 00:07:E9:6E:2
C:84
SCSI device sda: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sda: drive cache: write back
SCSI device sda: 781422768 512-byte hdwr sectors (400088 MB)
SCSI device sda: drive cache: write back


Thats her right there. I think I just need to create my file systems and edit /etc/fstab with the applicable info and I'm off to the races.....

What shocks me is the stock ubuntu kernel config has pretty much everything under the sun configured as a module. I'm really amazed it didn't work out of the gate. But it looks like it is going to now...and I think I have found a new favorite distro....most impressive so far.

\\:D/

---

