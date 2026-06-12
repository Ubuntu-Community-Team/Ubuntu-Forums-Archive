---
title: "ubuntu won't boot need help trouble shooting"
date: 2011-09-19
forum: General Help
---

### Post by iconoclast hero on 2011-09-19
Here is my output from [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

It worked this morning.  Yesterday I tried out unuty, but it booted after that.  The hdd won't boot on another computer and this one will boot with CDRom.


```
 
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector
    1 of the same hard drive for core.img. core.img is at this location and
    looks in partition 1 for (,msdos1)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Mounting failed:   mount: /dev/sda1 already mounted or sda1 busy

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:
    Boot files:

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   861,466,623   861,466,561  83 Linux
/dev/sda2    *    861,466,624   871,706,623    10,240,000   7 NTFS / exFAT / HPFS
/dev/sda3         871,708,670   976,771,071   105,062,402   5 Extended
/dev/sda5         871,710,720   875,804,671     4,093,952  82 Linux swap / Solaris
/dev/sda6         875,806,720   976,769,023   100,962,304  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs
/dev/sda1        b2323c52-4613-40f2-aec3-d3f1fbf16e4a   ext4
/dev/sda2        908868038867E5E6                       ntfs
/dev/sda5        82b4a03f-9aba-462c-963f-40d45afd35ca   swap       swap
/dev/sda6        b7877ac1-450e-4a63-ad74-6417bdf1c79c   ext4       /home

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect
--------------------------------------------------------------------------------




```

---

### Post by iconoclast hero on 2011-09-20
Update and bump:
Partitioned /dev/sda1 to create a new primary partition /dev/sda4 and installed a fresh copy of 10.10.  When I rebooted, I was able to get GRUB to show both the new 10.10 install on /dev/sda4 and the old one on /dev/sda1, so I am currently booted into my old system.  What is the best way to undo this, i.e. how do I best remove the new installation, GRUB entry, and partition rolling that space back into /dev/sda1?

---

