---
title: "can't detach/eject  /dev/sdb"
date: 2011-09-17
forum: General Help
---

### Post by moonpoppy on 2011-09-17
there is no device in /dev/sdb. in disk utility it appears as generic sd firmware 1.0. 

i get this when i do dmesg:

[    7.507145] scsi 4:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[    7.508193] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    7.508970] sd 4:0:0:0: Attached scsi generic sg1 type 0

and when i do this:

 sg_sync --verbose /dev/sdb
    synchronize cache(10) cdb: 35 00 00 00 00 00 00 00 00 00 
synchronize cache(10):  Fixed format, current;  Sense key: Illegal Request
 Additional sense: Invalid field in cdb
  Sense Key Specific: Error in Command byte 1
bad field in Synchronize cache command
[t@a~]$ sg_start --stop --verbose /dev/sdb
    Start stop unit command: 1b 00 00 00 00 00

and wheni do this:

[t@a ~]$ cd /dev
[t@a dev]$ ls s*
sda  sda1  sda2  sda5  **sdb**  sg0  sg1  snapshot  stderr  stdin  stdout


in disk utility, there is no option to eject or safely remove it. i can't detach it with udisks. it does not appear in gparted.

my bios is fine (no beeps). ran a memtest and that was fine too.

any idea on what i can do detach, eject or remove it?

---

### Post by dcstar on 2011-09-18
> **moonpoppy said:**
> there is no device in /dev/sdb. in disk utility it appears as generic sd firmware 1.0. 

i get this when i do dmesg:

[    7.507145] scsi 4:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[    7.508193] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    7.508970] sd 4:0:0:0: Attached scsi generic sg1 type 0

and when i do this:

 sg_sync --verbose /dev/sdb
    synchronize cache(10) cdb: 35 00 00 00 00 00 00 00 00 00 
synchronize cache(10):  Fixed format, current;  Sense key: Illegal Request
 Additional sense: Invalid field in cdb
  Sense Key Specific: Error in Command byte 1
bad field in Synchronize cache command
[t@a~]$ sg_start --stop --verbose /dev/sdb
    Start stop unit command: 1b 00 00 00 00 00

and wheni do this:

[t@a ~]$ cd /dev
[t@a dev]$ ls s*
sda  sda1  sda2  sda5  **sdb**  sg0  sg1  snapshot  stderr  stdin  stdout


in disk utility, there is no option to eject or safely remove it. i can't detach it with udisks. it does not appear in gparted.

my bios is fine (no beeps). ran a memtest and that was fine too.

any idea on what i can do detach, eject or remove it?

It seems to be a SD card reader device that spawns dev/sg0, so use that.

---

### Post by moonpoppy on 2011-09-18
dcstar, thanks so much for your response!

i tried to unmount/detach, etc via umount and udisks. both said there was nothing mounted. i tried to do mkfs and said that there was nothing there to format. here's what udisks said exactly...

sudo udisks --detach /dev/sg1 (I did the same for dev/sg0)
Device file /dev/sg1 is not a block device: Resource temporarily unavailable

and umount
sudo umount /dev/sg1 
umount: /dev/sg1: not mounted


i tried ug3-utils and go this info:
sudo sg_scan -i
/dev/sg0: scsi0 channel=0 id=0 lun=0 [em]
    ATA       Hitachi HTS54322  ESBO [rmb=0 cmdq=0 pqual=0 pdev=0x0] 
/dev/sg1: scsi4 channel=0 id=0 lun=0 [em]
    Generic-  xD/SD/M.S.        1.00 [rmb=1 cmdq=0 pqual=0 pdev=0x0] 

any other advice?

---

### Post by moonpoppy on 2011-09-18
cat /proc/scsi/scsi 
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: Hitachi HTS54322 Rev: ESBO
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: Generic- Model: xD/SD/M.S.       Rev: 1.00
  Type:   Direct-Access                    ANSI  SCSI revision: 02

sudo sg_map
Password: 
/dev/sg0  /dev/sda
/dev/sg1  /dev/sdb


the original usb stick was corrupted when i tried to reformat it via disk utility. so it's not an option to use it to solve the problem.

---

### Post by dcstar on 2011-09-19
> **moonpoppy said:**
> 
.........
the original usb stick was corrupted when i tried to reformat it via disk utility. so it's not an option to use it to solve the problem.

You might want to use **gparted** to write a new partition table to it.

---

