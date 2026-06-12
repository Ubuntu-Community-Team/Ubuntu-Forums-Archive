---
title: "Mount FAT32 External Drive when switched on ..."
date: 2012-07-10
forum: General Help
---

### Post by Bucky Ball on 2012-07-10
Hi all,

I have an old external drive which is eSATA to my laptop. In 10.10 it connected without issue and up popped the three partition on the drive.

I'm using Xubuntu 10.04 now and, sure, the partitions appear but don't mount. When I open a file manager as root I can access them but otherwise permission denied. 

When I mount, for instance, /dev/sdd5 in /mnt/SOUND there are no permission problems and I can mount all three partitions fine like this (but cumbersome), read/write and all fine.

So, anyone know how I can get the three FAT partitions on the external eSATA drive automounting when I switch it on, as it did in 10.10 (and all other releases but 10.04 LTS)? 

(Don't confuse this with 'when I boot the computer'. The external is only used occasionally so don't need to auto-mount at boot. Tnx in advance. ;)

---

### Post by Bucky Ball on 2012-07-11
Just wondering; if I add something like this to fstab:

```
/dev/sdc5 /mnt/FAT32partition vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0

```... will this be a problem if sdc5 is not there (ext HDD off) when the machine is booted (seem to remember wasn't on another setup in the past) and will this then recognise the external drive and partitions when I switch on the drive, whenever that may be?

* 10.04 BTW.

---

### Post by HermanAB on 2012-07-11
Howdy,

Fstab is read at boot.  So if the drive is not plugged in before you boot, then it will not be mounted and if it is listed in fstab, then the automount system for removable media will ignore it, so it will remain unmounted if you plug it in later.  

However, you can mount it manually afterwards with 'mount -a'.

---

### Post by Bucky Ball on 2012-07-11
Switch drive on, they are mounting somewhere I guess as they're appearing and when I right click asks if I want to 'Unmount Drive'. This is part of the dmesg directly after I switch on, before I've tried to access the partitions:

```
[ 9454.569237] ata5: limiting SATA link speed to 1.5 Gbps
[ 9454.569242] ata5: hard resetting link
[ 9460.361237] ata5: link is slow to respond, please be patient (ready=0)
[ 9462.340397] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 9462.341398] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[ 9462.341564] ata5.00: ACPI cmd ef/10:02:00:00:00:a0 (SET FEATURES) succeeded
[ 9462.341570] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 9462.341787] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[ 9462.363023] ata5.00: ATA-8: WDC WD5000AACS-00ZUB0, 01.01B01, max UDMA/133
[ 9462.363027] ata5.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[ 9462.364130] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[ 9462.364137] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[ 9462.364358] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[ 9462.364672] ata5.00: configured for UDMA/133
[ 9462.364692] ata5: EH complete
[ 9462.364819] scsi 4:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 01.0 PQ: 0 ANSI: 5
[ 9462.364999] sd 4:0:0:0: [sdd] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 9462.365125] sd 4:0:0:0: [sdd] Write Protect is off
[ 9462.365131] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[ 9462.365176] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 9462.365271] sd 4:0:0:0: Attached scsi generic sg3 type 0
[ 9462.408653]  sdd: sdd1 < sdd5 sdd6 sdd7 >
[ 9462.409159] sd 4:0:0:0: [sdd] Attached SCSI disk
```

Not quite understanding why the eSATA connection is getting cut to 1.5Gb (yes, both devices are capable of it). Maybe something to do with FAT32, one of the reasons on want to clear that drive and reformat. ;)

---

### Post by Bucky Ball on 2012-07-11
Oddly, mount -a does nothing. When I right click in pcmanfm and 'mount' that way, it mounts fine. Just no permission. So, I am changing this to how to change permissions. The weird thing is that once it's mounted in /media (after I click it in the file manager), I have no permission, but if I then manually mount /media/partition in /mnt/partition, all good. I have permissions. Which is why I'm reluctant to change them.

Hmm, odd.

---

