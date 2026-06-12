---
title: "Boot problem (no menu, &quot;Minimal BASH-like line editing...&quot;, grub&gt;)"
date: 2011-09-26
forum: General Help
---

### Post by tbauer on 2011-09-26
Trying to recover a Ubuntu version I was upgrading and had gotten to 10.10 but messed up while trying to increase partition size w/ GParted (didn't have space for 11.4).  Basically, I was trying to resize and deleted a smaller partition that I thought was the swap but apparently not.  Ran boot-repair under LiveCD (11.04) in an attempt to recover but couldn't point it at my partition that has Ubuntu (/dev/sda).    Currently when I boot it I get:

```
"Grub 1.97 beta 4" Minimal BASH-like line editing ... 
bash:grub
```

When I boot w/ LiveCD (11.04) and run BootInfoScript I get this:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /grub.

sda1: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    16,273,844    16,273,782  8e Linux LVM
/dev/sda2          16,273,845    16,771,859       498,015   5 Extended
/dev/sda5          16,273,908    16,771,859       497,952  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        KNAeN6-zRuZ-McXt-3fc3-ZXhD-Rl49-YlyFxm LVM2_member 
/dev/sda5        9a83da95-7204-4a87-bef1-b858bea2eaf7   ext2       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   7.934906960 = 8.520041472    grub/core.img                                  2
   7.775177956 = 8.348533760    initrd.img-2.6.31-14-server                   34
   7.807483673 = 8.383221760    initrd.img-2.6.31-16-server                   36
   7.822238922 = 8.399065088    initrd.img-2.6.31-22-server                   34
   7.764180183 = 8.336724992    vmlinuz-2.6.31-14-server                      16
   7.787733078 = 8.362014720    vmlinuz-2.6.31-16-server                      17
```


I have earlier snapshots of the environment that I could work from if people feel I messed this one up too much.  One that is right after I deleted the partitions I shouldn't have.  Another is way earlier (OS is Karmic) but seems to have its own issues (might be a bad copy).

Thoughts on how I might recover from this one?

---

### Post by tbauer on 2011-09-27
Here is the output from Bootrepairs "Boot Info Summary":

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /grub.

sda1: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/core.img

daisy-root': ___________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

daisy-swap_1': _________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    16,273,844    16,273,782  8e Linux LVM
/dev/sda2          16,273,845    16,771,859       498,015   5 Extended
/dev/sda5          16,273,908    16,771,859       497,952  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/daisy-root 469cf2ed-46e8-4c0b-8edf-a2a920682fb7   ext4       
/dev/mapper/daisy-swap_1 ffeb54a7-9527-4684-a3a3-29c4072cf5fb   swap       
/dev/sda1        KNAeN6-zRuZ-McXt-3fc3-ZXhD-Rl49-YlyFxm LVM2_member 
/dev/sda5        9a83da95-7204-4a87-bef1-b858bea2eaf7   ext2       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
daisy-root
daisy-swap_1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   7.934906960 = 8.520041472    grub/core.img                                  2
   7.775177956 = 8.348533760    initrd.img-2.6.31-14-server                   34
   7.807483673 = 8.383221760    initrd.img-2.6.31-16-server                   36
   7.822238922 = 8.399065088    initrd.img-2.6.31-22-server                   34
   7.764180183 = 8.336724992    vmlinuz-2.6.31-14-server                      16
   7.787733078 = 8.362014720    vmlinuz-2.6.31-16-server                      17

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on daisy-root'


Unknown BootLoader on daisy-swap_1'



=============================== StdErr Messages: ===============================

File descriptor 3 (pipe:[22618]) leaked on lvscan invocation. Parent PID 19076: bash
File descriptor 7 (pipe:[22618]) leaked on lvscan invocation. Parent PID 19076: bash
File descriptor 9 (/usr/lib/gio/modules/libgiobamf.so) leaked on lvscan invocation. Parent PID 19076: bash
File descriptor 63 (pipe:[28598]) leaked on lvscan invocation. Parent PID 19076: bash
File descriptor 3 (pipe:[22618]) leaked on lvdisplay invocation. Parent PID 19080: bash
File descriptor 7 (pipe:[22618]) leaked on lvdisplay invocation. Parent PID 19080: bash
File descriptor 9 (/usr/lib/gio/modules/libgiobamf.so) leaked on lvdisplay invocation. Parent PID 19080: bash
File descriptor 63 (pipe:[28598]) leaked on lvdisplay invocation. Parent PID 19080: bash
  One or more specified logical volume(s) not found.
File descriptor 3 (pipe:[22618]) leaked on lvdisplay invocation. Parent PID 19083: bash
File descriptor 7 (pipe:[22618]) leaked on lvdisplay invocation. Parent PID 19083: bash
File descriptor 9 (/usr/lib/gio/modules/libgiobamf.so) leaked on lvdisplay invocation. Parent PID 19083: bash
File descriptor 63 (pipe:[28598]) leaked on lvdisplay invocation. Parent PID 19083: bash
  One or more specified logical volume(s) not found.
File descriptor 3 (pipe:[22618]) leaked on lvchange invocation. Parent PID 18719: bash
File descriptor 7 (pipe:[22618]) leaked on lvchange invocation. Parent PID 18719: bash
File descriptor 9 (/usr/lib/gio/modules/libgiobamf.so) leaked on lvchange invocation. Parent PID 18719: bash
File descriptor 63 (pipe:[28598]) leaked on lvchange invocation. Parent PID 18719: bash
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/daisy-root': No such file or directory
hexdump: /dev/mapper/daisy-root': No such file or directory
File descriptor 3 (pipe:[22618]) leaked on lvdisplay invocation. Parent PID 19111: bash
File descriptor 7 (pipe:[22618]) leaked on lvdisplay invocation. Parent PID 19111: bash
File descriptor 9 (/usr/lib/gio/modules/libgiobamf.so) leaked on lvdisplay invocation. Parent PID 19111: bash
File descriptor 63 (pipe:[28598]) leaked on lvdisplay invocation. Parent PID 19111: bash
  One or more specified logical volume(s) not found.
File descriptor 3 (pipe:[22618]) leaked on lvdisplay invocation. Parent PID 19115: bash
File descriptor 7 (pipe:[22618]) leaked on lvdisplay invocation. Parent PID 19115: bash
File descriptor 9 (/usr/lib/gio/modules/libgiobamf.so) leaked on lvdisplay invocation. Parent PID 19115: bash
File descriptor 63 (pipe:[28598]) leaked on lvdisplay invocation. Parent PID 19115: bash
  One or more specified logical volume(s) not found.
File descriptor 3 (pipe:[22618]) leaked on lvchange invocation. Parent PID 18719: bash
File descriptor 7 (pipe:[22618]) leaked on lvchange invocation. Parent PID 18719: bash
File descriptor 9 (/usr/lib/gio/modules/libgiobamf.so) leaked on lvchange invocation. Parent PID 18719: bash
File descriptor 63 (pipe:[28598]) leaked on lvchange invocation. Parent PID 18719: bash
  One or more specified logical volume(s) not found.
hexdump: /dev/mapper/daisy-swap_1': No such file or directory
hexdump: /dev/mapper/daisy-swap_1': No such file or directory

ADDITIONAL INFORMATION :
**************** log of boot-repair 2011-09-27__04h01 ****************
boot-repair version : 3-0ppa7~natty
clean-ubiquity-common version : 3-0ppa6~natty
internet: connected
boot-repair-common version : 3.0-0ppa7~natty
/usr/share/clean/cleancommon-gui.sh: line 204: type: lvscan: not found
LVM2 package needed
Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
watershed
The following NEW packages will be installed:
lvm2 watershed
0 upgraded, 2 newly installed, 0 to remove and 254 not upgraded.
Need to get 425 kB of archives.
After this operation, 1,262 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ natty/main watershed amd64 5 [11.5 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ natty/main lvm2 amd64 2.02.66-4ubuntu2 [414 kB]
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin:
Selecting previously deselected package watershed.
(Reading database ... 134431 files and directories currently installed.)
Unpacking watershed (from .../archives/watershed_5_amd64.deb) ...
Selecting previously deselected package lvm2.
Unpacking lvm2 (from .../lvm2_2.02.66-4ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
Setting up watershed (5) ...
update-initramfs is disabled since running on read-only media
Setting up lvm2 (2.02.66-4ubuntu2) ...
update-initramfs is disabled since running on read-only media
LVBKID /dev/sda1: UUID="KNAeN6-zRuZ-McXt-3fc3-ZXhD-Rl49-YlyFxm" TYPE="LVM2_member"
/dev/sda5: UUID="9a83da95-7204-4a87-bef1-b858bea2eaf7" TYPE="ext2"
/dev/loop0: TYPE="squashfs"
MODPROBE
VGSCAN
File descriptor 3 (pipe:[22618]) leaked on vgscan invocation. Parent PID 5600: /bin/bash
File descriptor 7 (pipe:[22618]) leaked on vgscan invocation. Parent PID 5600: /bin/bash
File descriptor 9 (/usr/lib/gio/modules/libgiobamf.so) leaked on vgscan invocation. Parent PID 5600: /bin/bash
Reading all physical volumes.  This may take a while...
Found volume group "daisy" using metadata type lvm2
VGCHANGE
File descriptor 3 (pipe:[22618]) leaked on vgchange invocation. Parent PID 5600: /bin/bash
File descriptor 7 (pipe:[22618]) leaked on vgchange invocation. Parent PID 5600: /bin/bash
File descriptor 9 (/usr/lib/gio/modules/libgiobamf.so) leaked on vgchange invocation. Parent PID 5600: /bin/bash
2 logical volume(s) in volume group "daisy" now active
File descriptor 3 (pipe:[22618]) leaked on lvscan invocation. Parent PID 5600: /bin/bash
File descriptor 7 (pipe:[22618]) leaked on lvscan invocation. Parent PID 5600: /bin/bash
File descriptor 9 (/usr/lib/gio/modules/libgiobamf.so) leaked on lvscan invocation. Parent PID 5600: /bin/bash
LVSCAN:   ACTIVE            '/dev/daisy/root' [7.35 GiB] inherit
ACTIVE            '/dev/daisy/swap_1' [388.00 MiB] inherit
LIVESESSION is : yes
sda1 is LVM2_member
ls: cannot access /dev/mapper/daisy: No such file or directory
ls: cannot access /dev/mapper/daisy: No such file or directory
LVLINE ACTIVE            '/dev/daisy/root' [7.35 GiB] inherit
LVLINE ACTIVE            '/dev/daisy/swap_1' [388.00 MiB] inherit
BYTES_BEFORE_PART[1] (sda) = 63 sectors * 512 bytes = 32256 bytes.
ls: cannot access /sys/block/mapper/: No such file or directory
BYTES_BEFORE_PART[2] (mapper) = 2048 sectors * 512 bytes = 1048576 bytes.
OSPROBER: /dev/mapper/daisy-root:Ubuntu 9.10 (9.10):Ubuntu:linux
BLKID: /dev/sda1: UUID="KNAeN6-zRuZ-McXt-3fc3-ZXhD-Rl49-YlyFxm" TYPE="LVM2_member"
/dev/sda5: UUID="9a83da95-7204-4a87-bef1-b858bea2eaf7" TYPE="ext2"
/dev/loop0: TYPE="squashfs"
/dev/mapper/daisy-root: UUID="469cf2ed-46e8-4c0b-8edf-a2a920682fb7" TYPE="ext4"
/dev/mapper/daisy-swap_1: UUID="ffeb54a7-9527-4684-a3a3-29c4072cf5fb" TYPE="swap"
ls: cannot access /dev/mapper/daisy: No such file or directory
ls: cannot access /dev/mapper/daisy: No such file or directory
mapper/daisy-root contains Ubuntu 9.10 (linux)
1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.
dd: reading `/dev/mapper': Is a directory
0+0 records in
0+0 records out
Total of 1 OS detected on mapper disk.
mapper contains minimum one OS
Disk /dev/dm-0 doesn't contain a valid partition table
Disk /dev/dm-1 doesn't contain a valid partition table
FDISK
Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00061530

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    16273844     8136891   8e  Linux LVM
/dev/sda2        16273845    16771859      249007+   5  Extended
/dev/sda5        16273908    16771859      248976   83  Linux

Disk /dev/dm-0: 7889 MB, 7889485824 bytes
255 heads, 63 sectors/track, 959 cylinders, total 15409152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/dm-1: 406 MB, 406847488 bytes
255 heads, 63 sectors/track, 49 cylinders, total 794624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00061530

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    16273844     8136891   8e  Linux LVM
/dev/sda2        16273845    16771859      249007+   5  Extended
/dev/sda5        16273908    16771859      248976   83  Linux

Disk /dev/dm-0: 7889 MB, 7889485824 bytes
255 heads, 63 sectors/track, 959 cylinders, total 15409152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/dm-1: 406 MB, 406847488 bytes
255 heads, 63 sectors/track, 49 cylinders, total 794624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
sda5 : sda, is-maybe-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sda5, no-os, no-gpt, no-fstab.
mapper/daisy-root : mapper, not-sepboot, grub, aptget, 64, no boot, /mnt/clean/mapper/daisy-root, with-os, no-gpt, fstab-without-efi.
PARTED: Model: ATA VBOX HARDDISK (scsi)
Disk /dev/sda: 8590MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
1      32.3kB  8332MB  8332MB  primary                boot, lvm
2      8332MB  8587MB  255MB   extended
5      8332MB  8587MB  255MB   logical   ext2


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/daisy-swap_1: 407MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system     Flags
1      0.00B  407MB  407MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/daisy-root: 7889MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
1      0.00B  7889MB  7889MB  ext4



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.

                                                                          
Error: /dev/sr1: unrecognised disk label
MOUNT aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda5 on /mnt/clean/sda5 type ext2 (rw)
/dev/mapper/daisy-root on /mnt/clean/mapper/daisy-root type ext4 (rw)
/sys/block/dm-0:  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-1:  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  autofs block bsg btrfs-control bus cdrom cdrom1 char console core cpu cpu_dma_latency daisy disk dm-0 dm-1 dvd dvd1 ecryptfs fd full fuse hidraw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem pktcdvd port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 scd1 sda sda1 sda2 sda5 sg0 sg1 sg2 shm snapshot snd sr0 sr1 stderr stdin stdout uinput urandom usbmon0 usbmon1 vga_arbiter zero
/dev/mapper:  control daisy-root daisy-swap_1
Disk /dev/dm-0 doesn't contain a valid partition table
Disk /dev/dm-1 doesn't contain a valid partition table
DF Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    500M  109M  391M  22% /
none      devtmpfs    492M  648K  491M   1% /dev
/dev/sr0   iso9660    699M  699M     0 100% /cdrom
/dev/loop0
squashfs    665M  665M     0 100% /rofs
none         tmpfs    500M  176K  500M   1% /dev/shm
tmpfs        tmpfs    500M  624K  499M   1% /tmp
none         tmpfs    500M   92K  500M   1% /var/run
none         tmpfs    500M  4.0K  500M   1% /var/lock
/dev/sda5     ext2    228M   39M  178M  18% /mnt/clean/sda5
/dev/mapper/daisy-root
ext4    7.3G  4.3G  2.7G  62% /mnt/clean/mapper/daisy-root
FDISK
Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00061530

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    16273844     8136891   8e  Linux LVM
/dev/sda2        16273845    16771859      249007+   5  Extended
/dev/sda5        16273908    16771859      248976   83  Linux

Disk /dev/dm-0: 7889 MB, 7889485824 bytes
255 heads, 63 sectors/track, 959 cylinders, total 15409152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/dm-1: 406 MB, 406847488 bytes
255 heads, 63 sectors/track, 49 cylinders, total 794624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
Logs saved into /mnt/clean/mapper/daisy-root/var/log/clean/log/2011-09-27__04h01boot-repair52
combobox_ostoboot_bydefault_fillin
Order Linux according to their /boot type noorder
combobox_efi_fillin mapper/daisy-root
combobox_separateboot_fillin
set_checkbutton_reinstall_grub
set_radiobutton_ostoboot_bydefault
separate_bootpart and efi show_hide mapper/daisy-root
efi_show_hide 2 (no-gpt)
set_radiobutton_place_grub
separate_bootpart and efi show_hide mapper/daisy-root
efi_show_hide 2 (no-gpt)
************************Before mainwindow appear
PURGE_POSSIBLE yes PART_TO_REINSTALL_GRUB_PURGE 2 (mapper/daisy-root)
FSCK_ACTION yes PASTEBIN_ACTION no
REINSTALL_POSSIBLE yes MBR_ACTION reinstall UNHIDEBOOT_ACTION yes (10.s)
PART_TO_REINSTALL_GRUB 2 (mapper/daisy-root) FORCE_GRUB all NOFORCE_DISK mapper REMOVABLEDISK no UNCOMMENT_GFXMODE no ATA no-ata ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE  () USE_SEPARATEBOOTPART yes (sda5) grub-pc ()
/usr/share/clean/bootrepair.sh: line 56:  5624 Terminated              while true; do
done
RETOURCOMBO_purge_grub : mapper/daisy-root (Ubuntu 9.10)
RETOURCOMBO_ostoboot_bydefault : mapper/daisy-root (Ubuntu 9.10)
separate_bootpart and efi show_hide mapper/daisy-root
efi_show_hide 2 (no-gpt)
RETOURCOMBO_place_grub (NOFORCE_DISK) : mapper
RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sda5
set_radiobutton_place_alldisks
set_checkbutton_reinstall_grub
set_radiobutton_ostoboot_bydefault
separate_bootpart and efi show_hide mapper/daisy-root
efi_show_hide 2 (no-gpt)
set_radiobutton_place_grub
separate_bootpart and efi show_hide mapper/daisy-root
efi_show_hide 2 (no-gpt)
RETOURCOMBO_place_grub (NOFORCE_DISK) : mapper
set_radiobutton_place_grub
set_radiobutton_place_alldisks
internet: connected
************************Before Repairing
PURGE_POSSIBLE yes PART_TO_REINSTALL_GRUB_PURGE 2 (mapper/daisy-root)
FSCK_ACTION no PASTEBIN_ACTION yes
REINSTALL_POSSIBLE yes MBR_ACTION nombraction UNHIDEBOOT_ACTION no (10.s)
PART_TO_REINSTALL_GRUB 2 (mapper/daisy-root) FORCE_GRUB all NOFORCE_DISK mapper REMOVABLEDISK no UNCOMMENT_GFXMODE no ATA no-ata ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE  () USE_SEPARATEBOOTPART yes (sda5) grub-pc ()
Freed space function
/dev/mapper/daisy-root
/usr/share/clean/bootrepair-actions.sh: line 379: [[: /dev/mapper/daisy-root: syntax error: operand expected (error token is "/dev/mapper/daisy-root")
internet: connected
E: Unable to locate package pastebinit
Activate all repositories in /etc/apt/sources.list
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin:
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
Restore the original repositories in /etc/apt/sources.list
```

---

### Post by tbauer on 2011-09-27
When I try the CHROOT method discussed here 	• [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) I get an error when trying to mount the ubuntu partition drive (/hd/sda1) I get this error:

> unknown filesystem type LVM2_member

Not sure how to figure out the filesystem type given where I am at right now.   I ran sudo blkid and got:

```
/dev/sda1: UUID="KNAeN6-zRuZ-McXt-3fc3-ZXhD-Rl49-YlyFxm" TYPE="LVM2_member" 
/dev/sda5: UUID="9a83da95-7204-4a87-bef1-b858bea2eaf7" TYPE="ext2" 
/dev/loop0: TYPE="squashfs" 
/dev/mapper/daisy-root: UUID="469cf2ed-46e8-4c0b-8edf-a2a920682fb7" TYPE="ext4" 
/dev/mapper/daisy-swap_1: UUID="ffeb54a7-9527-4684-a3a3-29c4072cf5fb" TYPE="swap" 
```

Not sure if its safe to assume that the dev mapper entry for daisy-root being ext4 means LVM2_member should be ext 4.

---

### Post by tbauer on 2011-09-27
I tried to mount using -t and ext4 ... that got a new error saying the /dev/sda1 was already mounted or the mount was busy.   Definitely not mounted (checked fdisk -l).

To the inability to mount due to 'busy', I saw a post commenting that it might be a RAID / LVM issue.  I do see 'RAID' being detected by "Boot Repair" periodically and recall reading that LVM was part of the setup on RAID on Linux.   Could that be part of the problem?  Do i need to get my /hd/sda1/ out of RAID?

---

### Post by tbauer on 2011-09-27
So I was able to activate LVM after installing it.  That allowed me to mount the old Ubuntu partition.  So at minimum I am optimistic I can get my files back.

Now, I am trying to get the last hurdle ... making the old partition boot again.   1st I'll try to do an upgrade (if you recall it was at 10.10) to 11.01 from a LiveCD after getting LVM on.  See if that works (creates a new grub/mbr, etc).   I tried that earlier (w/o LVM on) and it failed probably because it couldn't write/access the old ubuntu partition.

---

### Post by tbauer on 2011-09-27
Oh well.  Upgrade to 11.01 from LiveCD still fails.  Something about APT Clone failing (same error as before).   

I'll try the Chroot using a 10.10 LiveCD next as described here:

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by tbauer on 2011-09-27
So i was able to Chroot and purge-reinstall grub per this site:

[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html)

However I still get the minimal grub command line on boot.   Perhaps the LVM isn't loading (so its pulling this minimal grub from somewhere else?).  I'll look into recovering LVM's.

---

