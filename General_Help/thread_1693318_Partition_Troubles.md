---
title: "Partition Troubles"
date: 2011-02-22
forum: General Help
---

### Post by nosiphoratu on 2011-02-22
Sorry if this is the wrong forum, this seemed to be the closest thing. 

So in the process of a grow/move operation of my linux Home partition using gparted I stupidly hit restart because I thought it had finished. Ubuntu live then restarted the computer. Killing that partition (or so I thought). I was able to continue to use windows 7 (i was running a dual boot) but in the process of trying to restore my MBR and grub various times, I have lost access to my windows partition but regained access to the ext4 linux partition. However the odd thing is that in gparted it shows my entire hard drive as unallocated, and I am not able to get windows up and running again. Testdisk says that the (NTFS windows 7 partition) file system may be damaged, however I was able to access all the files only this morning before I tried to reset grub. 

I have important files on both the NTFS and the ext4. Any ideas? :confused:

---

### Post by oldfred on 2011-02-22
Run this, it is more for boot issues, but may highlight partition problems, just by saying which ones it cannot parse.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.


Have you run chkdsk on the NTFS partition and e2fsck on any Linux partitions?

---

### Post by nosiphoratu on 2011-02-22
I should also mention that just now after running a thourough check using testdisk I was able to access my windows partition through it. The only problem is I do not have a hard drive big enough to copy everything to.And it would be a lot easier if I could copy the files from within an OS, and recover my windows 7 and ubuntu installs rather than starting fresh.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   554,322,823   554,322,761   7 HPFS/NTFS
/dev/sda2         948,314,112 1,909,569,535   961,255,424  83 Linux
/dev/sda3       1,909,569,536 1,950,529,535    40,960,000  83 Linux
/dev/sda4       1,950,531,975 1,953,536,129     3,004,155   f W95 Ext d (LBA)
/dev/sda5       1,950,532,038 1,953,520,045     2,988,008  82 Linux swap / Solaris

/dev/sda4 ends after the last sector of /dev/sda

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        0c6ecc58-0961-42b4-bb2f-4b32305a205e   ext4                                     
/dev/sda3        7d11d5eb-3294-4506-8e49-392d7a106279   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5                                               swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb         0CE6-4843                              vfat       PENDRIVE                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr2         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sr0         /media/HIREN'SBOOTCD9.5  iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda2        /media/0c6ecc58-0961-42b4-bb2f-4b32305a205e ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7d11d5eb-3294-4506-8e49-392d7a106279
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7d11d5eb-3294-4506-8e49-392d7a106279
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7d11d5eb-3294-4506-8e49-392d7a106279
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=7d11d5eb-3294-4506-8e49-392d7a106279 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7d11d5eb-3294-4506-8e49-392d7a106279
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=7d11d5eb-3294-4506-8e49-392d7a106279 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7d11d5eb-3294-4506-8e49-392d7a106279
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7d11d5eb-3294-4506-8e49-392d7a106279 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7d11d5eb-3294-4506-8e49-392d7a106279
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=7d11d5eb-3294-4506-8e49-392d7a106279 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7d11d5eb-3294-4506-8e49-392d7a106279
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7d11d5eb-3294-4506-8e49-392d7a106279
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 4c94d82894d81674
    chainloader +1
}
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=7d11d5eb-3294-4506-8e49-392d7a106279 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=0c6ecc58-0961-42b4-bb2f-4b32305a205e /home           ext4    defaults        0       2
/dev/sda5       none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 979.9GB: boot/grub/core.img
 991.4GB: boot/grub/grub.cfg
 980.5GB: boot/initrd.img-2.6.35-22-generic
 980.5GB: boot/initrd.img-2.6.35-25-generic
 980.2GB: boot/vmlinuz-2.6.35-22-generic
 980.3GB: boot/vmlinuz-2.6.35-25-generic
 980.5GB: initrd.img
 980.5GB: initrd.img.old
 980.3GB: vmlinuz
 980.2GB: vmlinuz.old

=========================== sdb/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Install Ubuntu Studio" {
    set gfxpayload=keep
    linux    /install/vmlinuz  file=/cdrom/preseed/ubuntustudio.seed quiet --
    initrd    /install/initrd.gz
}
menuentry "Install in expert mode" {
    set gfxpayload=keep
    linux    /install/vmlinuz  file=/cdrom/preseed/ubuntustudio.seed priority=low --
    initrd    /install/initrd.gz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /install/vmlinuz  MENU=/bin/cdrom-checker-menu quiet --
    initrd    /install/initrd.gz
}
menuentry "Rescue a broken system" {
    set gfxpayload=keep
    linux    /install/vmlinuz  rescue/enable=true --
    initrd    /install/initrd.gz
}

==================== sdb: Location of files loaded by Grub: ====================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 20 06 11  |.X.SYSLINUX.. ..|
00000010  02 00 00 00 00 f8 00 00  11 00 04 00 00 00 00 00  |................|
00000020  e0 df 77 00 7d 07 00 00  00 00 00 00 02 00 00 00  |..w.}...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 43 48 e6 0c 4e  4f 20 4e 41 4d 45 20 20  |..)CH..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 00 20 60 00  66 ba 00 00 00 00 bb 00  |}.f.. `.f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by jkgoose937 on 2011-02-23
My biggest "beef" with testdisk, it's great at recovering NTFS or other non linux partitions that it lacks the infrastructure to restore my Reiser partition properly . It's like it would rather restore my ntfs partition first then mess up my linux partition so all my files are now corrupt.  I used the photorec utility to hopefully get all my pix but i don't know if it got them all. now granted i should have backed up my pix frist on disk but my dvd burner had a hardware failure, plus k3b does have a span disk feature yet. i lost A LOT of pix because it restored the ntfs partition argh.

---

### Post by oldfred on 2011-02-23
Did you run testdisk? It seems to have a nasty little bug that does this.
/dev/sda4 ends after the last sector of /dev/sda

Partition table errors cause many programs not to work correctly as they rely on the partition table.

Do this first just in case and store elsewhere.
Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt

this occasionally fixes issues and is worth trying:
you do the following :
fdisk /dev/sda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit

If partitions are reordered you may have to reinstall grub or edit fstab.

Fix overlaping partition error srs5694
[http://ubuntuforums.org/showthread.php?t=1667614](http://ubuntuforums.org/showthread.php?t=1667614)
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

Once partition table is corrected, I would then try chkdsk on sda1. Some of the tools boot script uses saw the sda1 partition as NTFS and others could not see it at all. Not sure if just related to partition error or not.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by nosiphoratu on 2011-02-23
I think I'm close. I edited the parts file and rewrote it to the system, however after running fdisk again it seems that sda4 (my extended partition) is still out of order. The commands I ran were sudo sfdisk -d /dev/sda > parts.txt and sudo sfdisk - -force  -d /dev/sda < parts.txt. After I edited the parts file.
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe959fe0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   554322823   277161380+   7  HPFS/NTFS
/dev/sda2       948314112  1909569535   480627712   83  Linux
/dev/sda3      1909569536  1950529535    20480000   83  Linux
/dev/sda4      1950531975  1953536129     1502077+   f  W95 Ext'd (LBA)
/dev/sda5      1950532038  1953520045     1494004   82  Linux swap / Solaris
```

Here is my modified parts file.
```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=554322761, Id= 7, bootable
/dev/sda2 : start=948314112, size=961255424, Id=83
/dev/sda3 : start=1909569536, size= 40960000, Id=83
/dev/sda4 : start=1950531975, size=  2993193, Id= f
/dev/sda5 : start=1950532038, size=  2988008, Id=82
```

---

### Post by oldfred on 2011-02-23
If you are adding the sda4 from sfdisk, I do not know how it gets the number it does.

>>> 1950531975 + 2993193
1953525168

Which is your drive size:
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168

I have seen some posts about subtracting 1 in some cases and having 63 sectors between partititons, but I do not know this at all.

Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

### Post by srs5694 on 2011-02-23
You need to reduce the size of /dev/sda4 by 10962 sectors -- that is, to 2982231 sectors, if I did the arithmetic correctly. (Note that you could reduce it by significantly more than this and it would work, too -- just be sure not to reduce it so much that it's smaller than your swap partition.)

More generally, look at the numbers (cut-and-paste them into a text editor and add commas for legibility, if you like). Check that each partition ends before the next one begins (adjusting for out-of-order partitions, if necessary, and taking into account the fact that logical partitions must reside entirely within the extended partition). Also check that no partition ends after the last sector on the disk. That last point is the only problem I see in your current fdisk output.

Another approach in your situation is to delete both /dev/sda5 and /dev/sda4. You'll then need to create a new swap partition, either by using fdisk and mkswap or by using a libparted-based tool such as GParted. This will require you to adjust your swap partition's entry in /etc/fstab or use the -U option to mkswap to match the new swap space's UUID to whatever the current one's is.

---

