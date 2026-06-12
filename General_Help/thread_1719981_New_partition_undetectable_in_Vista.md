---
title: "New partition undetectable in Vista"
date: 2011-04-02
forum: General Help
---

### Post by Teegoo on 2011-04-02
Hey, I'm completely new to Ubuntu, but installation was pretty straightforward. I created a new 18gb partition after selecting the "install alongside existing OS" option, and after it was done installing, I rebooted. Upon restarting, vista did one of its "disk checks", and then started normally. However, the new partition didn't show up. I booted again from my installation USB, and the file system showed up fine, and inside it were the Ubuntu system files, including a "home" folder with the user account I created when I installed it. However, I simply have no idea how to boot Ubuntu from the hard disk instead of vista. I realize that it's probably a silly question, and something has probably just blown over my head, but I would really appreciate the help, as I haven't found anything on the subject in any guide.

By the way, in case it helps, I installed the latest version, on the same hard drive as my Vista (sp2, I believe), in the hopes of keeping Vista as my default OS.

EDIT: after reading up on it, I think it might be a problem with GRUB... I've heard that it's supposed to load before any other OS, and in my case, it's obviously not.

---

### Post by lithopsian on 2011-04-02
Yes, you shouldn't get the Windows boot.  You should get Grub and the choice to boot to Ubuntu or Windows (plus some other stuff).  If not, boot from your CD and install Grub.

Your new partition most likely will not be visible to Windows unless you deliberately put it on a non-standard file system.  Windows can be made to read Linux ext-type file systems but overall not recommended.  Shared partitions would normally be made NTFS or even FAT.

---

### Post by Rubi1200 on 2011-04-02
Hi,

please do the following so we can get an overview of the current state of your setup:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Teegoo on 2011-04-02
Okay, here's the contents of the file that generated:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 463697336 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 8192.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    20,561,919    20,480,000   7 HPFS/NTFS
/dev/sda3    *     20,561,920   445,804,288   425,242,369   7 HPFS/NTFS
/dev/sda4         445,804,542   488,394,751    42,590,210   f W95 Ext d (LBA)
/dev/sda5         483,155,968   488,394,751     5,238,784  dd Dell Media Direct
/dev/sda6         445,804,544   481,505,279    35,700,736  83 Linux
/dev/sda7         481,507,328   483,153,919     1,646,592  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,192     7,744,511     7,736,320   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D7-0615                              vfat       DellUtility                   
/dev/sda2        AAB6D921B6D8EEB7                       ntfs       RECOVERY                      
/dev/sda3        2C6EDB496EDB0B0A                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        72CA-0838                              vfat       MEDIADIRECT                   
/dev/sda6        8cfc5c1b-130e-4a53-ac60-58b8e083b19a   ext4                                     
/dev/sda7        ced3dd1d-980a-49b9-9fd9-9df0dae25d60   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        CD97-4037                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda5/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 8cfc5c1b-130e-4a53-ac60-58b8e083b19a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 8cfc5c1b-130e-4a53-ac60-58b8e083b19a
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 8cfc5c1b-130e-4a53-ac60-58b8e083b19a
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=8cfc5c1b-130e-4a53-ac60-58b8e083b19a ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 8cfc5c1b-130e-4a53-ac60-58b8e083b19a
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=8cfc5c1b-130e-4a53-ac60-58b8e083b19a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 8cfc5c1b-130e-4a53-ac60-58b8e083b19a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 8cfc5c1b-130e-4a53-ac60-58b8e083b19a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 2c6edb496edb0b0a
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 72ca-0838
	drivemap -s (hd0) ${root}
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=8cfc5c1b-130e-4a53-ac60-58b8e083b19a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=ced3dd1d-980a-49b9-9fd9-9df0dae25d60 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 237.4GB: boot/grub/core.img
 230.5GB: boot/grub/grub.cfg
 232.9GB: boot/initrd.img-2.6.35-22-generic
 237.4GB: boot/vmlinuz-2.6.35-22-generic
 232.9GB: initrd.img
 237.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  bb aa b1 bb ab b1 bc ab  b2 bc ac b3 bd ad b3 be  |................|
00000010  ae b4 bf af b5 c1 b1 b7  c3 b2 b8 c4 b2 b8 c4 b2  |................|
00000020  b8 c5 b3 b8 c6 b4 b9 c8  b5 ba c9 b5 bc ca b5 bf  |................|
00000030  cd b6 c0 ce b7 c1 cf b8  c2 d0 ba c3 d1 bb c3 d2  |................|
00000040  bc c4 d2 be c5 d3 bf c7  d5 c1 c8 d6 c2 c8 d7 c3  |................|
00000050  c9 d8 c4 ca d9 c5 ca d9  c6 ca d9 c6 cc da c6 cf  |................|
00000060  da c7 d1 db ca d2 de cc  d3 e0 ce d4 e1 d0 d5 e2  |................|
00000070  d1 d4 e2 d2 d5 e4 d4 d7  e6 d6 d9 e8 d6 db ea d7  |................|
00000080  dc eb d7 dc eb d6 dc ec  d4 db ec d4 dd ec d4 e1  |................|
00000090  ed d6 e3 ef d7 e5 f0 d8  e5 f2 d8 e5 f2 d9 e6 f3  |................|
000000a0  da e7 f5 db e8 f6 dc e8  f6 dc e9 f7 dd e9 f9 dd  |................|
000000b0  ea fa de ea fa de eb fb  df eb fb e0 ec fb e2 ec  |................|
000000c0  fb e3 ed fb e3 ee fc e3  ee fc e3 ef fd e3 ef fd  |................|
000000d0  e4 f0 fd e4 f0 fd e5 f1  fd e6 f2 fd e7 f3 fd e7  |................|
000000e0  f3 fd e8 f3 fd e9 f3 fd  ea f3 fd ea f4 fd e9 f5  |................|
000000f0  fd e9 f6 fd ea f6 fd ea  f6 fd ea f6 fd eb f7 fd  |................|
00000100  eb f7 fd ec f8 fd ed f9  fd ed f9 fd ed f9 fd ed  |................|
00000110  f9 fd ee fa fd ee fa fd  ee fa fd ee fa fd ee fa  |................|
00000120  fd ee fa fd ee fb fd ed  fc fd ec fc fd ec fc fd  |................|
00000130  eb fd fd ea fd fd ea fd  fd ea fd fd eb fc fd ed  |................|
00000140  fc fd ee fc fd ee fc fd  ef fb fd ee fb fd ed fc  |................|
00000150  fd ec fc fd ec fc fd ec  fc fd ec fc fd ec fc fd  |................|
00000160  ec fc fd ec fc fd eb fb  fd eb fb fd eb fb fd eb  |................|
00000170  fb fd eb fb fd eb fb fd  eb fb fd ec fc fd ed fc  |................|
00000180  fd ee fd fd ee fd fd ee  fd fd ee fd fd ee fd fd  |................|
00000190  ee fd fd ee fd fd ee fd  fd ee fd fd ee fd fd ee  |................|
000001a0  fd fd ee fd fd ee fd fd  ee fd fd ed fd fd ec fd  |................|
000001b0  fd eb fd fd ec fd fd ec  fd fd ed fd fd ee 00 fe  |................|
000001c0  ff ff dd fe ff ff 02 f0  39 02 00 f0 4f 00 00 fe  |........9...O...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 c0 20 02 00 00  |............ ...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 0c 76 00 75 1d 00 00  00 00 00 00 02 00 00 00  |..v.u...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 37 40 97 cd 4d  45 4d 4f 52 59 20 43 41  |..)7@..MEMORY CA|
00000050  52 44 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |RDFAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 2a  59 58 00 66 ba 00 00 00  |..E}.f.*YX.f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by srs5694 on 2011-04-02
It looks like GRUB is present, but it wasn't installed to the MBR. I recommend the following:


[list=1]
[*]Download [Super GRUB 2 Disk](http://www.supergrubdisk.org) (note that's the GRUB *2* version, not the GRUB [no number] version).
[*]Burn a CD with Super GRUB 2 Disk.
[*]Boot with Super GRUB 2 Disk. It will give you various options for locating your GRUB files. Try them until you get a menu that shows an Ubuntu boot option, and boot using it.
[*]Once Ubuntu is booted, open a Terminal window and type "sudo grub-install /dev/sda".
[*]Remove the Super GRUB 2 Disk and reboot to see if GRUB appears.
[/list]


It's also possible to re-install GRUB from an emergency disc such as the Ubuntu installer in "live" mode, but I prefer to use Super GRUB 2 Disk for this.

---

### Post by Teegoo on 2011-04-02
That did it! :D

Thanks for your help, guys! I just have a few more questions. One thing I noticed is that I can't connect to the internet, for lack of firmware. Is there a place where I can get the firmware I need?

---

### Post by Anonymous is Incognito on 2011-04-02
Mark this thread as solved and create a new one. It helps keep things seperate.

In the new thread, please post, in [code /] brackets, the output of;

```
lspci
```

---

