---
title: "Stuck on Grub Startup"
date: 2010-12-06
forum: General Help
---

### Post by macro312 on 2010-12-06
System: Acer Aspire
1 hard disk with two partitions
I recently installed ubuntu on my second partition
and decided to update the thing. Silly mistake, I installed grub.
Now it has over written my booting sequence to Grub itself.
I cannot access my either os (Windows 7 or Ubuntu) due to it just loading up the grub prompt.
So right now I'm using the live"usb" of ubuntu.

My question is "How do I use grub to boot my Windows 7?"

Also: I used boot_info_script055.sh
Result: ```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 18791760 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Windows/System32/winload.exe /wubildr.mbr 
                       /wubildr

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 579539456 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk 
                       /boot/grub/core.img

sda4/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    26,626,047    26,624,000  27 Hidden HPFS/NTFS
/dev/sda2    *     26,626,048    26,830,847       204,800   7 HPFS/NTFS
/dev/sda3          26,830,848   501,745,663   474,914,816   7 HPFS/NTFS
/dev/sda4         501,745,664   976,771,119   475,025,456   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8088 MB, 8088715264 bytes
5 heads, 32 sectors/track, 98739 cylinders, total 15798272 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064    15,798,271    15,790,208   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       2297b4d8-cb89-4f2a-b44b-90b5a8b77633   ext4                                     
/dev/sda1        DAA41C49A41C2B11                       ntfs       PQSERVICE                     
/dev/sda2        020868D20868C5EF                       ntfs       SYSTEM RESERVED               
/dev/sda3        CAD47BD5D47BC1ED                       ntfs       ACER                          
/dev/sda4        90422DAD422D994C                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        574D-4D2B                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=================== sda4: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

======================== sda4/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ntfs
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 90422dad422d994c
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ntfs
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 90422dad422d994c
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 90422dad422d994c
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda4 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 90422dad422d994c
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda4 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 90422dad422d994c
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda4 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 90422dad422d994c
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda4 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set daa41c49a41c2b11
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 020868d20868c5ef
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda4/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda4/Wubi: Location of files loaded by Grub: =================


  15.1GB: boot/grub/core.img
  10.9GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.32-24-generic
   1.0GB: boot/initrd.img-2.6.32-26-generic
  15.1GB: boot/vmlinuz-2.6.32-24-generic
  15.1GB: boot/vmlinuz-2.6.32-26-generic
   1.0GB: initrd.img
    .9GB: initrd.img.old
  15.1GB: vmlinuz
  15.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 c0 07  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  20 00 10 00 80 1f 00 00  |........ .......|
00000020  80 f0 f0 00 20 3c 00 00  00 00 00 00 02 00 00 00  |.... <..........|
00000030  01 00 08 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 2b 4d 4d 57 54  4f 53 48 49 42 41 20 20  |..)+MMWTOSHIBA  |
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
00000100  7d 00 66 b8 18 28 16 00  66 ba 00 00 00 00 bb 00  |}.f..(..f.......|
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


```In advance thanks guys. :)

---

### Post by macro312 on 2010-12-06
btw [http://forums.scotsnewsletter.com/index.php?act=ST&f=14&t=5025](http://forums.scotsnewsletter.com/index.php?act=ST&f=14&t=5025)
that is my exact problem but when I'm up to the kernel bit it says
"Error: unknow command 'kernel' "

---

### Post by macro312 on 2010-12-07
I have figured my Grub does not have kernel. I might need to update it.... but suggestions would be nice (Just bumping this post up)

---

### Post by wilee-nilee on 2010-12-07
So first if you look at the bootscript you have 4 sda1,2,3,4 partitions not 2. Just for information here since you actually have a pretty messed up setup I wont go into the details first where the problems are. But do you have everything backed up and do you have a W7 install disc?

Are you willing to just do a fresh install and maybe dual boot without the wubi setup? I ask this because although this may be fixable, I see the work of a new user that has left a system pretty messed up. Not a big deal we all started out as new users, I would just like to see you set up and understanding the setup.;)

I would stop the web searches for answers as I suspect your understanding may just get things worse. Your on one of the best forums for just the problems you have.

---

### Post by bcbc on 2010-12-07
Reinstall the windows boot loader - boot from windows dvd/repairCD and run 'bootrec.exe /fixmbr'

You've installed grub everywhere (MBR, boot sectors on sda1 and sda4) but your main windows boot partition sda2 is still clean, so maybe it will work ok. Otherwise you'll have to restore your bootsectors using windows repair or testdisk ([http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector))

This should work to boot wubi from grub prompt:
```
insmod ntfs
set root=(hd0,4)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda4 loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot
```

---

### Post by wilee-nilee on 2010-12-07
> **bcbc said:**
> Reinstall the windows boot loader - boot from windows dvd/repairCD and run 'bootrec.exe /fixmbr'

You've installed grub everywhere (MBR, boot sectors on sda1 and sda4) but your main windows boot partition sda2 is still clean, so maybe it will work ok. Otherwise you'll have to restore your bootsectors using windows repair or testdisk ([http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector))

This should work to boot wubi from grub prompt:
```
insmod ntfs
set root=(hd0,4)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda4 loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot
```

Are you sure here with grub in sda4, I see the right stuff here but I wondered about that partition. Hopefully testdisk will clean it up.

---

### Post by bcbc on 2010-12-07
> **wilee-nilee said:**
> Are you sure here with grub in sda4, I see the right stuff here but I wondered about that partition. Hopefully testdisk will clean it up.

I'm not sure at all. I know Wubi doesn't care about the bootsector so it should boot fine... I'm hoping that windows only cares about the bootsector on /sda2 (the one with the boot flag). I figure it's worth a shot though, if the alternative is reinstalling.

Also I can't figure out how grub installs itself to windows partition bootsectors anymore. Grub is supposed to prevent this - unless it was --force installed.

---

### Post by wilee-nilee on 2010-12-07
> **bcbc said:**
> I'm not sure at all. I know Wubi doesn't care about the bootsector so it should boot fine... I'm hoping that windows only cares about the bootsector on /sda2 (the one with the boot flag). I figure it's worth a shot though, if the alternative is reinstalling.

Also I can't figure out how grub installs itself to windows partition bootsectors anymore. Grub is supposed to prevent this - unless it was --force installed.

Yeah man your on the right track especially with the manual boot, but you just plain know more about everything really.;) My first response was just phishing for the tackle box.

---

### Post by Rubi1200 on 2010-12-07
> **bcbc said:**
> Also I can't figure out how grub installs itself to windows partition bootsectors anymore. Grub is supposed to prevent this - unless it was --force installed.
I believe for versions before 10.10, there is still an option to install "everywhere," so to speak.

@macro312:
for general information, troubleshooting, and solutions for Wubi installs see here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

