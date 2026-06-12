---
title: "Fresh Windows install removed GRUB"
date: 2012-05-16
forum: General Help
---

### Post by Afiorentino on 2012-05-16
I've been in the process of upgrading my system for a little while now. After doing a fresh install of Windows 7 (from Windows XP), I could no longer access the drive Kubuntu is on. I even went as far to remove the drive from my computer to try and mount it from my laptop (also Kubuntu) using an external enclosure.

Any ideas? I'd really like to avoid doing a fresh install of Kubuntu if I can help it.

Thanks in advance.

---

### Post by wilee-nilee on 2012-05-16
So lets see the whole setup run these commands from a live kubuntu cd look in  home for a results.txt, open a reply click on the # in the reply panel to generate code tags  and copy and paste all the text in between.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
``` ```
chmod a+x bootinfoscript
``````
sudo bash bootinfoscript
```I assume kubuntu is sudo if ksudo then adjust the commands accordingly, never used kubuntu.

Have you tried just booting the drive kubuntu is on?

---

### Post by lolpenguin on 2012-05-17
You installed Windows. Windows is very selfish. Windows really likes being first on the drive. Windows will not go anywhere without NTFS. Windows does not read ext filesystems. Windows will always overwrite the MBR.

That last point. Windows will always overwrite the MBR.

This is easily solved, though quite annoying. Boot into a live desktop (presumably your install CD) and run:
```
grub-install /dev/sdx
```
where sdx is your primary hard drive. This is usually sda. Don't put in the partition number.

---

### Post by satish_j on 2012-05-17
> **lolpenguin said:**
> 
```
grub-install /dev/sdx
```
where sdx is your primary hard drive. This is usually sda. Don't put in the partition number.

For me,above command did not worked..Foll worked..
```

sudo mount /dev/sdXY /mnt
grub-install --root-directory=/mnt /dev/sdX

```
where,/dev/sdXY is your Ubuntu partition and /dev/sdX is the drive(without partition number)

---

### Post by wilee-nilee on 2012-05-17
> **lolpenguin said:**
> You installed Windows. Windows is very selfish. Windows really likes being first on the drive. Windows will not go anywhere without NTFS. Windows does not read ext filesystems. Windows will always overwrite the MBR.

That last point. Windows will always overwrite the MBR.

This is easily solved, though quite annoying. Boot into a live desktop (presumably your install CD) and run:
```
grub-install /dev/sdx
```where sdx is your primary hard drive. This is usually sda. Don't put in the partition number.

From a cd will do nothing, you need to chroot to use this command. :)

---

### Post by Afiorentino on 2012-05-18
Booted from the live cd:

```
sudo grub-install /dev/sdb
```results in

```
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
``````
sudo mount /dev/sdb1 /mnt
```results with

```
mount: you must specify the filesystem type
```I didn't think you needed to specify for ext file systems (only ntfs and FAT)?

Wilee, the live cd isn't agreeing with my wireless adapter, but I think I can get you that boot information from something I tried earlier. 

I've already tried to boot from my ubuntu drive, but my system just reboots.

---

### Post by Afiorentino on 2012-05-18
```
                 Boot Info Script 0.60-git      [23 Feb 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:  Syslinux looks at sector 3568098 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   625,142,447   625,142,447  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       206,847       204,800 EFI System partition
/dev/sda2         206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         468,992   625,141,759   624,672,768 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1         378,635,985   390,716,864    12,080,880   5 Extended
/dev/sdb5         378,636,048   390,716,864    12,080,817  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   117,210,239   117,210,177   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0E3B-BBC9                              vfat       
/dev/sda3        EE244C61244C2EC1                       ntfs       
/dev/sdb5        fb37be59-8564-486b-93d2-b63ee09604ba   swap       
/dev/sdc1        16E8-0F4C                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /media/disk              squashfs   (ro,nosuid,nodev,uhelper=udisks)
/dev/sr0         /live/image              iso9660    (ro,noatime)


=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Start Kubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/kubuntu.seed boot=casper maybe-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
File descriptor 11 (pipe:[13125]) leaked on lvscan invocation. Parent PID 14497: bash
File descriptor 12 (pipe:[13125]) leaked on lvscan invocation. Parent PID 14497: bash
  No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
**************** log of boot-repair 2012-04-25__16h03 ****************
boot-repair version : 3.16-0ppa10~lucid
boot-sav version : 3.17-0ppa18~lucid
/usr/share/boot-sav/gui-update.sh: line 31: hash: glade2script: not found
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
internet: no-internet
File descriptor 11 (pipe:[13125]) leaked on lvs invocation. Parent PID 11694: /bin/sh
File descriptor 12 (pipe:[13125]) leaked on lvs invocation. Parent PID 11694: /bin/sh
No volume groups found
LIVESESSION is : yes (Debian GNU/Linux 6.0.3 (squeeze) , squeeze , Debian , x86_64  )
BYTES_BEFORE_PART[1] (sda) = 2048 sectors * 512 bytes = 1048576 bytes.
BYTES_BEFORE_PART[2] (sdc) = 63 sectors * 512 bytes = 32256 bytes.

OSPROBER:


BLKID:
/dev/sdb5: UUID="fb37be59-8564-486b-93d2-b63ee09604ba" TYPE="swap"
/dev/sda1: UUID="0E3B-BBC9" TYPE="vfat"
/dev/sda3: UUID="EE244C61244C2EC1" TYPE="ntfs"
/dev/loop0: TYPE="squashfs"
/dev/sdc1: UUID="16E8-0F4C" TYPE="vfat"


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

LIST_GPTPART[1] is 1 (sda1 , sdc)
ReadEFI: /dev/sda , N 128 , 0 ,  , PRStart 1024 , PRSize 128
part /dev/sda1 is BISEFI
part /dev/sda3 is notBISEFI
TABLE_TYPE of sda is EFI
TABLE_TYPE of sdc is MSDos
sda1 : sda, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda1, no-os, gpt, BISEFI, no-fstab.
sda3 : sda, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda3, no-os, no-gpt, notBISEFI, no-fstab.
sdc1 : sdc, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, with boot, /mnt/boot-sav/sdc1, no-os, no-gpt, notEFItable, no-fstab.

PARTED:

Model: ATA ST3320620AS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                          Flags
1      1049kB  106MB  105MB  fat32        EFI system partition          boot
2      106MB   240MB  134MB               Microsoft reserved partition  msftres
3      240MB   320GB  320GB  ntfs         Basic data partition


Model: ATA MAXTOR STM320082 (scsi)
Disk /dev/sdb: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End    Size    Type      File system     Flags
1      194GB  200GB  6185MB  extended
5      194GB  200GB  6185MB  logical   linux-swap(v1)


Model: WDC WD60 0VE-00HDT0 (scsi)
Disk /dev/sdc: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  60.0GB  60.0GB  primary  fat32        boot, lba



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


MOUNT:
aufs on / type aufs (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sr0 on /live/image type iso9660 (ro,noatime)
tmpfs on /live/cow type tmpfs (rw,noatime,mode=755)
tmpfs on /live type tmpfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/loop0 on /media/disk type squashfs (ro,nosuid,nodev,uhelper=udisks)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdc1 on /mnt/boot-sav/sdc1 type vfat (rw)


/sys/block/sda:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 sdb5 size slaves stat subsystem trace uevent
/sys/block/sdc:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency disk dvd dvdrw fd full fuse hidraw0 hidraw1 hpet initctl input kmsg log MAKEDEV mcelog md mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sda2 sda3 sdb sdb1 sdb5 sdc sdc1 sg0 sg1 sg2 sg3 shm snapshot snd sndstat sr0 stderr stdin stdout urandom usb vga_arbiter xconsole zero

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


DF:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    7.9G   12M  7.9G   1% /
tmpfs        tmpfs    7.9G     0  7.9G   0% /lib/init/rw
udev         tmpfs    7.9G  240K  7.9G   1% /dev
tmpfs        tmpfs    7.9G     0  7.9G   0% /dev/shm
/dev/sr0   iso9660    339M  339M     0 100% /live/image
tmpfs        tmpfs    7.9G   12M  7.9G   1% /live/cow
tmpfs        tmpfs    7.9G     0  7.9G   0% /live
tmpfs        tmpfs    7.9G  1.3M  7.9G   1% /tmp
/dev/loop0
squashfs    313M  313M     0 100% /media/disk
/dev/sda1     vfat     96M   18M   79M  19% /mnt/boot-sav/sda1
/dev/sda3  fuseblk    298G  253G   46G  85% /mnt/boot-sav/sda3
/dev/sdc1     vfat     56G  1.7G   55G   4% /mnt/boot-sav/sdc1

FDISK:

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00016a79

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1       378635985   390716864     6040440    5  Extended
/dev/sdb5       378636048   390716864     6040408+  82  Linux swap / Solaris

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xba6fba6f

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   625142447   312571223+  ee  GPT

Disk /dev/sdc: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x28f12a69

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   117210239    58605088+   c  W95 FAT32 (LBA)



************************Before mainwindow
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, restore, REINSTALL_POSSIBLE no PURGE_POSSIBLE
UNHIDEBOOT_ACTION yes (10s), noflag (sdc1)
PART_TO_REINSTALL_GRUB , PART_TO_REINSTALL_GRUB_PURGE , FORCE_GRUB  () REMOVABLEDISK
USE_SEPARATEBOOTPART  ()  ()
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) ( )
internet: no-internet

************************Actions
FSCK_ACTION yes PASTEBIN_ACTION yes
customrepair, restore, REINSTALL_POSSIBLE no PURGE_POSSIBLE
UNHIDEBOOT_ACTION yes (10s), noflag (sdc1)
PART_TO_REINSTALL_GRUB , PART_TO_REINSTALL_GRUB_PURGE , FORCE_GRUB  () REMOVABLEDISK
USE_SEPARATEBOOTPART  ()  ()
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sdc (mbr) (sdc 3)
Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

fsck from util-linux-ng 2.17.2

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

fsck from util-linux-ng 2.17.2

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

fsck from util-linux-ng 2.17.2
Will restore the MBR_TO_RESTORE : sdc (mbr) into sdc
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdc
0+1 records in
0+1 records out
bootflag_action sdc1 (=sdc1)
parted /dev/sdc set 2 boot off

                                                                          
Error: Partition doesn't exist.
parted /dev/sdc set 3 boot off

                                                                          
Error: Partition doesn't exist.
parted /dev/sdc set 4 boot off

                                                                          
Error: Partition doesn't exist.
parted /dev/sdc set 1 boot on

                                                                          
Information: You may need to update /etc/fstab.

internet: no-internet
internet: no-internet

```

---

### Post by Afiorentino on 2012-05-19
Just a thought: ignore the sdc drive from the boot data-- it's an external hard drive I left plugged in which I used as a live version of linux at one point.

---

### Post by YannBuntu on 2012-05-19
Hello
you have 2 problems:
1) your Kubuntu system partition has disappeared
2) your Windows boot partition has a "mount: unknown filesystem type ''" error

If i were you, i would:
1) backup my documents on an external disk (or DVDs)
2) Via a Windows disk, repair Windows boot files (or reinstall Windows)
3) reinstall Ubuntu

but wait a little, someone may have better ideas.

---

### Post by Afiorentino on 2012-05-29
Is there a way to force mount my kubuntu partition using another linux system so that I can back up my files and just do a fresh install?

---

### Post by YannBuntu on 2012-05-30
Maybe TestDisk will help you recover your documents.

---

### Post by Afiorentino on 2012-06-09
I was able to recover all of my documents from my linux partition using test disk.

[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

Thank you everyone for you help

---

