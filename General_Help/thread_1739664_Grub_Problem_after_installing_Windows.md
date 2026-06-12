---
title: "Grub Problem after installing Windows"
date: 2011-04-26
forum: General Help
---

### Post by abdulqadir93 on 2011-04-26
I have Windows is C partition and Ubuntu in D partition. After Installing Windows in C, I can't boot into ubuntu. So I installed grub2 in C partition (I have now "boot" folder created in root of the C partition) ... and then I rebooted. I was expecting a menu. but this appeared instead:

```
Minimal Bash like editing is supported for the first word, TAB lists possible command completion. Anywhere else TAB lists possible device or file completion.

grub>_
```

So I have to put these commands at startup to boot xp

grub> chainloader +1
grub> boot

And I don't know how to boot ubuntu. Anyways tht's not the issue. Issue is, I can't figure out how to get the menu back! I can't run these command everytime i start my PC. Please help! thanx in advance

---

### Post by coffeecat on 2011-04-26
> **abdulqadir93 said:**
> So I installed grub2 in C partition (I have now "boot" folder created in root of the C partition)

That was a mistake. Grub files should never be installed to the Windows C: partition. Fortunately, it's fairly easily resolved and your grub booting problem is also easily resolved by reinstalling grub to the mbr. But we need to know which your Ubuntu root partition is before you try this latter.

Boot up the Ubuntu live CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script as described there. Post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags as also described there.

The easiest way of repairing your Windows C: partition boot sector is with a Microsoft installation or repair disc. Which version of Windows are you running? Do you have Microsoft installation or repair discs? Manufacturer's restore discs will not be suitable.

---

### Post by abdulqadir93 on 2011-04-26
```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   104,872,319   104,872,257   7 HPFS/NTFS
/dev/sda2         104,873,984   202,528,767    97,654,784  83 Linux
/dev/sda3         202,528,768   209,727,487     7,198,720  82 Linux swap / Solaris
/dev/sda4         209,728,636   625,137,344   415,408,709   f W95 Ext d (LBA)
/dev/sda5         209,728,638   314,584,829   104,856,192   7 HPFS/NTFS
/dev/sda6         314,584,893   419,441,084   104,856,192   7 HPFS/NTFS
/dev/sda7         419,441,148   524,297,339   104,856,192   7 HPFS/NTFS
/dev/sda8         524,297,403   625,137,344   100,839,942   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1998 MB, 1998585856 bytes
255 heads, 63 sectors/track, 242 cylinders, total 3903488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,903,487     3,903,425   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        BE1483361482F127                       ntfs                                     
/dev/sda2        6973506b-a496-43bd-9e4f-e3eca7c9fb48   ext4                                     
/dev/sda3        d2e9680e-ead6-4a62-af0a-d4cf27cdc247   swap                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        645CA0275C9FF1D2                       ntfs       Muffu                         
/dev/sda6        2818AB8018AB4C1E                       ntfs       Muffu                         
/dev/sda7        CE3CCB1D3CCB0007                       ntfs       Abdul                         
/dev/sda8        EE3CDB3D3CDB000F                       ntfs       Murtaza                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        64D2-D1CE                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

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
set default="1"
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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 6973506b-a496-43bd-9e4f-e3eca7c9fb48
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 6973506b-a496-43bd-9e4f-e3eca7c9fb48
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 6973506b-a496-43bd-9e4f-e3eca7c9fb48
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=6973506b-a496-43bd-9e4f-e3eca7c9fb48 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 6973506b-a496-43bd-9e4f-e3eca7c9fb48
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=6973506b-a496-43bd-9e4f-e3eca7c9fb48 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 6973506b-a496-43bd-9e4f-e3eca7c9fb48
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6973506b-a496-43bd-9e4f-e3eca7c9fb48 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 6973506b-a496-43bd-9e4f-e3eca7c9fb48
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6973506b-a496-43bd-9e4f-e3eca7c9fb48 ro single 
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
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 6973506b-a496-43bd-9e4f-e3eca7c9fb48
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 6973506b-a496-43bd-9e4f-e3eca7c9fb48
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=6973506b-a496-43bd-9e4f-e3eca7c9fb48 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=d2e9680e-ead6-4a62-af0a-d4cf27cdc247 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  75.4GB: boot/grub/core.img
  75.3GB: boot/grub/grub.cfg
  58.2GB: boot/initrd.img-2.6.35-22-generic
  58.3GB: boot/initrd.img-2.6.35-28-generic
  75.6GB: boot/vmlinuz-2.6.35-22-generic
  75.6GB: boot/vmlinuz-2.6.35-28-generic
  58.3GB: initrd.img
  58.2GB: initrd.img.old
  75.6GB: vmlinuz
  75.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 48 02  |.X.SYSLINUX...H.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c1 8f 3b 00 dc 0e 00 00  00 00 00 00 02 00 00 00  |..;.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 ce d1 d2 64 4e  4f 20 4e 41 4d 45 20 20  |..)...dNO NAME  |
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
00000100  7d 00 66 b8 d8 c7 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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


First of all thank u very much for the reply. Ooopsss ... I thought since C partition was my bootable partition I should install grub there. I have Windows XP. And unfortunately. I dont have the repair disks. What If i just delete the "boot" folder from C partition?!? Will it revert back to normal?

---

### Post by coffeecat on 2011-04-26
> **abdulqadir93 said:**
>  Ooopsss ... I thought since C partition was my bootable partition I should install grub there.

No, but this is a common misunderstanding. I presume by "bootable" that you are referring to the boot flag. This only has relevance to Windows and only if you have Windows boot code in the mbr. All that does is to pass the boot process onto the boot files in the boot sector of the partition with the boot flag. If you use grub, the boot flag becomes irrelevant even with Windows. Part of the grub code is installed to the mbr (and the embedding area, the space between the partition table and the first sector of the first partition), which looks to the Linux root partition for the rest of itself.

So - on to fixing grub in order to get you booting into Ubuntu at least. Boot up with the Ubuntu Maverick live CD.  Open a terminal, and run these commands:

```
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```There is a slight inconsistency in your grub.cfg file, because your sda2 Ubuntu root partition was originally sda3 before you installed Windows. This won't matter, because grub.cfg has the correct partition UUID. Now reboot and you should be able to see the grub menu and boot into Ubuntu. We haven't fixed Windows yet, so don't try that just yet.

> **abdulqadir93 said:**
>   I have Windows XP. And unfortunately. I dont have the repair disks. What If i just delete the "boot" folder from C partition?!? Will it revert back to normal?

Don't delete anything just yet. Just to be sure: you don't have the XP installation disc? If you do it's simply a matter of running 'fixboot' from the repair console command line. If you don't, there is a way of doing it from Ubuntu, but I need to find a weblink for you. I'll post again.

---

### Post by coffeecat on 2011-04-26
> **coffeecat said:**
> I need to find a weblink for you. I'll post again.

I found it quicker than I thought I could. Have a look at this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

The first thing to note is that it describes boot sector damage worse than the boot script is reporting in your partition sda1. It's just possible that the presence of /boot/grub/core.img is not doing any harm. Your problem stemmed from the fact that grub in the mbr was looking to sda1 when it should have been looking to sda2. So try this.

Once you've repaired grub as in my previous post and you are able to boot into Ubuntu, run:

```
sudo update-grub
```

Now reboot. Is there a Windows entry? Can you boot into Windows with it? If yes to both, problem solved, and you can ignore the presence of /boot/grub/core.img in the Windows partition - or you could delete it if you want.

If that doesn't work, try installing testdisk as described in that link (it's in the Ubuntu repos) and following the steps described there. Don't forget to run "sudo update-grub" before you reboot.

---

### Post by ahears on 2011-06-25
Hey, Coffeecat is right but he forgot one thing; before you run 'update-grub' from a live cd, you must mount the partition with the Ubuntu installation. Execute 'mount /dev/sda2 /media/whereveryouwanttomountubuntu' (if ubuntu is the second partition) then 'chroot /media/whereverubuntuismounted' THEN, 'grub-install /dev/sda' (or wherever the ubuntu partition is located...not mounted.) , and finally 'update-grub'. Make sure you see 'Windows 7' is listed in the output..

---

