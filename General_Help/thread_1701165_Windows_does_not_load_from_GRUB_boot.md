---
title: "Windows does not load from GRUB boot"
date: 2011-03-06
forum: General Help
---

### Post by clivewearing on 2011-03-06
Hi all, 

I have installed Ubuntu (10.4) on a Windows machine leaving the possibility to choose which OS should be booted (but, by default, Ubuntu was loaded automatically).
After few month using only Ubuntu, I choose the Windows partition from the boot screen but it did not load (and it gave me an error that the partition cannot be found...but I cannot recall exactly what it was about...).
Then, I tried again and the option for the Windows partition disappeared...(see attached pic).

[IMG]http://img851.imageshack.us/i/boot.jpg/[/IMG][[IMG]http://img851.imageshack.us/img851/6812/boot.jpg[/IMG]]("http://img851.imageshack.us/i/boot.jpg/")

How can I fix that?
Is there the possibility to re-install Windows on its partition from Ubuntu?
I have Ubuntu 10.4 and (I had) Windows XP.
I used GNU GRUB version 1.98
Many thanks in advance for your help.
Best
M.

---

### Post by clivewearing on 2011-03-06
Hi all, 

quick update.
I have run bootinfoscript and the result is the following, in  case this can help somehow...
Thank you again
M.



```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 30.0 GB, 30020272128 byte
255 testine, 63 settori/tracce, 3649 cilindri, totale 58633344 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    58,605,119    58,605,057   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 80.0 GB, 80026361856 byte
255 testine, 63 settori/tracce, 9729 cilindri, totale 156301488 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    24,579,449    24,579,387   7 HPFS/NTFS
/dev/sdb2          24,579,511   156,301,311   131,721,801   f W95 Ext d (LBA)
/dev/sdb5          24,579,513   132,191,840   107,612,328   7 HPFS/NTFS
/dev/sdb6         132,192,256   155,185,151    22,992,896  83 Linux
/dev/sdb7         155,187,200   156,301,311     1,114,112  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        34C8-23E7                              vfat       DATI                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8C280137280121B6                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        666CA0706CA03D25                       ntfs       Film & Musica                 
/dev/sdb6        0d6d3245-424c-42ce-beff-fd283e485bf4   ext4                                     
/dev/sdb7        76248c1c-a0d6-4d0e-aab7-08ecd77fa5b0   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/DATI              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb5        /media/Film & Musica     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
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
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
set locale_dir=($root)/boot/grub/locale
set lang=it
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
menuentry 'Ubuntu, con Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=0d6d3245-424c-42ce-beff-fd283e485bf4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-29-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    echo    'Caricamento Linux 2.6.32-29-generic...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=0d6d3245-424c-42ce-beff-fd283e485bf4 ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=0d6d3245-424c-42ce-beff-fd283e485bf4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-28-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    echo    'Caricamento Linux 2.6.32-28-generic...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=0d6d3245-424c-42ce-beff-fd283e485bf4 ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=0d6d3245-424c-42ce-beff-fd283e485bf4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-27-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    echo    'Caricamento Linux 2.6.32-27-generic...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=0d6d3245-424c-42ce-beff-fd283e485bf4 ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=0d6d3245-424c-42ce-beff-fd283e485bf4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-26-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    echo    'Caricamento Linux 2.6.32-26-generic...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=0d6d3245-424c-42ce-beff-fd283e485bf4 ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=0d6d3245-424c-42ce-beff-fd283e485bf4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-25-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    echo    'Caricamento Linux 2.6.32-25-generic...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=0d6d3245-424c-42ce-beff-fd283e485bf4 ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=0d6d3245-424c-42ce-beff-fd283e485bf4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-24-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    echo    'Caricamento Linux 2.6.32-24-generic...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=0d6d3245-424c-42ce-beff-fd283e485bf4 ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=0d6d3245-424c-42ce-beff-fd283e485bf4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-23-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    echo    'Caricamento Linux 2.6.32-23-generic...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=0d6d3245-424c-42ce-beff-fd283e485bf4 ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=0d6d3245-424c-42ce-beff-fd283e485bf4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-22-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    echo    'Caricamento Linux 2.6.32-22-generic...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=0d6d3245-424c-42ce-beff-fd283e485bf4 ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0d6d3245-424c-42ce-beff-fd283e485bf4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    echo    'Caricamento Linux 2.6.32-21-generic...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=0d6d3245-424c-42ce-beff-fd283e485bf4 ro single 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 0d6d3245-424c-42ce-beff-fd283e485bf4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=0d6d3245-424c-42ce-beff-fd283e485bf4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=76248c1c-a0d6-4d0e-aab7-08ecd77fa5b0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


  70.0GB: boot/grub/core.img
  73.4GB: boot/grub/grub.cfg
  70.3GB: boot/initrd.img-2.6.32-21-generic
  70.5GB: boot/initrd.img-2.6.32-22-generic
  72.0GB: boot/initrd.img-2.6.32-23-generic
  70.6GB: boot/initrd.img-2.6.32-24-generic
  75.9GB: boot/initrd.img-2.6.32-25-generic
  75.7GB: boot/initrd.img-2.6.32-26-generic
  78.6GB: boot/initrd.img-2.6.32-27-generic
  72.1GB: boot/initrd.img-2.6.32-28-generic
  71.5GB: boot/initrd.img-2.6.32-29-generic
  70.1GB: boot/vmlinuz-2.6.32-21-generic
  70.3GB: boot/vmlinuz-2.6.32-22-generic
  72.0GB: boot/vmlinuz-2.6.32-23-generic
  70.5GB: boot/vmlinuz-2.6.32-24-generic
  71.7GB: boot/vmlinuz-2.6.32-25-generic
  75.3GB: boot/vmlinuz-2.6.32-26-generic
  72.0GB: boot/vmlinuz-2.6.32-27-generic
  71.3GB: boot/vmlinuz-2.6.32-28-generic
  78.8GB: boot/vmlinuz-2.6.32-29-generic
  71.5GB: initrd.img
  72.1GB: initrd.img.old
  78.8GB: vmlinuz
  71.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  00 32 45 04 00 58 45 04  00 68 45 04 00 90 45 04  |.2E..XE..hE...E.|
00000010  00 ac 45 04 00 d4 45 04  00 e4 45 04 00 fa 45 04  |..E...E...E...E.|
00000020  00 14 46 04 00 36 46 04  00 68 46 04 00 8a 46 04  |..F..6F..hF...F.|
00000030  00 a8 46 04 00 ca 46 04  00 14 47 04 00 24 47 04  |..F...F...G..$G.|
00000040  00 5c 47 04 00 6c 47 04  00 88 47 04 00 a8 47 04  |.\G..lG...G...G.|
00000050  00 ba 47 04 00 f2 47 04  00 1c 48 04 00 2e 48 04  |..G...G...H...H.|
00000060  00 3a 48 04 00 66 48 04  00 7e 48 04 00 b8 48 04  |.:H..fH..~H...H.|
00000070  00 de 48 04 00 76 49 04  00 84 49 04 00 96 49 04  |..H..vI...I...I.|
00000080  00 d2 49 04 00 5c 4a 04  00 b0 4a 04 00 00 4b 04  |..I..\J...J...K.|
00000090  00 0a 4d 04 00 2a 4d 04  00 a4 50 04 00 22 52 04  |..M..*M...P.."R.|
000000a0  00 22 54 04 00 48 54 04  00 56 54 04 00 64 54 04  |."T..HT..VT..dT.|
000000b0  00 70 54 04 00 7c 54 04  00 a6 54 04 00 d0 54 04  |.pT..|T...T...T.|
000000c0  00 e8 54 04 00 00 55 04  00 18 55 04 00 30 55 04  |..T...U...U..0U.|
000000d0  00 46 55 04 00 5c 55 04  00 78 55 04 00 94 55 04  |.FU..\U..xU...U.|
000000e0  00 a4 55 04 00 c8 55 04  00 d4 55 04 00 f4 55 04  |..U...U...U...U.|
000000f0  00 00 56 04 00 22 56 04  00 3a 56 04 00 62 56 04  |..V.."V..:V..bV.|
00000100  00 88 56 04 00 a0 56 04  00 b8 56 04 00 c8 56 04  |..V...V...V...V.|
00000110  00 00 57 04 00 10 57 04  00 1c 57 04 00 3a 57 04  |..W...W...W..:W.|
00000120  00 4c 57 04 00 5e 57 04  00 a0 57 04 00 f6 57 04  |.LW..^W...W...W.|
00000130  00 50 58 04 00 6e 58 04  00 7e 58 04 00 fe 58 04  |.PX..nX..~X...X.|
00000140  00 54 59 04 00 b6 59 04  00 fa 59 04 00 18 5a 04  |.TY...Y...Y...Z.|
00000150  00 3e 5a 04 00 5c 5a 04  00 6a 5a 04 00 8e 5a 04  |.>Z..\Z..jZ...Z.|
00000160  00 92 5a 04 00 9e 5a 04  00 b8 5a 04 00 ec 5a 04  |..Z...Z...Z...Z.|
00000170  00 20 5b 04 00 4a 5b 04  00 5e 5b 04 00 6a 5b 04  |. [..J[..^[..j[.|
00000180  00 7e 5b 04 00 8c 5b 04  00 9a 5b 04 00 b2 5b 04  |.~[...[...[...[.|
00000190  00 c8 5b 04 00 e4 5b 04  00 48 5c 04 00 f4 5c 04  |..[...[..H\...\.|
000001a0  00 d0 5d 04 00 3c 5e 04  00 c4 5e 04 00 54 5f 04  |..]..<^...^..T_.|
000001b0  00 82 5f 04 00 c2 5f 04  00 f8 5f 04 00 60 00 01  |.._..._..._..`..|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 a8 08 6a 06 00 fe  |............j...|
000001d0  ff ff 05 fe ff ff aa 08  6a 06 9f d9 5e 01 00 00  |........j...^...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

