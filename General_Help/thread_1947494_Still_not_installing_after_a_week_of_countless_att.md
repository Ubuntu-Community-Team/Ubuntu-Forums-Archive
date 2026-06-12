---
title: "Still not installing after a week of countless attempts"
date: 2012-03-26
forum: General Help
---

### Post by momo101 on 2012-03-26
Hi Guys,
Pasted below is the text from the results file as suggested in another thread after someone else got a similar "dev/disl/by-uuid/f4cee...." error message after rebooting and selecting Ubuntu.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/mapper/isw_bdaaeadaea_ARRAY0.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_bdaaeadaea_ARRAY01: ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_bdaaeadaea_ARRAY02: ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_bdaaeadaea_ARRAY03: ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       160,649       160,587  de Dell Utility
/dev/sda2             161,792    31,619,071    31,457,280   7 NTFS / exFAT / HPFS
/dev/sda3    *     31,619,072 1,953,533,951 1,921,914,880   7 NTFS / exFAT / HPFS

/dev/sda3 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


Drive: isw_bdaaeadaea_ARRAY0 _____________________________________________________________________

Disk /dev/mapper/isw_bdaaeadaea_ARRAY0: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953536512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_bdaaeadaea_ARRAY01                 63       160,649       160,587  de Dell Utility
/dev/mapper/isw_bdaaeadaea_ARRAY02            161,792    31,619,071    31,457,280   7 NTFS / exFAT / HPFS
/dev/mapper/isw_bdaaeadaea_ARRAY03   *     31,619,072 1,953,533,951 1,921,914,880   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_bdaaeadaea_ARRAY0p1 07D9-041D                              vfat       DellUtility
/dev/mapper/isw_bdaaeadaea_ARRAY0p2 1030EA1030E9FD1A                       ntfs       RECOVERY
/dev/mapper/isw_bdaaeadaea_ARRAY0p3 F4CEECA0CEEC5BFC                       ntfs       OS
/dev/sda                                                isw_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_bdaaeadaea_ARRAY0
isw_bdaaeadaea_ARRAY0p1
isw_bdaaeadaea_ARRAY0p2
isw_bdaaeadaea_ARRAY0p3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda3


Unknown BootLoader on isw_bdaaeadaea_ARRAY01


Unknown BootLoader on isw_bdaaeadaea_ARRAY02


Unknown BootLoader on isw_bdaaeadaea_ARRAY03



========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/mapper/isw_bdaaeadaea_ARRAY01: No such file or directory
hexdump: /dev/mapper/isw_bdaaeadaea_ARRAY01: No such file or directory
hexdump: /dev/mapper/isw_bdaaeadaea_ARRAY02: No such file or directory
hexdump: /dev/mapper/isw_bdaaeadaea_ARRAY02: No such file or directory
hexdump: /dev/mapper/isw_bdaaeadaea_ARRAY03: No such file or directory
hexdump: /dev/mapper/isw_bdaaeadaea_ARRAY03: No such file or directory

```

Much appreciated if someone could assist as I just want to start using Ubuntu!

Momo.

---

### Post by mörgæs on 2012-03-26
Hi, welcome to the fora.

This thread is the best to search for Wubi problems:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by oldfred on 2012-03-26
I do not know RAID as I do not believe in it for most desktops and it is more advanced to manage.

But you have a problem:
```

/dev/sda3 ends after the last sector of /dev/sda
```

Script sees sda as  500GB and sdb as 1TB but RAID size is the same on both drives. So either sda is not seen as correct size or your RAID is sized incorrectly as both drives have to have identical sized partitions. Or you can only RAID 500GB of the 1TB drive.

The failed mounts are probably becaue of the RAID. You can add drivers to liveCD to work with fakeRAID.

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)
[http://ubuntuforums.org/showthread.php?t=1338445&page=5](http://ubuntuforums.org/showthread.php?t=1338445&page=5)
Software RAID w/mdadm driver

---

### Post by momo101 on 2012-03-27
Hi guys,
I'll have a look at the Raid setup after work tonight, I bought this DELL PC used with Vista installed and I upgraded it to Win 7. I suspect the Raid setup is the default setup by Dell with a Restore Partition which might be protected.

Momo

---

