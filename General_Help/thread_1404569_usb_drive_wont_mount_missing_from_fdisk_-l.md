---
title: "usb drive wont mount missing from fdisk -l"
date: 2010-02-11
forum: General Help
---

### Post by tatt on 2010-02-11
I have a remote headless server of which I have an SSH connection to.
I have 2 identical usb drives for this fileserver for backup.
I have automated cron and rsync running the backups at 2AM each day.

Each day the girl in the office removes the drive and plugs in the other one and then takes the backup from the office home each night is case of disaster.

This has all worked fine for a while until a recent update.

The server is not mounting any of the usb drives when plugged. I will attach some logs.

dmesg is listing the device SDC connecting when it is plugged in.
The other two devices SDA and SDB are fixed disks in the server.

The following dmesg outputs are from a rebbot. I cannot plug in/out the disk at the moment. The server is remote.

> uname -a
Linux fileserver 2.6.24-26-generic #1 SMP Tue Dec 1 17:55:03 UTC 2009 x86_64 GNU/Linux


> dmesg | grep -i scsi
[   21.782352] SCSI subsystem initialized
[   22.325145] scsi0 : ata_piix
[   22.325173] scsi1 : ata_piix
[   23.013403] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW SHM-165P6S MS0R PQ: 0 ANSI: 5
[   23.013588] scsi2 : ata_piix
[   23.013637] scsi3 : ata_piix
[   23.071099] scsi4 : SCSI emulation for USB Mass Storage devices
[   23.392948] scsi 2:0:0:0: Direct-Access     ATA      WDC WD800AAJS-00 05.0 PQ: 0 ANSI: 5
[   23.393103] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 05.0 PQ: 0 ANSI: 5
[   23.403131] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   23.403197] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   23.403372]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   23.405446] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   23.405459] scsi 3:0:0:0: Attached scsi generic sg2 type 0
[   23.434990] sd 2:0:0:0: [sda] Attached SCSI disk
[   23.449781] sd 3:0:0:0: [sdb] Attached SCSI disk
[   28.058812] scsi 4:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[   28.060097] sd 4:0:0:0: [sdc] Attached SCSI disk
[   28.060127] sd 4:0:0:0: Attached scsi generic sg3 type 0


> dmesg | grep -i sdc
[   28.060097] sd 4:0:0:0: [sdc] Attached SCSI disk



> sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007d0e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9118    73240303+  83  Linux
/dev/sda2            9119        9729     4907857+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000240

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux



> lsusb
Bus 005 Device 002: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

> lsmod | grep -i usb
usb_storage            82624  0 
libusual               23648  1 usb_storage
scsi_mod              178744  5 sg,sd_mod,sr_mod,usb_storage,libata
usbcore               170288  5 usb_storage,libusual,ehci_hcd,uhci_hcd


> /proc/scsi/usb-storage$ cat 4
   Host scsi4: usb-storage
       Vendor: JMicron
      Product: USB to ATA/ATAPI Bridge
Serial Number: 152D20329000
     Protocol: Transparent SCSI
    Transport: Bulk
       Quirks:





If I remote desktop connect to the server gparted only shows sda and sdb.




Any help would be greatly appreciated.

Chris

---

### Post by tatt on 2010-02-13
Bump

---

### Post by tatt on 2010-02-21
can anyone help me with this?????

---

