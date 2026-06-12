---
title: "Messed up ext3 disk"
date: 2011-04-01
forum: General Help
---

### Post by thavox on 2011-04-01
Hi I have messed up one of my partitions and need help.


I thought it would be a good thing to check my 1TB ext3 disk for faults so I pushed the "check and fix" button in the "Disk utility 2.30.1" ("Diskverktyg 2.30.1" in my swedish disribution). This seriously messed up the disk. It wont mount and this is displayed in dmesg:

************
[ 4092.150079] usb 1-1: new high speed USB device using ehci_hcd and address 6
[ 4092.302226] usb 1-1: configuration #1 chosen from 1 choice
[ 4092.322390] scsi7 : SCSI emulation for USB Mass Storage devices
[ 4092.330560] usb-storage: device found at 6
[ 4092.330568] usb-storage: waiting for device to settle before scanning
[ 4097.330338] usb-storage: device scan complete
[ 4097.331457] scsi 7:0:0:0: Direct-Access     SAMSUNG  HD103UI          1111 PQ: 0 ANSI: 2 CCS
[ 4097.337000] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 4097.341766] sd 7:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[ 4097.342497] sd 7:0:0:0: [sdc] Write Protect is off
[ 4097.342507] sd 7:0:0:0: [sdc] Mode Sense: 00 38 00 00
[ 4097.342514] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 4097.351722] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 4097.351741]  sdc: sdc1 < sdc5 sdc6 sdc7 sdc8 sdc9 sdc10 > sdc2
[ 4097.408140] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 4097.408155] sd 7:0:0:0: [sdc] Attached SCSI disk
[ 4098.649303] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[ 4098.665342] SGI XFS Quota Management subsystem
[ 4098.669036] XFS: bad version
[ 4098.669041] XFS: SB validate failed
************

"sudo dumpe2fs -f /dev/sdc2" gives:
dumpe2fs 1.41.11 (14-Mar-2010)
dumpe2fs: Bad magic number in super-block vid försök att öppna /dev/sdc2
Kunde inte hitta giltigt filsystemssuperblock.
**
In english:
Bad magic number in super-block when trying to open /dev/sdc2
Could not find a valid filesystem super-block.
************

sudo fsck.ext3 /dev/sdc2 gives:
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext3: Superblocket är ogiltigt, försöker med reservblock ...
fsck.ext3: Bad magic number in super-block vid försök att öppna /dev/sdc2

Superblocket kunde inte läsas eller beskriver inte ett korrekt
ext2-filsystem.  Om enheten är giltig och den verkligen innehåller ett
ext2-filsystem (och inte växlingsutrymme eller ufs eller något annat)
är superblocket trasigt, och du kan försöka köra med ett alternativt
superblock:
    e2fsck -b 8193 <enhet>
**
In english:
fsck.ext3: Superblocke is invalid, trying backup block...
fsck.ext3: Bad magic number in super-block when trying to open /dev/sdc2

Could not read superblock or the superblock does not describe a correct ext2 filesystem. If the unit is valid and it really holds a ext2-filesystem (and not a swap space of ufs or something else) then the the superblock is broken, and you can try using an alternative superblock:
    e2fsck -b 8193 <enhet>

************

This though does not work, it gives the exact same result as above. I tried all possible superblocks.


I'm lost. Please help. Is it possible to fix the disk? Can the files be extracted somehow? or, Am I screwed?

---

### Post by cbowman57 on 2011-04-01
I don't have any sage advice but GParted seems to have some recovery capability now.

Download their iso and give it a try.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by thavox on 2011-04-02
I installed GParted and that solved another problem :) but not this problem :(

GParted use "e2fsck -f -v -y /dev/sdc*" for controlling and fixing disks. But I just used the normal program, not the live iso. The disk with the error isn't a system disk.

As said the main problem still exsists. e2fsck (and GParted) seems unable to handle this error since they need a valid super-block, and that I do not have. :(

---

### Post by thavox on 2011-04-02
Ok, now I have a plan.

1. Order new disk -check!
2. Wait for delivery -in progress...
3. Make sector-by-sector copy of the faulty partition (/dev/sdc2) to the new disk with dd .
4. Try to fix the copy with TestDisk ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)) and/or debugfs.
5. Hope for the best.

The hardest part so far is the waiting. It challanges the strenght of my patiens, which isn't very good.


I'll be back and report the outcome...

---

### Post by thavox on 2011-04-12
ok. Now I tried it all. Or something close to it.

TestDisk could not help me. It didn't find any valid superblock.

Photorec at least saved some sh*t but nothing I really wanted. Well I didn't loose any valuable stuff anyway. I do use backup for such stuff!

Now I have to re-rip all my CD:s and DVD:s...  *boring!*


So long and thanx for all the fish!
/Mr. "I just lost 1TB of data"

---

