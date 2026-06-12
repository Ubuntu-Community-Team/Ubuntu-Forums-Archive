---
title: "udev warning on boot re: RAID on non-boot HDD"
date: 2010-10-02
forum: General Help
---

### Post by spleach on 2010-10-02
I'm branching this thread off from [http://ubuntuforums.org/showthread.php?t=1497230](http://ubuntuforums.org/showthread.php?t=1497230)

The symptom of this problem occurs only on boot, with udevd warnings each and every time; now  and then it will continue to check one or two of my disk drives for  problems.
I've got 3 SATA drives (2 in a RAID0; the boot disk outside  the RAID) & 1 SAS drive, so I assume it checks the RAID drives, as the udevd add_notify_watch warnings refer to the RAID disks. It's  more of a nuisance than anything else, but I'd love to know the  solution.

I think the fix would include stopping udevd from trying  to mount & read the RAID drives, but to instead read from their  partitions... I think udevadm holds the key... Just looked at it's  database with 
```
udevadm info --export -db | less
```
and searched for '/dev/sd'. 
Here's what it says about one of the RAID drives:-
```
P: /devices/pci0000:00/0000:00:1f.2/host3/target3:0:0/3:0:0:0/block/sda
N: sda
W: 73
S: block/8:0
S: disk/by-id/ata-WDC_WD3000HLFS-01G6U1_WD-WXL1C10C8246
S: disk/by-id/scsi-SATA_WDC_WD3000HLFS-_WD-WXL1C10C8246
S: disk/by-path/pci-0000:00:1f.2-scsi-2:0:0:0
S: disk/by-id/wwn-0x50014ee0ace6049d
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1f.2/host3/target3:0:0/3:0:0:0/block/sda
E: MAJOR=8
E: MINOR=0
E: DEVNAME=/dev/sda
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: ID_ATA=1
E: ID_TYPE=disk
E: ID_BUS=ata
E: ID_MODEL=WDC_WD3000HLFS-01G6U1
E: ID_MODEL_ENC=WDC\x20WD3000HLFS-01G6U1\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
E: ID_REVISION=04.04V20
E: ID_SERIAL=WDC_WD3000HLFS-01G6U1_WD-WXL1C10C8246
E: ID_SERIAL_SHORT=WD-WXL1C10C8246
E: ID_ATA_WRITE_CACHE=1
E: ID_ATA_WRITE_CACHE_ENABLED=1
E: ID_ATA_FEATURE_SET_HPA=1
E: ID_ATA_FEATURE_SET_HPA_ENABLED=1
E: ID_ATA_FEATURE_SET_PM=1
E: ID_ATA_FEATURE_SET_PM_ENABLED=1
E: ID_ATA_FEATURE_SET_SECURITY=1
E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=48
E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=48
E: ID_ATA_FEATURE_SET_SMART=1
E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
E: ID_ATA_FEATURE_SET_AAM=1
E: ID_ATA_FEATURE_SET_AAM_ENABLED=1
E: ID_ATA_FEATURE_SET_AAM_VENDOR_RECOMMENDED_VALUE=128
E: ID_ATA_FEATURE_SET_AAM_CURRENT_VALUE=254
E: ID_ATA_DOWNLOAD_MICROCODE=1
E: ID_ATA_SATA=1
E: ID_ATA_SATA_SIGNAL_RATE_GEN2=1
E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
E: ID_ATA_ROTATION_RATE_RPM=10000
E: ID_WWN=0x50014ee0ace6049d
E: ID_WWN_WITH_EXTENSION=0x50014ee0ace6049d
E: ID_SCSI_COMPAT=SATA_WDC_WD3000HLFS-_WD-WXL1C10C8246
E: ID_PATH=pci-0000:00:1f.2-scsi-2:0:0:0
E: ID_FS_VERSION=1.0.00
E: ID_FS_TYPE=isw_raid_member
E: ID_FS_USAGE=raid
E: UDISKS_PRESENTATION_NOPOLICY=0
E: UDISKS_ATA_SMART_IS_AVAILABLE=1
E: DEVLINKS=/dev/block/8:0  /dev/disk/by-id/ata-WDC_WD3000HLFS-01G6U1_WD-WXL1C10C8246  /dev/disk/by-id/scsi-SATA_WDC_WD3000HLFS-_WD-WXL1C10C8246  /dev/disk/by-path/pci-0000:00:1f.2-scsi-2:0:0:0  /dev/disk/by-id/wwn-0x50014ee0ace6049d

```

If anyone could shed some light on solving this, I'd be much obliged.

If it helps, I'm running Ubuntu 10.04 LTS x86_64. I have dmraid installed but not gparted. The RAID is BIOS configured with Intel ICH10, with 3 partitions: 105MB windows system partition, 300GB Windows boot drive on NTFS, and 300GB ext4 partition for Windows on Virtual Box. The SAS controller is by Marvell, with both of the HD controllers built into an Asus P6T7 Supercomputer mobo.
Cheers

---

### Post by psusi on 2010-10-02
What is the problem again?  I don't see it.

---

### Post by spleach on 2010-10-02
On booting, I always get a couple of warnings i.e.

```
udevd-work[pid]: inotify_add_watch(6, /dev/sda, 10) failed: no such file or directory
udevd-work[pid2]: inotify_add_watch(6, /dev/sdb, 10) failed: no such file or directory
```

where pid / pid2 are 3 digit integers. I'm sure booting wastes a second or two trying to find these drives too, but these drives shouldn't be mounted directly as they're part of a RAID0 array configured in the BIOS.
So I have /etc/fstab configured to mount two of the RAID partitions with their UUIDs and they mount fine; it's just these udev warnings that bug me, and the occasional occasion when it continues to check one or two drives for errors.

That clearer??

---

### Post by psusi on 2010-10-02
So?  Ignore those.  Fsck is run periodically, that is normal.

---

### Post by JohnFante on 2010-10-11
Sorry in advance for the long post. 

I have the same problem but a little different setup thou.

Two 500gb discs in Raid0 on the ICH10R. The first partition 100 mb Windows 7 system (gaming etc.) and then 300gb for the actual Windos install. Then Ubuntu 10.10 with /, /home, /swap and then 5 data partitions. Grub is on the Windows system partition.

Besides that I have 2x300gb dics on the Gigabyte built ind raid controller. Installed with a Hackintos setup using Mac software raid.

Both on 10.04 and now on 10.10 I get the following error:

udevd-work[157]: inotify_add_watch(6, /dev/dm-1, 10) failed: no such file or directory

udevd-work[179]: inotify_add_watch(6, /dev/dm-1, 10) failed: no such file or directory

It comes once a while but not all the time. I used the standard x64 USB install method.

My fstab looks like this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_diefbafiah_Volume05 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_diefbafiah_Volume06 /home           ext4    defaults        0       2
/dev/mapper/isw_diefbafiah_Volume012 /home/Backup    ext4    defaults        0       2
/dev/mapper/isw_diefbafiah_Volume09 /home/Emulatorer ext4    defaults        0       2
/dev/mapper/isw_diefbafiah_Volume010 /home/Games     ext4    defaults        0       2
/dev/mapper/isw_diefbafiah_Volume08 /home/Musik     ext4    defaults        0       2
/dev/mapper/isw_diefbafiah_Volume011 /home/VMware    ext4    defaults        0       2
/dev/mapper/isw_diefbafiah_Volume07 none            swap    sw              0       0
```

The only thing I can see missing is the Windows partitions. They are mounted visible in Natilus so they are there. Can that be the problem?

Things get weird thou when I try to use gparted to check if I can see my partitions. Then I get (translated form danish:

======================
libparted : 2.3
======================
Can not have a partition outside the dics!
Invalid partitionstabel på /dev/sdb - wrong signatur 4aa7

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...

Any suggestions?

And while we are at it. Any suggestions for a hardware raidcard that works "out of the box" on linux?

---

### Post by blausand on 2010-11-02
I get the very same error message, but i get dropped into the [FONT="Courier New"](initramfs)[/FONT] shell.
_My Setup:_
[LIST]
[*]Two 500GB on Intel PM55
[*]in the BIOS, i setup
[*]one RAID0 (mirror, ca. 100GB) for the OSs
[*]one RAID1 (stripe, ca. 700GB) for swap and data
[/LIST]

**Windows 7** partitions the RAID0 into: 
[INDENT]   1MB FREE SPACE
~100MB EFI blabla
~140MB Windows idonnow
~ 60GB Windows 7 actual system partition[/INDENT]

After installing completed, Windows worked perfectly.

Now, i install **UbuntuStudio 10.10 64bit**, doing this on the intaller's partitioning stage:

[LIST]
[*]on the RAID0:
40GB ext4 as /
[*]on the RAID1:
  12GB Linux Swap
~680GB ext4 as /av for (externally redundant) media data.
[/LIST]

On my first attempt, i setup a 1MB [FONT="Courier New"]/boot[/FONT] Partition, on the second attempt, i didn't.

However, in both cases, when restarting, it says: 
```
Gave up waiting for root device.
```
And furtheron:
```
ALERT! /dev/disk/by-uuid/XXXX-bla-XXX does not exist.
```
In fact, when listing [FONT="Courier New"]/dev/disk/by-uuid/[/FONT] there is no such uuid.

:confused: I really wonder why, in 2010, two of the major Operating Systems are not capable of recognizing each other, not to speak about healing broken bootmanager data...
Can anybody give some *relevant* links on how to repair those [COLOR="Red"]rotten lines of inconsistency[/COLOR], please?

---

