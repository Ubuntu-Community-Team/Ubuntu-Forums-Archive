---
title: "Windows 7 broke, then I broke it worse w/11.04 [MBR]"
date: 2011-06-09
forum: General Help
---

### Post by sanguines on 2011-06-09
Originally, my computer had Windows 7 x64 installed on the first partition of 2 on a 1 TB hard drive. Each partition is ~500GB. One day, I did a graceful takedown to rearrange my furniture, but when I booted, I ended up in grub rescue (?!). I've had Ubuntu installed previously but not in quite some time and Windows 7 had been working flawlessly for over a year. 

The second partition on my disk was blank, so I went ahead and installed Ubuntu 11.04 on it to try and salvage things. Well, after hours of Google-ing and trying this and that, I think I broke my system even more.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sdb5        86e546fc-4aed-4e22-a6b9-1577eb88c7d6   ext4       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)




```

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/dm-0: 8583 MB, 8583643136 bytes
255 heads, 63 sectors/track, 1043 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


```

/dev/sda is irrelevant and has no data on it, I believe. /dev/sdb is my primary disk.

I have data I'd like to save on the Windows 7 partition, and I don't have a Windows 7 install disk at hand. I *do* have a Windows Vista disk, but the first thing I did was try the startup recovery, without results. 

What do you recommend?

---

### Post by oldfred on 2011-06-09
You have an invalid MBR signature. I have not seen that, but you do not have any boot loaders and little if any partition table. Some BIOS put out errors if you do not have  a boot flag on a primary partition, but you do not have any primary partitions.

It also looks like you had LVM and encryption?? I do not know LVM nor encryption.

I would see if test disk tells anything.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Testdisk may find old partitions and allow you to restore them depending on what has transpired.  If data is encrypted then I do not think you have anything to recover. if not encrypted then photorec may find some files.
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)

---

### Post by sanguines on 2011-06-10
OK, so I used testdisk to resurrect the the partition table. I can now mount my Windows 7 partition and browse the data from liveCD Ubuntu, so I know we're good there. Now, though, neither of my OSes boot - the whole deal just boots into a grub prompt. 

Any ideas on how to get grub working again? I'd like it to boot to the OS-selection menu. I probably just have grub installed in the wrong spot or something but I don't know enough about what I'm doing to proceed w/o breaking it worse :)

---

### Post by oldfred on 2011-06-10
Lets see if windows boots on its own first. You can install a windows boot loader to the MBR of sda and it should then boot windows. Boot flag has to be on windows boot partition. If windows 7 it usually has two partitions, a small 100MB boot/recovery partition and the main install.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by sanguines on 2011-06-10
I completed the suggested steps, and now I am stuck at a blinking cursor. I used a guide I found to completely recreate the bootloader from the repair disk command prompt, to no effect.  I'm out of ideas again.

---

### Post by linuxinstalledfromhdd on 2011-06-10
Try this:

[http://cinderbox.net/2011/06/08/how-to-fix-grub-grub2-windows-mbr-and-lost-systems/](http://cinderbox.net/2011/06/08/how-to-fix-grub-grub2-windows-mbr-and-lost-systems/)

---

### Post by Quackers on 2011-06-10
Please re-run the boot script and post the new results in code tags.

---

### Post by sanguines on 2011-06-10
Here we go:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

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

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1     ? 1,936,269,394 3,772,285,809 1,836,016,416  4f QNX4.x 3rd part
/dev/sda2     ? 1,917,848,077 2,462,285,169   544,437,093  73 Unknown
/dev/sda3     ? 1,818,575,915 2,362,751,050   544,175,136  2b SyllableSecure
/dev/sda4     ? 2,844,524,554 2,844,579,527        54,974  61 SpeedStor

/dev/sda1 ends after the last sector of /dev/sda
/dev/sda1 overlaps with /dev/sda2
/dev/sda1 overlaps with /dev/sda3
/dev/sda1 overlaps with /dev/sda4
/dev/sda2 ends after the last sector of /dev/sda
/dev/sda2 overlaps with /dev/sda3
/dev/sda3 ends after the last sector of /dev/sda
/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *        206,848   989,491,199   989,284,352   7 NTFS / exFAT / HPFS
/dev/sdb2         989,491,200 1,953,519,615   964,028,416  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        0975AA55FB810F72                       ntfs       
/dev/sdb2        b8c59562-33b2-47be-b023-7382cabdd28c   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=========================== sdb2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos2)'
search --no-floppy --fs-uuid --set=root b8c59562-33b2-47be-b023-7382cabdd28c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos2)'
search --no-floppy --fs-uuid --set=root b8c59562-33b2-47be-b023-7382cabdd28c
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root b8c59562-33b2-47be-b023-7382cabdd28c
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=b8c59562-33b2-47be-b023-7382cabdd28c ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root b8c59562-33b2-47be-b023-7382cabdd28c
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=b8c59562-33b2-47be-b023-7382cabdd28c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root b8c59562-33b2-47be-b023-7382cabdd28c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root b8c59562-33b2-47be-b023-7382cabdd28c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=b8c59562-33b2-47be-b023-7382cabdd28c /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 823.960708618 = 884.721074176  boot/grub/core.img                             1
 823.960716248 = 884.721082368  boot/grub/grub.cfg                             1
 473.263671875 = 508.162998272  boot/initrd.img-2.6.38-8-generic               2
 823.958988190 = 884.719226880  boot/vmlinuz-2.6.38-8-generic                  1
 473.263671875 = 508.162998272  initrd.img                                     2
 823.958988190 = 884.719226880  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda3


Unknown BootLoader on sda4



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory

```

As before, /dev/sdb is the drive that matters. /dev/sda is blank.

---

### Post by Quackers on 2011-06-10
Yes, /dev/sda is a mess. Serious partition problems there. It needs formatting, if it will let you.

I suspect that what is stopping Windows from booting is the file in red. It shouldn't be there.
```
sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       [COLOR="Red"]/boot/grub/core.img[/COLOR]

```
I assume that you are booted into a live cd/usb desktop now? If not, please do so.
In Places menu you should be able to navigate to the Windows root.
There will be a folder called "boot". Within that folder there may be a file called "grub" with a file in it called core.img
Please delete that grub folder. NOT the boot folder!

Then please reboot and see if Windows boots (making sure that your bios is set to boot /dev/sdb before /dev/sda).

If Windows boots we can then install grub to the mbr of /dev/sdb from the live cd/usb desktop.

---

### Post by sanguines on 2011-06-10
> **Quackers said:**
> Yes, /dev/sda is a mess. Serious partition problems there. It needs formatting, if it will let you.

I suspect that what is stopping Windows from booting is the file in red. It shouldn't be there.
```
sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       [COLOR="Red"]/boot/grub/core.img[/COLOR]

```
I assume that you are booted into a live cd/usb desktop now? If not, please do so.
In Places menu you should be able to navigate to the Windows root.
There will be a folder called "boot". Within that folder there may be a file called "grub" with a file in it called core.img
Please delete that grub folder. NOT the boot folder!

Then please reboot and see if Windows boots (making sure that your bios is set to boot /dev/sdb before /dev/sda).

If Windows boots we can then install grub to the mbr of /dev/sdb from the live cd/usb desktop.

Yes, I'm living out of an 11.04 live CD. ;)

I've deleted the grub folder as suggested. Still, neither OS boots. I went ahead and fixed /dev/sda just to clear things up, so here's a new boot info script: 

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   488,392,064   488,392,002   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *        206,848   989,491,199   989,284,352   7 NTFS / exFAT / HPFS
/dev/sdb2         989,491,200 1,953,519,615   964,028,416  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        507DF7C4067498AA                       ntfs       New Volume
/dev/sdb1        0975AA55FB810F72                       ntfs       
/dev/sdb2        b8c59562-33b2-47be-b023-7382cabdd28c   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/0975AA55FB810F72  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2        /media/b8c59562-33b2-47be-b023-7382cabdd28c ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos2)'
search --no-floppy --fs-uuid --set=root b8c59562-33b2-47be-b023-7382cabdd28c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos2)'
search --no-floppy --fs-uuid --set=root b8c59562-33b2-47be-b023-7382cabdd28c
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root b8c59562-33b2-47be-b023-7382cabdd28c
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=b8c59562-33b2-47be-b023-7382cabdd28c ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root b8c59562-33b2-47be-b023-7382cabdd28c
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=b8c59562-33b2-47be-b023-7382cabdd28c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root b8c59562-33b2-47be-b023-7382cabdd28c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root b8c59562-33b2-47be-b023-7382cabdd28c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=b8c59562-33b2-47be-b023-7382cabdd28c /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 823.960708618 = 884.721074176  boot/grub/core.img                             1
 823.960716248 = 884.721082368  boot/grub/grub.cfg                             1
 473.263671875 = 508.162998272  boot/initrd.img-2.6.38-8-generic               2
 823.958988190 = 884.719226880  boot/vmlinuz-2.6.38-8-generic                  1
 473.263671875 = 508.162998272  initrd.img                                     2
 823.958988190 = 884.719226880  vmlinuz                                        1


```

---

### Post by Quackers on 2011-06-10
Well /dev/sda looks a lot better :-)

Is the 1TB disc (/dev/sdb) set as the first HDD to boot in your bios?

---

### Post by sanguines on 2011-06-10
Yes it is, and my BIOS also has the option to manually select which boot device to use. No matter what I do: blinking cursor of doom.

---

### Post by Quackers on 2011-06-10
Well we can install grub and that should get Ubuntu booting. I have reservations on whether it will boot Windows though. You may need a Windows repair/installation disc to fix it. (You may need to run a chkdsk on it).

Please open a terminal in the live desktop.
Then copy/paste the following commands in one at a time, pressing enter after each line.
```
sudo mount /dev/sdb2 /mnt  
sudo grub-install --root-directory=/mnt /dev/sdb
``` Which should report finished. No errors.
If so, reboot and Ubuntu should boot directly.
Then open a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is run to see that the Windows Loader is recognised. If it is reboot and from your new grub menu choose Windows and see if it boots.

---

### Post by sanguines on 2011-06-10
> **Quackers said:**
> Well we can install grub and that should get Ubuntu booting. I have reservations on whether it will boot Windows though. You may need a Windows repair/installation disc to fix it. (You may need to run a chkdsk on it).

Please open a terminal in the live desktop.
Then copy/paste the following commands in one at a time, pressing enter after each line.
```
sudo mount /dev/sdb2 /mnt  
sudo grub-install --root-directory=/mnt /dev/sdb
``` Which should report finished. No errors.
If so, reboot and Ubuntu should boot directly.
Then open a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is run to see that the Windows Loader is recognised. If it is reboot and from your new grub menu choose Windows and see if it boots.

I'll give this a go now. For what it's worth, I have a Windows repair disk and I ran chkdsk earlier today (took 3+ hours, but I waited it out) with no errors reported.

Edit: Ubuntu boots again. Progress!

---

### Post by Quackers on 2011-06-10
Progress is good :-)

---

### Post by sanguines on 2011-06-10
OK, grub-update found the Windows bootloader and boots to the menu, but choosing Windows still results in a blinking cursor of doom. What can I do (have repair disk) to fix Windows w/o destroying grub and restarting this whole vicious cycle?

---

### Post by Quackers on 2011-06-10
If you boot from the Windows repair disc and choose the recovery console you can choose the command prompt option (ignore the automatic startup repair) then run this command (note the space between boorec.exe and /fixmbr) ```
bootrec.exe /fixmbr
``` If no error is reported reboot and Windows should boot directly. We hope!

Obviously this will over-write grub but that's easily fixed by running the 2 commands you ran earlier from the live cd.
The important thing is to get Windows booting again at this stage.

---

### Post by sanguines on 2011-06-10
> **Quackers said:**
> If you boot from the Windows repair disc and choose the recovery console you can choose the command prompt option (ignore the automatic startup repair) then run this command (note the space between boorec.exe and /fixmbr) ```
bootrec.exe /fixmbr
``` If no error is reported reboot and Windows should boot directly. We hope!

Obviously this will over-write grub but that's easily fixed by running the 2 commands you ran earlier from the live cd.
The important thing is to get Windows booting again at this stage.

No luck - back to the live cd for me.

---

### Post by Quackers on 2011-06-10
What happened? Just the flashing cursor?
Try running the automatic startup repair in the Windows repair cd. It may need to be run up to 3 times, as it can only repair one thing at a time.

---

### Post by sanguines on 2011-06-10
> **Quackers said:**
> What happened? Just the flashing cursor?
Try running the automatic startup repair in the Windows repair cd. It may need to be run up to 3 times, as it can only repair one thing at a time.

Yes indeed, flashing cursor.

I ran the auto startup repair 3 times, to no avail - flashing cursor again. Here's the log: 

```
Startup Repair diagnosis and repair log

---------------------------

Last successful boot time: ?6/?6/?2011 9:27:46 PM (GMT)

Number of repair attempts: 3



Session details

---------------------------

System Disk = \Device\Harddisk1

Windows directory = D:\Windows

AutoChk Run = 0

Number of root causes = 1



Test Performed: 

---------------------------

Name: Check for updates

Result: Completed successfully. Error code =  0x0

Time taken = 0 ms



Test Performed: 

---------------------------

Name: System disk test

Result: Completed successfully. Error code =  0x0

Time taken = 0 ms



Test Performed: 

---------------------------

Name: Disk failure diagnosis

Result: Completed successfully. Error code =  0x0

Time taken = 203 ms



Test Performed: 

---------------------------

Name: Disk metadata test

Result: Completed successfully. Error code =  0x0

Time taken = 16 ms



Test Performed: 

---------------------------

Name: Target OS test

Result: Completed successfully. Error code =  0x0

Time taken = 296 ms



Test Performed: 

---------------------------

Name: Volume content check

Result: Completed successfully. Error code =  0x0

Time taken = 0 ms



Test Performed: 

---------------------------

Name: Boot manager diagnosis

Result: Completed successfully. Error code =  0x0

Time taken = 0 ms



Test Performed: 

---------------------------

Name: System boot log diagnosis

Result: Completed successfully. Error code =  0x0

Time taken = 16 ms



Test Performed: 

---------------------------

Name: Event log diagnosis

Result: Completed successfully. Error code =  0x0

Time taken = 0 ms



Test Performed: 

---------------------------

Name: Internal state check

Result: Completed successfully. Error code =  0x0

Time taken = 0 ms



Test Performed: 

---------------------------

Name: Boot status test

Result: Completed successfully. Error code =  0x0

Time taken = 0 ms



Root cause found: 

---------------------------

Boot status indicates that the OS booted successfully.



---------------------------

---------------------------

Session details

---------------------------

System Disk = \Device\Harddisk1

Windows directory = D:\Windows

AutoChk Run = 0

Number of root causes = 1



Test Performed: 

---------------------------

Name: Check for updates

Result: Completed successfully. Error code =  0x0

Time taken = 0 ms



Test Performed: 

---------------------------

Name: System disk test

Result: Completed successfully. Error code =  0x0

Time taken = 0 ms



Test Performed: 

---------------------------

Name: Disk failure diagnosis

Result: Completed successfully. Error code =  0x0

Time taken = 203 ms



Test Performed: 

---------------------------

Name: Disk metadata test

Result: Completed successfully. Error code =  0x0

Time taken = 31 ms



Test Performed: 

---------------------------

Name: Target OS test

Result: Completed successfully. Error code =  0x0

Time taken = 312 ms



Test Performed: 

---------------------------

Name: Volume content check

Result: Completed successfully. Error code =  0x0

Time taken = 125 ms



Test Performed: 

---------------------------

Name: Boot manager diagnosis

Result: Completed successfully. Error code =  0x0

Time taken = 47 ms



Test Performed: 

---------------------------

Name: System boot log diagnosis

Result: Completed successfully. Error code =  0x0

Time taken = 0 ms



Test Performed: 

---------------------------

Name: Event log diagnosis

Result: Completed successfully. Error code =  0x0

Time taken = 78 ms



Test Performed: 

---------------------------

Name: Internal state check

Result: Completed successfully. Error code =  0x0

Time taken = 31 ms



Test Performed: 

---------------------------

Name: Boot status test

Result: Completed successfully. Error code =  0x0

Time taken = 0 ms



Root cause found: 

---------------------------

Boot status indicates that the OS booted successfully.



---------------------------

---------------------------

Session details

---------------------------

System Disk = \Device\Harddisk1

Windows directory = D:\Windows

AutoChk Run = 0

Number of root causes = 1



Test Performed: 

---------------------------

Name: Check for updates

Result: Completed successfully. Error code =  0x0

Time taken = 0 ms



Test Performed: 

---------------------------

Name: System disk test

Result: Completed successfully. Error code =  0x0

Time taken = 16 ms



Test Performed: 

---------------------------

Name: Disk failure diagnosis

Result: Completed successfully. Error code =  0x0

Time taken = 187 ms



Test Performed: 

---------------------------

Name: Disk metadata test

Result: Completed successfully. Error code =  0x0

Time taken = 31 ms



Test Performed: 

---------------------------

Name: Target OS test

Result: Completed successfully. Error code =  0x0

Time taken = 312 ms



Test Performed: 

---------------------------

Name: Volume content check

Result: Completed successfully. Error code =  0x0

Time taken = 125 ms



Test Performed: 

---------------------------

Name: Boot manager diagnosis

Result: Completed successfully. Error code =  0x0

Time taken = 47 ms



Test Performed: 

---------------------------

Name: System boot log diagnosis

Result: Completed successfully. Error code =  0x0

Time taken = 0 ms



Test Performed: 

---------------------------

Name: Event log diagnosis

Result: Completed successfully. Error code =  0x0

Time taken = 93 ms



Test Performed: 

---------------------------

Name: Internal state check

Result: Completed successfully. Error code =  0x0

Time taken = 31 ms



Test Performed: 

---------------------------

Name: Boot status test

Result: Completed successfully. Error code =  0x0

Time taken = 0 ms



Root cause found: 

---------------------------

Boot status indicates that the OS booted successfully.



---------------------------

---------------------------
```

---

### Post by Quackers on 2011-06-10
Hmm, it's finding 1 root cause but it states that the system thinks it booted ok.
This looks odd though
```
Session details

---------------------------

System Disk = \Device\Harddisk1

Windows directory = D:\Windows

AutoChk Run = 0

Number of root causes = 1
``` I would have expected that to report 
Windows Directory = C:\Windows - not D:\Windows

---

### Post by sanguines on 2011-06-10
> **Quackers said:**
> Hmm, it's finding 1 root cause but it states that the system thinks it booted ok.
This looks odd though
```
Session details

---------------------------

System Disk = \Device\Harddisk1

Windows directory = D:\Windows

AutoChk Run = 0

Number of root causes = 1
``` I would have expected that to report 
Windows Directory = C:\Windows - not D:\Windows

I believe the 250GB drive AKA /dev/sda snatched up C: as its drive letter. I'm going to disconnect it and see what happens.

---

### Post by Quackers on 2011-06-10
Another question.
Is your repair cd the same architecture as your installation (ie both 32 bit or both 64 bit)?

---

### Post by sanguines on 2011-06-11
> **Quackers said:**
> Another question.
Is your repair cd the same architecture as your installation (ie both 32 bit or both 64 bit)?

Yes, both are x64.

Anyways, I disconnected the spare drive and found that my guess was correct. As soon as I disconnected it, the 1TB drive returned to being C:. Windows (nor Ubuntu) does not boot. I also tried doing bootrec /fixmbr and bootrec /fixboot again, to no avail.

---

### Post by Quackers on 2011-06-11
Try bootrec.exe /rebuildbcd

---

### Post by sanguines on 2011-06-11
> **Quackers said:**
> Try bootrec.exe /rebuildbcd

No change. The recovery tool detects the Windows 7 install, but doesn't find anything (or is it anything new?) when I run the /rebuildbcd command.

---

### Post by Quackers on 2011-06-11
Did the automatic startup repair find the installation previously?

---

### Post by sanguines on 2011-06-11
Yes. That's the log I posted a few posts back.

---

### Post by Quackers on 2011-06-11
I'm out of ideas :-(
Maybe somebody else can think of something.
In the meantime you can either get Ubuntu booting again or boot from the live cd and backup everything that you need from Windows, in case you need to re-install it.

---

### Post by oldfred on 2011-06-11
I know with XP when you change drive order you have to re-edit boot.ini as drive 1 then becomes drive 0. The same should happen with Vista/7 but inside the BCD. I would have thought the rebuildBCD would have solved it.

But you may have to go thru all the command again in order to reset it to drive 0?? You should not need the chkdsk if it ran without error before:

BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by Quackers on 2011-06-11
I hope your luck turns good with oldfred's help :-)
It's nearly 6am here, so it's time for my bo-bo's  :-)

---

