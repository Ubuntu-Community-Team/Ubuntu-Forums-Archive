---
title: "Fixing &quot;missing operating system&quot; error"
date: 2011-02-26
forum: General Help
---

### Post by Gertlex on 2011-02-26
I'm having a fun Saturday. x_x

The problem I bring to you guys is this:
I have Ubuntu 10.10 x64 installed on a HD.  If I boot from this hard drive, I get the error "missing operating system".  And thus I can't run my Ubuntu install.

My suspicion is that grub (grub2?) is broken on this install.  I've run Ubuntu off of a flash drive attempting to investigate, but have given up since I don't know enough.

Other info:
In the past this install has worked fine... My normal setup is a HD with Win 7 on it, and the Ubuntu HD, and a storage HD.  I initially installed Ubuntu on the same drive as the Win 7 install (worst decision I've made in the past several months, imo).  I have been stuck using grub as my bootloader since then, and it appears that grub was embedded on the Win 7 HD, and then managed to boot the Ubuntu HD.  That's all gone to hell since I tried repairing the windows MBR earlier today.

Right now I'm focusing on getting my Ubuntu install to be self-sufficient.  It seems I probably ought to just reinstall, but let's see if anyone can help me here, first.

Thanks, and let me know any other info I can provide of use...

---

### Post by wilee-nilee on 2011-02-26
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by Gertlex on 2011-02-26
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

sdb: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,126   254,214,143   254,198,018   f W95 Ext d (LBA)
/dev/sda5              16,128   244,204,096   244,187,969   7 HPFS/NTFS
/dev/sda6         244,205,568   254,214,143    10,008,576  82 Linux swap / Solaris
/dev/sda2    *    254,214,144   488,396,799   234,182,656  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4093 MB, 4093640704 bytes
63 heads, 62 sectors/track, 2046 cylinders, total 7995392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          8,192     7,995,391     7,987,200   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: PTTYPE="dos" 
/dev/sda2        fcaff426-b766-42af-a460-22437b55a87a   ext4                                     
/dev/sda5        4642656C42656223                       ntfs       New Volume                    
/dev/sda6        b03466f9-7568-4cc9-aa16-79aa7338ac83   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb         3e6fddd7-aca5-4912-8d5a-8d5be5c47bd6   xfs                                      
/dev/sdc1        90E3-B50B                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 
/dev/sdd         3248BC2948BBEA2D                       ntfs       OCZ DIESEL                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/MB SUPPORT CD     iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda2        /media/fcaff426-b766-42af-a460-22437b55a87a ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb         /media/3e6fddd7-aca5-4912-8d5a-8d5be5c47bd6 xfs        (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd         /media/OCZ DIESEL        fuseblk    (rw,nosuid,nodev,allow_other,blksize=512,default_permissions)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set fcaff426-b766-42af-a460-22437b55a87a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set fcaff426-b766-42af-a460-22437b55a87a
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
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set fcaff426-b766-42af-a460-22437b55a87a
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=fcaff426-b766-42af-a460-22437b55a87a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set fcaff426-b766-42af-a460-22437b55a87a
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=fcaff426-b766-42af-a460-22437b55a87a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set fcaff426-b766-42af-a460-22437b55a87a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fcaff426-b766-42af-a460-22437b55a87a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set fcaff426-b766-42af-a460-22437b55a87a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fcaff426-b766-42af-a460-22437b55a87a ro single 
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
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set fcaff426-b766-42af-a460-22437b55a87a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set fcaff426-b766-42af-a460-22437b55a87a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set d010f96d10f95ac4
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=fcaff426-b766-42af-a460-22437b55a87a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b03466f9-7568-4cc9-aa16-79aa7338ac83 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


 134.5GB: boot/grub/core.img
 216.2GB: boot/grub/grub.cfg
 131.2GB: boot/initrd.img-2.6.35-22-generic
 131.7GB: boot/initrd.img-2.6.35-25-generic
 134.7GB: boot/vmlinuz-2.6.35-22-generic
 134.7GB: boot/vmlinuz-2.6.35-25-generic
 131.7GB: initrd.img
 131.2GB: initrd.img.old
 134.7GB: vmlinuz
 134.7GB: vmlinuz.old

=========================== sdc1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdc1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 26 00  |.X.SYSLINUX...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 20 00 00  |........?.... ..|
00000020  00 e0 79 00 69 1e 00 00  00 00 00 00 02 00 00 00  |..y.i...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 0b b5 e3 90 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
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
00000100  7d 00 66 b8 00 3d 00 00  66 ba 00 00 00 00 bb 00  |}.f..=..f.......|
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

### Post by wilee-nilee on 2011-02-26
So if you could state what was working it would be helpful, as in what you did to stop this. You have the Windows in a extended, looks like a clone to be honest it shouldn't boot from there. You have the windows bootloader in the mbr it wont boot Ubuntu.

Is sda5 a shared partition?

---

### Post by Monotoko on 2011-02-26
Try to restore Grub2 using a LiveCD, I had to do it the other day:

You can follow this tutorial: [http://maketecheasier.com/restore-grub-2-as-the-main-bootloader/2010/05/05](http://maketecheasier.com/restore-grub-2-as-the-main-bootloader/2010/05/05)

---

### Post by Gertlex on 2011-02-26
> **wilee-nilee said:**
> So if you could state what was working it would be helpful, as in what you did to stop this. You have the Windows in a extended, looks like a clone to be honest it shouldn't boot from there. You have the windows bootloader in the mbr it wont boot Ubuntu.

Is sda5 a shared partition?
Not entirely clear on what you're asking.

What started my problems in general today was using my Win 7 CD to repair stuff in an attempt to get hibernate to work again.  Specifically I followed this guide: [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html) .  After that, I was unable to get anything to boot.  Eventually I decided to isolate my hard drives and see what each one did, and that's when I discovered that the ubuntu install won't boot either.

sda 5 is the second partition (unused) on the hard drive with ubuntu on it.  Both are about equally-sized.

---

### Post by Monotoko on 2011-02-26
I see,

You need to use the Ubuntu bootloader (GRUB) as the Windows boot loader isn't Linux friendly and will just boot itself. The Linux bootloader will find everything and give you an option.

Follow the guide to restore the bootloader and then run update-grub and it should be all good :)

---

### Post by FoxEWolf on 2011-02-26
"Missing Operating System" errors bring me back to my now dead Compaq Presario C300.

I am only wondering if you are using a Compaq as well. (or HP since both companies have merged)

---

### Post by Gertlex on 2011-02-26
I'm back into ubuntu after following the grub repair guide.  Thanks all! :)

> **FoxEWolf said:**
> "Missing Operating System" errors bring me back to my now dead Compaq Presario C300.

I am only wondering if you are using a Compaq as well. (or HP since both companies have merged)
To sate your curiosity: no :)

Self-built AMD Phenom II 1090t, 16gb ram, asus mobo, ASUS Radeon 5770 graphics card oh and purple lighting ;)

---

