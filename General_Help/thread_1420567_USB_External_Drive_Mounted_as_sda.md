---
title: "USB External Drive Mounted as sda"
date: 2010-03-03
forum: General Help
---

### Post by dudemanbubba on 2010-03-03
I have a server with 5 SATA hard drives.  A 320GB system drive and (4) 1TB drives setup in raid-5.

I have been using a usb WD external 1TB disk for my backups for Bacula.  Every thing has been working fine for weeks.  I believe I rebooted a couple times in that period with no issues.  I was doing some work remotely last evening and the system crashed.  I restarted the server this morning and the external disk mounted as sda.  The system booted but had some errors and weirdness.

Here is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 - System Drive
UUID=888c10e9-7cc8-4e85-959b-d378402df44a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=992b31b4-7311-45f5-8145-6d805873dee9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#RAID-5 using sdb1/sdc1/sdd1/sde1
/dev/md0        /mnt/raid       auto    defaults,acl    0       0
#/dev/sdf1 - USB 1TB Drive
UUID=535f7130-0f68-450b-8ae2-cf2ee7cc8e69  /mnt/backups  ext3  defaults  0  0

```I unplugged the USB drive, restarted and everything booted up fine.  I reconnected the drive and it mounted as sdf1 again and all is well.  I need to figure a way to prevent this from happening on a reboot in the future.

Is there a way to force the mounting of a particular UUID to always be a particular device letter?

Thanks in advance.

---

### Post by QLee on 2010-03-03
> **dudemanbubba said:**
> I have a server with 5 SATA hard drives.  A 320GB system drive and (4) 1TB drives setup in raid-5.

I have been using a usb WD external 1TB disk for my backups for Bacula.  Every thing has been working fine for weeks.  I believe I rebooted a couple times in that period with no issues.  I was doing some work remotely last evening and the system crashed.  I restarted the server this morning and the external disk mounted as sda.  The system booted but had some errors and weirdness.

Here is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 - System Drive
UUID=888c10e9-7cc8-4e85-959b-d378402df44a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=992b31b4-7311-45f5-8145-6d805873dee9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#RAID-5 using sdb1/sdc1/sdd1/sde1
/dev/md0        /mnt/raid       auto    defaults,acl    0       0
#/dev/sdf1 - USB 1TB Drive
UUID=535f7130-0f68-450b-8ae2-cf2ee7cc8e69  /mnt/backups  ext3  defaults  0  0

```I unplugged the USB drive, restarted and everything booted up fine.  I reconnected the drive and it mounted as sdf1 again and all is well.  I need to figure a way to prevent this from happening on a reboot in the future.

Is there a way to force the mounting of a particular UUID to always be a particular device letter?

Thanks in advance.

Well, it's my understanding that the use of UUID arose around the same time as changes to the way the kernel enumerates drives. I've encountered a problem similar to yours on an old mainboard that would sometimes change the device order on boot (not every time though). 

It seems your system handled the situation well and booted to the correct UUID, the way things are supposed to work. The statement "some errors and weirdness", doesn't give us much to speculate with. Does some of your system rely on device node notation and thus be in trouble if the order is rearranged?

Naturally it won't happen if your USB is turned off or unplugged until boot has finished, the next time you reboot that server.

---

### Post by dudemanbubba on 2010-03-03
The following is the syslog from the boot up.  It looks like it built the raid out of the same disks and adjusted to use sdc/sdd/sde/sdf (the four physical raid drives).  The USB drive was sda and the system drive became sdb.  There are some errors listed in the boot sequence about sda that I have no idea what they mean.

Again, it seems that there should be a way to force mounting of a particular uuid to a particular device.

Thanks for the reply!

```

Mar  3 07:07:41 ls1 kernel: [   39.799003] usb 1-2: configuration #1 chosen from 1 choice
Mar  3 07:07:41 ls1 kernel: [   39.807756] usbcore: registered new interface driver libusual
Mar  3 07:07:41 ls1 kernel: [   39.810170] Initializing USB Mass Storage driver...
Mar  3 07:07:41 ls1 kernel: [   39.810271] scsi0 : SCSI emulation for USB Mass Storage devices
Mar  3 07:07:41 ls1 kernel: [   39.810311] usb-storage: device found at 2
Mar  3 07:07:41 ls1 kernel: [   39.810313] usb-storage: waiting for device to settle before scanning
Mar  3 07:07:41 ls1 kernel: [   39.810316] usbcore: registered new interface driver usb-storage
Mar  3 07:07:41 ls1 kernel: [   39.810318] USB Mass Storage support registered.
Mar  3 07:07:41 ls1 kernel: [   40.677282] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
Mar  3 07:07:41 ls1 kernel: [   40.677287] ahci 0000:00:1f.2: flags: 64bit ncq pm led pmp slum part 
Mar  3 07:07:41 ls1 kernel: [   40.677292] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Mar  3 07:07:41 ls1 kernel: [   40.677468] scsi1 : ahci
Mar  3 07:07:41 ls1 kernel: [   40.677527] scsi2 : ahci
Mar  3 07:07:41 ls1 kernel: [   40.677564] scsi3 : ahci
Mar  3 07:07:41 ls1 kernel: [   40.677598] scsi4 : ahci
Mar  3 07:07:41 ls1 kernel: [   40.677631] scsi5 : ahci
Mar  3 07:07:41 ls1 kernel: [   40.677664] scsi6 : ahci
Mar  3 07:07:41 ls1 kernel: [   40.677683] ata1: SATA max UDMA/133 abar m1024@0xd8500400 port 0xd8500500 irq 19
Mar  3 07:07:41 ls1 kernel: [   40.677685] ata2: SATA max UDMA/133 abar m1024@0xd8500400 port 0xd8500580 irq 19
Mar  3 07:07:41 ls1 kernel: [   40.677687] ata3: SATA max UDMA/133 abar m1024@0xd8500400 port 0xd8500600 irq 19
Mar  3 07:07:41 ls1 kernel: [   40.677689] ata4: SATA max UDMA/133 abar m1024@0xd8500400 port 0xd8500680 irq 19
Mar  3 07:07:41 ls1 kernel: [   40.677691] ata5: SATA max UDMA/133 abar m1024@0xd8500400 port 0xd8500700 irq 19
Mar  3 07:07:41 ls1 kernel: [   40.677693] ata6: SATA max UDMA/133 abar m1024@0xd8500400 port 0xd8500780 irq 19
Mar  3 07:07:41 ls1 kernel: [   42.402671] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar  3 07:07:41 ls1 kernel: [   42.403508] ata1.00: ATA-8: WDC WD3202ABYS-02B7A0, 02.03B03, max UDMA/133
Mar  3 07:07:41 ls1 kernel: [   42.403510] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
Mar  3 07:07:41 ls1 kernel: [   42.404425] ata1.00: configured for UDMA/133
Mar  3 07:07:41 ls1 kernel: [   44.118097] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar  3 07:07:41 ls1 kernel: [   44.118824] ata2.00: ATA-8: WDC WD1002FBYS-02A6B0, 03.00C06, max UDMA/133
Mar  3 07:07:41 ls1 kernel: [   44.118826] ata2.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Mar  3 07:07:41 ls1 kernel: [   44.119617] ata2.00: configured for UDMA/133
Mar  3 07:07:41 ls1 kernel: [   44.799356] usb-storage: device scan complete
Mar  3 07:07:41 ls1 kernel: [   44.802349] scsi 0:0:0:0: Direct-Access     WD       My Book 1110     1030 PQ: 0 ANSI: 4
Mar  3 07:07:41 ls1 kernel: [   44.805341] scsi 0:0:0:1: CD-ROM            WD       Virtual CD 1110  1030 PQ: 0 ANSI: 4
Mar  3 07:07:41 ls1 kernel: [   44.808329] scsi 0:0:0:2: Enclosure         WD       SES Device       1030 PQ: 0 ANSI: 4
Mar  3 07:07:41 ls1 kernel: [   44.812089] Driver 'sd' needs updating - please use bus_type methods
Mar  3 07:07:41 ls1 kernel: [   44.813927] sd 0:0:0:0: Attached scsi generic sg0 type 0
Mar  3 07:07:41 ls1 kernel: [   44.813940] scsi 0:0:0:1: Attached scsi generic sg1 type 5
Mar  3 07:07:41 ls1 kernel: [   44.813955] scsi 0:0:0:2: Attached scsi generic sg2 type 13
Mar  3 07:07:41 ls1 kernel: [   44.814828] Driver 'sr' needs updating - please use bus_type methods
Mar  3 07:07:41 ls1 kernel: [   44.816309] sd 0:0:0:0: [sda] 1952151552 512-byte hardware sectors (999502 MB)
Mar  3 07:07:41 ls1 kernel: [   44.819299] sd 0:0:0:0: [sda] Write Protect is off
Mar  3 07:07:41 ls1 kernel: [   44.819301] sd 0:0:0:0: [sda] Mode Sense: 23 00 10 00
Mar  3 07:07:41 ls1 kernel: [   44.819303] sd 0:0:0:0: [sda] Assuming drive cache: write through
Mar  3 07:07:41 ls1 kernel: [   44.824288] sd 0:0:0:0: [sda] 1952151552 512-byte hardware sectors (999502 MB)
Mar  3 07:07:41 ls1 kernel: [   44.827281] sd 0:0:0:0: [sda] Write Protect is off
Mar  3 07:07:41 ls1 kernel: [   44.827283] sd 0:0:0:0: [sda] Mode Sense: 23 00 10 00
Mar  3 07:07:41 ls1 kernel: [   44.827284] sd 0:0:0:0: [sda] Assuming drive cache: write through
Mar  3 07:07:41 ls1 kernel: [   44.827329]  sda: sda1
Mar  3 07:07:41 ls1 kernel: [   44.833319] sd 0:0:0:0: [sda] Attached SCSI disk
Mar  3 07:07:41 ls1 kernel: [   44.838263] sr0: scsi3-mmc drive: 51x/51x caddy
Mar  3 07:07:41 ls1 kernel: [   44.838265] Uniform CD-ROM driver Revision: 3.20
Mar  3 07:07:41 ls1 kernel: [   44.838295] sr 0:0:0:1: Attached scsi CD-ROM sr0
Mar  3 07:07:41 ls1 kernel: [   45.826041] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar  3 07:07:41 ls1 kernel: [   45.826770] ata3.00: ATA-8: WDC WD1002FBYS-02A6B0, 03.00C06, max UDMA/133
Mar  3 07:07:41 ls1 kernel: [   45.826772] ata3.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Mar  3 07:07:41 ls1 kernel: [   45.827577] ata3.00: configured for UDMA/133
Mar  3 07:07:41 ls1 kernel: [   47.531485] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar  3 07:07:41 ls1 kernel: [   47.532216] ata4.00: ATA-8: WDC WD1002FBYS-02A6B0, 03.00C06, max UDMA/133
Mar  3 07:07:41 ls1 kernel: [   47.532219] ata4.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Mar  3 07:07:41 ls1 kernel: [   47.533024] ata4.00: configured for UDMA/133
Mar  3 07:07:41 ls1 kernel: [   49.239426] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar  3 07:07:41 ls1 kernel: [   49.240142] ata5.00: ATA-8: WDC WD1002FBYS-02A6B0, 03.00C06, max UDMA/133
Mar  3 07:07:41 ls1 kernel: [   49.240144] ata5.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Mar  3 07:07:41 ls1 kernel: [   49.240946] ata5.00: configured for UDMA/133
Mar  3 07:07:41 ls1 kernel: [   49.587505] ata6: SATA link down (SStatus 0 SControl 300)
Mar  3 07:07:41 ls1 kernel: [   49.587608] scsi 1:0:0:0: Direct-Access     ATA      WDC WD3202ABYS-0 02.0 PQ: 0 ANSI: 5
Mar  3 07:07:41 ls1 kernel: [   49.587669] sd 1:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
Mar  3 07:07:41 ls1 kernel: [   49.587678] sd 1:0:0:0: [sdb] Write Protect is off
Mar  3 07:07:41 ls1 kernel: [   49.587680] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Mar  3 07:07:41 ls1 kernel: [   49.587691] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  3 07:07:41 ls1 kernel: [   49.587735] sd 1:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
Mar  3 07:07:41 ls1 kernel: [   49.587741] sd 1:0:0:0: [sdb] Write Protect is off
Mar  3 07:07:41 ls1 kernel: [   49.587743] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Mar  3 07:07:41 ls1 kernel: [   49.587753] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  3 07:07:41 ls1 kernel: [   49.587755]  sdb: sdb1 sdb2 < sdb5 >
Mar  3 07:07:41 ls1 kernel: [   49.615762] sd 1:0:0:0: [sdb] Attached SCSI disk
Mar  3 07:07:41 ls1 kernel: [   49.615786] sd 1:0:0:0: Attached scsi generic sg3 type 0
Mar  3 07:07:41 ls1 kernel: [   49.615845] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1002FBYS-0 03.0 PQ: 0 ANSI: 5
Mar  3 07:07:41 ls1 kernel: [   49.615884] sd 2:0:0:0: [sdc] 1953525168 512-byte hardware sectors (1000205 MB)
Mar  3 07:07:41 ls1 kernel: [   49.615890] sd 2:0:0:0: [sdc] Write Protect is off
Mar  3 07:07:41 ls1 kernel: [   49.615892] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Mar  3 07:07:41 ls1 kernel: [   49.615902] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  3 07:07:41 ls1 kernel: [   49.615924] sd 2:0:0:0: [sdc] 1953525168 512-byte hardware sectors (1000205 MB)
Mar  3 07:07:41 ls1 kernel: [   49.615930] sd 2:0:0:0: [sdc] Write Protect is off
Mar  3 07:07:41 ls1 kernel: [   49.615932] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Mar  3 07:07:41 ls1 kernel: [   49.615942] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  3 07:07:41 ls1 kernel: [   49.615944]  sdc: sdc1
Mar  3 07:07:41 ls1 kernel: [   49.632027] sd 2:0:0:0: [sdc] Attached SCSI disk
Mar  3 07:07:41 ls1 kernel: [   49.632059] sd 2:0:0:0: Attached scsi generic sg4 type 0
Mar  3 07:07:41 ls1 kernel: [   49.632138] scsi 3:0:0:0: Direct-Access     ATA      WDC WD1002FBYS-0 03.0 PQ: 0 ANSI: 5
Mar  3 07:07:41 ls1 kernel: [   49.632193] sd 3:0:0:0: [sdd] 1953525168 512-byte hardware sectors (1000205 MB)
Mar  3 07:07:41 ls1 kernel: [   49.632205] sd 3:0:0:0: [sdd] Write Protect is off
Mar  3 07:07:41 ls1 kernel: [   49.632207] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Mar  3 07:07:41 ls1 kernel: [   49.632225] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  3 07:07:41 ls1 kernel: [   49.632262] sd 3:0:0:0: [sdd] 1953525168 512-byte hardware sectors (1000205 MB)
Mar  3 07:07:41 ls1 kernel: [   49.632272] sd 3:0:0:0: [sdd] Write Protect is off
Mar  3 07:07:41 ls1 kernel: [   49.632273] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Mar  3 07:07:41 ls1 kernel: [   49.632290] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  3 07:07:41 ls1 kernel: [   49.632292]  sdd: sdd1
Mar  3 07:07:41 ls1 kernel: [   49.641518] sd 3:0:0:0: [sdd] Attached SCSI disk
Mar  3 07:07:41 ls1 kernel: [   49.641544] sd 3:0:0:0: Attached scsi generic sg5 type 0
Mar  3 07:07:41 ls1 kernel: [   49.641594] scsi 4:0:0:0: Direct-Access     ATA      WDC WD1002FBYS-0 03.0 PQ: 0 ANSI: 5
Mar  3 07:07:41 ls1 kernel: [   49.641634] sd 4:0:0:0: [sde] 1953525168 512-byte hardware sectors (1000205 MB)
Mar  3 07:07:41 ls1 kernel: [   49.641641] sd 4:0:0:0: [sde] Write Protect is off
Mar  3 07:07:41 ls1 kernel: [   49.641642] sd 4:0:0:0: [sde] Mode Sense: 00 3a 00 00
Mar  3 07:07:41 ls1 kernel: [   49.641652] sd 4:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  3 07:07:41 ls1 kernel: [   49.641677] sd 4:0:0:0: [sde] 1953525168 512-byte hardware sectors (1000205 MB)
Mar  3 07:07:41 ls1 kernel: [   49.641683] sd 4:0:0:0: [sde] Write Protect is off
Mar  3 07:07:41 ls1 kernel: [   49.641684] sd 4:0:0:0: [sde] Mode Sense: 00 3a 00 00
Mar  3 07:07:41 ls1 kernel: [   49.641694] sd 4:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  3 07:07:41 ls1 kernel: [   49.641696]  sde: sde1
Mar  3 07:07:41 ls1 kernel: [   49.655406] sd 4:0:0:0: [sde] Attached SCSI disk
Mar  3 07:07:41 ls1 kernel: [   49.655430] sd 4:0:0:0: Attached scsi generic sg6 type 0
Mar  3 07:07:41 ls1 kernel: [   49.655488] scsi 5:0:0:0: Direct-Access     ATA      WDC WD1002FBYS-0 03.0 PQ: 0 ANSI: 5
Mar  3 07:07:41 ls1 kernel: [   49.655534] sd 5:0:0:0: [sdf] 1953525168 512-byte hardware sectors (1000205 MB)
Mar  3 07:07:41 ls1 kernel: [   49.655544] sd 5:0:0:0: [sdf] Write Protect is off
Mar  3 07:07:41 ls1 kernel: [   49.655545] sd 5:0:0:0: [sdf] Mode Sense: 00 3a 00 00
Mar  3 07:07:41 ls1 kernel: [   49.655562] sd 5:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  3 07:07:41 ls1 kernel: [   49.655593] sd 5:0:0:0: [sdf] 1953525168 512-byte hardware sectors (1000205 MB)
Mar  3 07:07:41 ls1 kernel: [   49.655603] sd 5:0:0:0: [sdf] Write Protect is off
Mar  3 07:07:41 ls1 kernel: [   49.655604] sd 5:0:0:0: [sdf] Mode Sense: 00 3a 00 00
Mar  3 07:07:41 ls1 kernel: [   49.655620] sd 5:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar  3 07:07:41 ls1 kernel: [   49.655623]  sdf: sdf1
Mar  3 07:07:41 ls1 kernel: [   49.666465] sd 5:0:0:0: [sdf] Attached SCSI disk
Mar  3 07:07:41 ls1 kernel: [   49.666489] sd 5:0:0:0: Attached scsi generic sg7 type 0
Mar  3 07:07:41 ls1 kernel: [   49.666550] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 17 (level, low) -> IRQ 17
Mar  3 07:07:41 ls1 kernel: [   49.668287] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Mar  3 07:07:41 ls1 kernel: [   49.668293] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Mar  3 07:07:41 ls1 kernel: [   49.668346] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Mar  3 07:07:41 ls1 kernel: [   49.672244] ehci_hcd 0000:00:1d.7: debug port 1
Mar  3 07:07:41 ls1 kernel: [   49.672248] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Mar  3 07:07:41 ls1 kernel: [   49.672254] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xd8500000
Mar  3 07:07:41 ls1 kernel: [   49.688558] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar  3 07:07:41 ls1 kernel: [   49.688667] usb usb5: configuration #1 chosen from 1 choice
Mar  3 07:07:41 ls1 kernel: [   49.688688] hub 5-0:1.0: USB hub found
Mar  3 07:07:41 ls1 kernel: [   49.688699] hub 5-0:1.0: 8 ports detected
Mar  3 07:07:41 ls1 kernel: [   49.753059] md: md0 stopped.
Mar  3 07:07:41 ls1 kernel: [   49.800951] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Mar  3 07:07:41 ls1 kernel: [   49.800985] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Mar  3 07:07:41 ls1 kernel: [   49.800996] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Mar  3 07:07:41 ls1 kernel: [   49.804011] ata_piix 0000:00:1f.1: version 2.12
Mar  3 07:07:41 ls1 kernel: [   49.804022] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Mar  3 07:07:41 ls1 kernel: [   49.804050] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Mar  3 07:07:41 ls1 kernel: [   49.804105] scsi7 : ata_piix
Mar  3 07:07:41 ls1 kernel: [   49.804148] scsi8 : ata_piix
Mar  3 07:07:41 ls1 kernel: [   49.804456] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
Mar  3 07:07:41 ls1 kernel: [   49.804459] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[B]Mar  3 07:07:41 ls1 kernel: [   49.839587] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Mar  3 07:07:41 ls1 kernel: [   49.839592] end_request: I/O error, dev sda, sector 1952151424
Mar  3 07:07:41 ls1 kernel: [   49.839595] Buffer I/O error on device sda1, logical block 244018672
Mar  3 07:07:41 ls1 kernel: [   49.839681] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Mar  3 07:07:41 ls1 kernel: [   49.839684] end_request: I/O error, dev sda, sector 1952151424
Mar  3 07:07:41 ls1 kernel: [   49.839686] Buffer I/O error on device sda1, logical block 244018672
Mar  3 07:07:41 ls1 kernel: [   49.839793] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Mar  3 07:07:41 ls1 kernel: [   49.839795] end_request: I/O error, dev sda, sector 1952151424
Mar  3 07:07:41 ls1 kernel: [   49.839797] Buffer I/O error on device sda, logical block 244018928
Mar  3 07:07:41 ls1 kernel: [   49.839879] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Mar  3 07:07:41 ls1 kernel: [   49.839881] end_request: I/O error, dev sda, sector 1952151424
Mar  3 07:07:41 ls1 kernel: [   49.839883] Buffer I/O error on device sda, logical block 244018928
M[/B]ar  3 07:07:41 ls1 kernel: [   49.840841] md: bind<sdd1>
Mar  3 07:07:41 ls1 kernel: [   49.840982] md: bind<sde1>
Mar  3 07:07:41 ls1 kernel: [   49.841107] md: bind<sdf1>
Mar  3 07:07:41 ls1 kernel: [   49.841242] md: bind<sdc1>
Mar  3 07:07:41 ls1 kernel: [   49.845672] raid5: device sdc1 operational as raid disk 0
Mar  3 07:07:41 ls1 kernel: [   49.845674] raid5: device sdf1 operational as raid disk 3
Mar  3 07:07:41 ls1 kernel: [   49.845676] raid5: device sde1 operational as raid disk 2
Mar  3 07:07:41 ls1 kernel: [   49.845678] raid5: device sdd1 operational as raid disk 1
Mar  3 07:07:41 ls1 kernel: [   49.846043] raid5: allocated 4274kB for md0
Mar  3 07:07:41 ls1 kernel: [   49.846045] raid5: raid level 5 set md0 active with 4 out of 4 devices, algorithm 2
Mar  3 07:07:41 ls1 kernel: [   49.846048] RAID5 conf printout:
Mar  3 07:07:41 ls1 kernel: [   49.846049]  --- rd:4 wd:4
Mar  3 07:07:41 ls1 kernel: [   49.846050]  disk 0, o:1, dev:sdc1
Mar  3 07:07:41 ls1 kernel: [   49.846051]  disk 1, o:1, dev:sdd1
Mar  3 07:07:41 ls1 kernel: [   49.846052]  disk 2, o:1, dev:sde1
Mar  3 07:07:41 ls1 kernel: [   49.846053]  disk 3, o:1, dev:sdf1
Mar  3 07:07:41 ls1 kernel: [   49.847411] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[B]Mar  3 07:07:41 ls1 kernel: [   49.847414] end_request: I/O error, dev sda, sector 1952151424
Mar  3 07:07:41 ls1 kernel: [   49.847416] Buffer I/O error on device sda1, logical block 244018672
Mar  3 07:07:41 ls1 kernel: [   49.847511] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Mar  3 07:07:41 ls1 kernel: [   49.847514] end_request: I/O error, dev sda, sector 1952151424
Mar  3 07:07:41 ls1 kernel: [   49.847516] Buffer I/O error on device sda1, logical block 244018672
Mar  3 07:07:41 ls1 kernel: [   49.847616] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Mar  3 07:07:41 ls1 kernel: [   49.847619] end_request: I/O error, dev sda, sector 1952151536
Mar  3 07:07:41 ls1 kernel: [   49.847620] Buffer I/O error on device sda1, logical block 244018686
Mar  3 07:07:41 ls1 kernel: [   49.847709] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Mar  3 07:07:41 ls1 kernel: [   49.847711] end_request: I/O error, dev sda, sector 1952151536
Mar  3 07:07:41 ls1 kernel: [   49.847713] Buffer I/O error on device sda1, logical block 244018686
Mar  3 07:07:41 ls1 kernel: [   49.847820] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Mar  3 07:07:41 ls1 kernel: [   49.847822] end_request: I/O error, dev sda, sector 1952151424
Mar  3 07:07:41 ls1 kernel: [   49.847823] Buffer I/O error on device sda, logical block 244018928
Mar  3 07:07:41 ls1 kernel: [   49.847914] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Mar  3 07:07:41 ls1 kernel: [   49.847916] end_request: I/O error, dev sda, sector 1952151424
Mar  3 07:07:41 ls1 kernel: [   49.847918] Buffer I/O error on device sda, logical block 244018928
Mar  3 07:07:41 ls1 kernel: [   49.848017] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Mar  3 07:07:41 ls1 kernel: [   49.848019] end_request: I/O error, dev sda, sector 1952151536
Mar  3 07:07:41 ls1 kernel: [   49.848062] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Mar  3 07:07:41 ls1 kernel: [   49.848065] end_request: I/O error, dev sda, sector 1952151536
Mar  3 07:07:41 ls1 kernel: [   49.863041] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Mar  3 07:07:41 ls1 kernel: [   49.863045] end_request: I/O error, dev sda, sector 1952151424
Mar  3 07:07:41 ls1 kernel: [   49.863085] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Mar  3 07:07:41 ls1 kernel: [   49.863088] end_request: I/O error, dev sda, sector 1952151424
Mar  3 07:07:41 ls1 kernel: [   49.863135] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Mar  3 07:07:41 ls1 kernel: [   49.863137] end_request: I/O error, dev sda, sector 1952151536
Mar  3 07:07:41 ls1 kernel: [   49.863176] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Mar  3 07:07:41 ls1 kernel: [   49.863178] end_request: I/O error, dev sda, sector 1952151536
Mar  3 07:07:41 ls1 kernel: [   49.863233] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Mar  3 07:07:41 ls1 kernel: [   49.863235] end_request: I/O error, dev sda, sector 1952151424
Mar  3 07:07:41 ls1 kernel: [   49.863273] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Mar  3 07:07:41 ls1 kernel: [   49.863275] end_request: I/O error, dev sda, sector 1952151424
Mar  3 07:07:41 ls1 kernel: [   49.863321] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Mar  3 07:07:41 ls1 kernel: [   49.863323] end_request: I/O error, dev sda, sector 1952151536
Mar  3 07:07:41 ls1 kernel: [   49.863361] sd 0:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK[/B]
Mar  3 07:**07:41 ls1 kernel: [   49.863363] end_request: I/O error, dev sda, sector 1952151536**
Mar  3 07:07:41 ls1 kernel: [   50.076554] usb 5-2: new high speed USB device using ehci_hcd and address 2
Mar  3 07:07:41 ls1 kernel: [   50.136818] ata7.00: ATAPI: HL-DT-STDVD-RAM GH22NP20, 2.00, max UDMA/66
Mar  3 07:07:41 ls1 kernel: [   50.227309] usb 5-2: configuration #1 chosen from 1 choice
Mar  3 07:07:41 ls1 kernel: [   50.227432] scsi9 : SCSI emulation for USB Mass Storage devices
Mar  3 07:07:41 ls1 kernel: [   50.227472] usb-storage: device found at 2
Mar  3 07:07:41 ls1 kernel: [   50.227473] usb-storage: waiting for device to settle before scanning
Mar  3 07:07:41 ls1 kernel: [   50.227534] usb 1-2: USB disconnect, address 2
Mar  3 07:07:41 ls1 kernel: [   50.316401] ata7.00: configured for UDMA/66
Mar  3 07:07:41 ls1 kernel: [   50.316436] ata8: port disabled. ignoring.
Mar  3 07:07:41 ls1 kernel: [   50.317538] scsi 7:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NP20 2.00 PQ: 0 ANSI: 5
Mar  3 07:07:41 ls1 kernel: [   50.322254] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Mar  3 07:07:41 ls1 kernel: [   50.322287] sr 7:0:0:0: Attached scsi CD-ROM sr0
Mar  3 07:07:41 ls1 kernel: [   50.322315] sr 7:0:0:0: Attached scsi generic sg0 type 5
Mar  3 07:07:41 ls1 kernel: [   50.409124] Attempting manual resume
Mar  3 07:07:41 ls1 kernel: [   50.409127] swsusp: Resume From Partition 8:21
Mar  3 07:07:41 ls1 kernel: [   50.409128] PM: Checking swsusp image.
Mar  3 07:07:41 ls1 kernel: [   50.409242] PM: Resume from disk failed.
Mar  3 07:07:41 ls1 kernel: [   50.434767] kjournald starting.  Commit interval 5 seconds
Mar  3 07:07:41 ls1 kernel: [   50.434781] EXT3-fs: mounted filesystem with ordered data mode.
Mar  3 07:07:41 ls1 kernel: [   52.556257] parport_pc 00:0c: reported by Plug and Play ACPI
Mar  3 07:07:41 ls1 kernel: [   52.556363] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Mar  3 07:07:41 ls1 kernel: [   52.568375] input: PC Speaker as /devices/platform/pcspkr/input/input2
Mar  3 07:07:41 ls1 kernel: [   52.577463] EDAC MC: Ver: 2.1.0 Jan 27 2010
Mar  3 07:07:41 ls1 kernel: [   52.578319] EDAC MC0: Giving out device to 'i5000_edac.c' 'I5000': DEV 0000:00:10.0
Mar  3 07:07:41 ls1 kernel: [   52.578335] EDAC PCI0: Giving out device to module 'i5000_edac' controller 'EDAC PCI controller': DEV '0000:00:10.0' (POLLED)
Mar  3 07:07:41 ls1 kernel: [   52.582251] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar  3 07:07:41 ls1 kernel: [   52.594646] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar  3 07:07:41 ls1 kernel: [   52.608833] iTCO_vendor_support: vendor-support=0
Mar  3 07:07:41 ls1 kernel: [   52.610015] input: Power Button (FF) as /devices/virtual/input/input3
Mar  3 07:07:41 ls1 kernel: [   52.610760] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Mar  3 07:07:41 ls1 kernel: [   52.875711] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Mar  3 07:07:41 ls1 kernel: [   52.875715] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
Mar  3 07:07:41 ls1 kernel: [   52.903654] ACPI: Power Button (FF) [PWRF]
Mar  3 07:07:41 ls1 kernel: [   52.903777] input: Power Button (CM) as /devices/virtual/input/input4
Mar  3 07:07:41 ls1 kernel: [   53.024617] ACPI: Power Button (CM) [PWRB]
Mar  3 07:07:41 ls1 kernel: [   53.144106] input: ImExPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Mar  3 07:07:41 ls1 kernel: [   53.293495] iTCO_wdt: Found a 631xESB/632xESB TCO device (Version=2, TCOBASE=0x1060)
Mar  3 07:07:41 ls1 kernel: [   53.293524] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Mar  3 07:07:41 ls1 kernel: [   53.341840] intel_rng: FWH not detected
Mar  3 07:07:41 ls1 kernel: [   53.464000] NET: Registered protocol family 10
Mar  3 07:07:41 ls1 kernel: [   53.464169] lo: Disabled Privacy Extensions
Mar  3 07:07:41 ls1 kernel: [   53.929359] loop: module loaded
Mar  3 07:07:41 ls1 kernel: [   53.941270] lp0: using parport0 (interrupt-driven).
Mar  3 07:07:41 ls1 kernel: [   54.118964] Adding 11871992k swap on /dev/sdb5.  Priority:-1 extents:1 across:11871992k
Mar  3 07:07:41 ls1 kernel: [   54.480043] EXT3 FS on sdb1, internal journal
Mar  3 07:07:41 ls1 kernel: [   54.744403] kjournald starting.  Commit interval 5 seconds
Mar  3 07:07:41 ls1 kernel: [   54.770278] EXT3 FS on md0, internal journal
Mar  3 07:07:41 ls1 kernel: [   54.770282] EXT3-fs: mounted filesystem with ordered data mode.
Mar  3 07:07:41 ls1 kernel: [   55.165099] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar  3 07:07:41 ls1 kernel: [   55.217923] usb-storage: device scan complete
Mar  3 07:07:41 ls1 kernel: [   55.218670] scsi 9:0:0:0: Direct-Access     WD       My Book 1110     1030 PQ: 0 ANSI: 4
Mar  3 07:07:41 ls1 kernel: [   55.219408] scsi 9:0:0:1: CD-ROM            WD       Virtual CD 1110  1030 PQ: 0 ANSI: 4
Mar  3 07:07:41 ls1 kernel: [   55.220157] scsi 9:0:0:2: Enclosure         WD       SES Device       1030 PQ: 0 ANSI: 4
Mar  3 07:07:41 ls1 kernel: [   55.221398] sd 9:0:0:0: [sda] 1952151552 512-byte hardware sectors (999502 MB)
Mar  3 07:07:41 ls1 kernel: [   55.223142] sd 9:0:0:0: [sda] Write Protect is off
Mar  3 07:07:41 ls1 kernel: [   55.223144] sd 9:0:0:0: [sda] Mode Sense: 23 00 10 00
Mar  3 07:07:41 ls1 kernel: [   55.223145] sd 9:0:0:0: [sda] Assuming drive cache: write through
Mar  3 07:07:41 ls1 kernel: [   55.224266] sd 9:0:0:0: [sda] 1952151552 512-byte hardware sectors (999502 MB)
Mar  3 07:07:41 ls1 kernel: [   55.226011] sd 9:0:0:0: [sda] Write Protect is off
Mar  3 07:07:41 ls1 kernel: [   55.226013] sd 9:0:0:0: [sda] Mode Sense: 23 00 10 00
Mar  3 07:07:41 ls1 kernel: [   55.226015] sd 9:0:0:0: [sda] Assuming drive cache: write through
Mar  3 07:07:41 ls1 kernel: [   55.226074]  sda: sda1
Mar  3 07:07:41 ls1 kernel: [   55.226682] sd 9:0:0:0: [sda] Attached SCSI disk
Mar  3 07:07:41 ls1 kernel: [   55.226711] sd 9:0:0:0: Attached scsi generic sg1 type 0
Mar  3 07:07:41 ls1 kernel: [   55.233005] sr1: scsi3-mmc drive: 51x/51x caddy
Mar  3 07:07:41 ls1 kernel: [   55.233033] sr 9:0:0:1: Attached scsi CD-ROM sr1
Mar  3 07:07:41 ls1 kernel: [   55.233057] sr 9:0:0:1: Attached scsi generic sg2 type 5
Mar  3 07:07:41 ls1 kernel: [   55.233104] scsi 9:0:0:2: Attached scsi generic sg8 type 13

```

---

### Post by psusi on 2010-03-03
Looks like your external drive has a bad sector.  What does its partition table look like?  Run sudo fdusk -ul /dev/sda and post the results.  Also try sudo dd if=/dev/sda bs=512 skip=1952151424 count=1 of=/dev/null and see if that complains.

---

### Post by dudemanbubba on 2010-03-03
Didn't seem to complain...  After rebooting without usb attached and then attaching it after boot, the drive showed up ad sdf as it should have.

The following is the output using sdf:

```
administrator@ls1:/mnt/raid/Restore$ sudo fdisk -ul /dev/sdf

Disk /dev/sdf: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders, total 1952151552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002ae3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            2048  1952151551   976074752   83  Linux
administrator@ls1:/mnt/raid/Restore$ sudo dd if=/dev/sdf bs=512 skip=19521424 count=1 of=/dev/null
1+0 records in
1+0 records out
512 bytes (512 B) copied, 7.55505 s, 0.1 kB/s
administrator@ls1:/mnt/raid/Restore$

```

> Does some of your system rely on device node notation and thus be in trouble if the order is rearranged?

I used mdadm for the raid and I believe that used dev node.  Although, it seemed to adjust the raid accordingly based on the boot syslog.

---

### Post by psusi on 2010-03-03
Weird... I don't see why the kernel would even be trying to read that sector during boot or why it would fail.  You might just want to test reading the entire disk by dropping the count= and skip= parameters from that dd command.

---

