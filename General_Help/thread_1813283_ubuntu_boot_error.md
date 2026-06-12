---
title: "ubuntu boot error"
date: 2011-07-27
forum: General Help
---

### Post by mihir_g on 2011-07-27
Hi all,
for past few days i have been  trying ti install and get ubunto to work on my desktop. here is thelink of all the support i have got so far .
my problem is stiill not solved . please help. thanks. 

[https://answers.launchpad.net/ubuntu/+source/grub2/+question/165078](https://answers.launchpad.net/ubuntu/+source/grub2/+question/165078)

---

### Post by seawolf167 on 2011-07-27
I read through it cursorily - can you please post the output of the [boot script found here]("http://bootinfoscript.sourceforge.net/"). Please use the "New Reply" button instead of "Quick Reply" and paste the contents inside CODE tags.

---

### Post by mihir_g on 2011-07-28
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 61620 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   112,647,779   112,647,717   7 NTFS / exFAT / HPFS
/dev/sda2         141,946,878   976,751,999   834,805,122   f W95 Extended (LBA)
/dev/sda5         217,504,098   636,929,054   419,424,957   7 NTFS / exFAT / HPFS
/dev/sda6         636,929,118   976,751,999   339,822,882   7 NTFS / exFAT / HPFS
/dev/sda7         141,946,880   151,709,695     9,762,816  83 Linux
/dev/sda8         209,690,624   217,503,743     7,813,120  82 Linux swap / Solaris
/dev/sda9         151,711,744   209,522,687    57,810,944  83 Linux
/dev/sda3         112,648,192   141,944,831    29,296,640  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8103 MB, 8103395328 bytes
255 heads, 63 sectors/track, 985 cylinders, total 15826944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    15,826,922    15,826,860   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        B24C66094C65C8A5                       ntfs       Windows
/dev/sda3        d2a7a0db-9d4d-48c7-9a97-23d2cbdc2e19   ext4       
/dev/sda5        A49C0CB59C0C8450                       ntfs       Storage
/dev/sda6        B20812F70812BA75                       ntfs       Backup
/dev/sda7        ec50e832-e27c-4ae4-ba37-09145f70a63c   ext4       
/dev/sda8        0527df24-d0ea-4fca-963b-ae2cc6c2a7dc   swap       
/dev/sda9        8f9e2e6b-7762-4bde-bf45-18f4ee8537d3   ext3       
/dev/sdb1        1A01-1A46                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

============================= sda7/grub/grub.cfg: ==============================

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
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root d2a7a0db-9d4d-48c7-9a97-23d2cbdc2e19
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root ec50e832-e27c-4ae4-ba37-09145f70a63c
set locale_dir=($root)/grub/locale
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
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root ec50e832-e27c-4ae4-ba37-09145f70a63c
    linux    /vmlinuz-2.6.38-8-generic root=UUID=d2a7a0db-9d4d-48c7-9a97-23d2cbdc2e19 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root ec50e832-e27c-4ae4-ba37-09145f70a63c
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=d2a7a0db-9d4d-48c7-9a97-23d2cbdc2e19 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root ec50e832-e27c-4ae4-ba37-09145f70a63c
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root ec50e832-e27c-4ae4-ba37-09145f70a63c
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root B24C66094C65C8A5
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
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  69.942909241 = 75.100626944   grub/core.img                                  1
  69.939472198 = 75.096936448   grub/grub.cfg                                  1
  67.861541748 = 72.865775616   initrd.img-2.6.38-8-generic                    1
  67.825599670 = 72.827183104   vmlinuz-2.6.38-8-generic                       1

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=d2a7a0db-9d4d-48c7-9a97-23d2cbdc2e19 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda7 during installation
UUID=ec50e832-e27c-4ae4-ba37-09145f70a63c /boot           ext4    defaults        0       2
# /home was on /dev/sda9 during installation
UUID=8f9e2e6b-7762-4bde-bf45-18f4ee8537d3 /home           ext3    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=0527df24-d0ea-4fca-963b-ae2cc6c2a7dc none            swap    sw              0       0
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  92 42 6b 84 b6 47 9c 05  43 5d d8 b1 f0 48 36 f4  |.Bk..G..C]...H6.|
00000010  2e 17 98 dd 87 32 47 31  d1 7b c2 a0 40 e7 38 68  |.....2G1.{..@.8h|
00000020  1c 34 c1 47 bc 18 08 c7  c3 30 31 8f 1f 78 82 18  |.4.G.....01..x..|
00000030  22 30 0c bc 41 0a 0a c4  15 e1 d0 60 13 86 5e f1  |"0..A......`..^.|
00000040  58 73 75 e7 de 90 54 74  e9 e9 44 4e 95 85 83 df  |Xsu...Tt..DN....|
00000050  a3 24 b4 24 3b 1c a0 80  e9 4e 94 a7 11 01 d6 9e  |.$.$;....N......|
00000060  4d 94 69 55 69 e6 0d d4  ab 26 c9 d2 95 64 c5 43  |M.iUi....&...d.C|
00000070  ed c9 5b 34 f1 79 ba 76  13 f1 c7 1e 1c 9c d2 24  |..[4.y.v.......$|
00000080  7f 19 3c 47 34 d5 26 9e  f4 88 38 d0 38 8e 14 7b  |..<G4.&...8.8..{|
00000090  d1 c3 e0 57 3d a6 b0 d6  9a 53 83 06 02 d1 50 20  |...W=....S....P |
000000a0  27 10 16 b9 c1 50 60 12  7b d2 0a ce 94 a6 d4 a2  |'....P`.{.......|
000000b0  25 a1 e8 11 5f a2 7a bc  a0 a6 2d 71 7a 2f 84 cf  |%..._.z...-qz/..|
000000c0  1e 8e 74 a0 54 35 0f d2  93 22 91 cf 0b 0d 0d 4a  |..t.T5...".....J|
000000d0  db c1 c5 bc 30 39 9a 9a  04 78 6d 05 4d b5 b2 27  |....09...xm.M..'|
000000e0  9d 1c 9f cf 16 b9 14 75  3e 7c 31 ff 28 2a 1d 76  |.......u>|1.(*.v|
000000f0  82 9e 22 8e ac b5 b8 d7  7b a9 0c de 2c a8 68 12  |..".....{...,.h.|
00000100  0e e7 54 14 ab 52 16 8a  07 b4 f0 90 ad 9e ac 14  |..T..R..........|
00000110  29 53 37 4a d3 a7 e9 46  4e 11 1b c2 80 79 f4 8a  |)S7J...FN....y..|
00000120  38 d0 38 8e 15 7b d1 c3  e0 43 c7 6b 8f 1f 1a 0e  |8.8..{...C.k....|
00000130  11 18 0a 21 88 60 41 10  13 aa bd 20 98 0a c3 01  |...!.`A.... ....|
00000140  67 d2 dc 89 d7 87 d0 31  0b f5 3b cb c6 a5 f6 92  |g......1..;.....|
00000150  ff 6b 50 fb c6 83 3e 9d  b1 51 40 72 4a 94 45 47  |.kP...>..Q@rJ.EG|
00000160  b2 be 82 41 99 11 e3 a3  b3 28 81 31 36 cd ed 18  |...A.....(.16...|
00000170  45 ae 7e dc 01 e2 20 12  95 0c f4 e1 50 0e cd 4e  |E.~... .....P..N|
00000180  33 2c 40 e1 60 7b 4f 7c  3a 72 f9 a3 8e 91 92 14  |3,@.`{O|:r......|
00000190  46 22 3c 1a 0c 33 f5 e2  80 75 0a cf 88 ce a7 9f  |F"<..3...u......|
000001a0  49 dd 36 44 44 e9 19 06  80 c5 14 77 bc 28 0c 14  |I.6DD......w.(..|
000001b0  7a 28 81 f8 20 f3 c6 8f  c7 1f 7a 26 06 24 00 01  |z(.. .....z&.$..|
000001c0  c1 ff 07 fe ff ff 64 e9  80 04 bd ea ff 18 00 fe  |......d.........|
000001d0  ff ff 05 fe ff ff 21 d4  80 1d 61 49 41 14 00 00  |......!...aIA...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

---

### Post by seawolf167 on 2011-07-28
[This is the error ]("http://www.flickr.com/photos/65316605@N03/5961647042/in/photostream")you are still receiving upon boot? Any cds in the drive and do you have your drive /dev/sda (500GB drive) set as the first priority boot device in BIOS? (and remove the flash drive so it doesn't attempt to boot off that if it has a higher priority)

---

### Post by mihir_g on 2011-07-28
Perfect... Thats the error i am facing. 
In the BIOS , the the hard disk is set as the first boot device. 


P.S. I have only one hard disk.( SATA)

---

### Post by seawolf167 on 2011-07-28
What mode is the hard drive setting on in BIOS? (IDE, AHCI/SATA, etc.)

I would check this first as you said the drive is a SATA drive so you don't have any jumpers to worry about.

---

### Post by mihir_g on 2011-07-28
> **seawolf167 said:**
> What mode is the hard drive setting on in BIOS? (IDE, AHCI/SATA, etc.)

I would check this first as you said the drive is a SATA drive so you don't have any jumpers to worry about.
How do i check that ? I have not seen this in the bios setup

---

### Post by seawolf167 on 2011-07-28
Should be under something similar to :

[LIST]
[*]SATA Configuration
[*]SATA Mode Select
[*]SATA RAID/AHCI Mode
[*]SATA IDE/AHCI Mode
[/LIST]

---

### Post by mihir_g on 2011-07-28
[IMG]http://ubuntuforums.org/%3Ca%20href=http://imageshack.us/photo/my-images/221/biosdriveconfig.jpg/%20target=_blank%3E[IMG]http://img221.imageshack.us/img221/92/biosdriveconfig.th.jpg[/IMG]
[http://img221.imageshack.us/img221/92/biosdriveconfig.jpg](http://img221.imageshack.us/img221/92/biosdriveconfig.jpg)

I cannot see such sata config. here are the images...

---

### Post by seawolf167 on 2011-07-28
What are you other options under the "enhanced" option and "enable" options?

---

### Post by mihir_g on 2011-07-28
ATA/IDE : Legacy
               Enhanced


the other option foe enable is disable. If we select that nothing happens . 

Here is another link of my bios
[http://imageshack.us/photo/my-images/59/img028ez.jpg/](http://imageshack.us/photo/my-images/59/img028ez.jpg/)

---

### Post by mihir_g on 2011-07-30
Do i need to change my motherboard

---

### Post by seawolf167 on 2011-07-30
> **mihir_g said:**
> Do i need to change my motherboard

I wouldn't think so - especially if you had everything up and running without installing the drivers for AHCI mode and have been using EIDE (enhanced IDE mode). 

Honestly, I'm not sure what other steps to take (the boot script looks ok, hardware appears to be working, etc.), hopefully someone else will chime in with some ideas!

---

