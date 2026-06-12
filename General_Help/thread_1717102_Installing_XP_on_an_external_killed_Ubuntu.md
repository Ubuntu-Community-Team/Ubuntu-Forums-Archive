---
title: "Installing XP on an external killed Ubuntu"
date: 2011-03-29
forum: General Help
---

### Post by Stop Being Such a TOONA on 2011-03-29
I've been attempting to fix my co-workers for the past week or so; his hard drive is shot.  I recovered all his files and that, no problem.  So yesterday I decided to install XP on his external hard drive so he could still use Windows, he was struggling with using Ubuntu which I have installed on my external.  So I partitioned up his external popped in the install CD and proceed to install it.  After booting up all the files i picked the 100gb partition I had made and installed.  I then rebooted and tried to run it... nothing.(frustration).  So I rebooted my computer and tried to boot into my internal hard drive "Can't locate the Selected operating system: Windows XP."  ](*,)(more frustration).  
I boot into a USB thinking I need to recover grub.  So I boot into terminal and try to recover the grub... 
```
sudo /sbin/grub
 command grub not found
locate *grub
/boot/grub
/etc/default/grub
/etc/kernel/postinst.d/zz-update-grub
/etc/kernel/postrm.d/zz-update-grub
/usr/lib/grub
/usr/lib/grub-legacy/update-grub
/usr/lib/linux-boot-probes/mounted/40grub
/usr/sbin/update-grub
/usr/share/grub
/usr/share/grub/default/grub
/usr/share/recovery-mode/options/grub
/var/lib/ucf/cache/:etc:default:grub

```No grub file in sbin... interesting. I go to look for my ubuntu partition and realize IT IS GONE ](*,)(punches concrete wall).  I have a dual boot with Win 7 and I can still access all of my windows on there, I just can't access Ubuntu.  

So I reboot loading into Ubuntu on my external. 

I go into Gparted and take a look at the drive.  
It says the entire drive is unallocated with the error message "Can't have overlapping partitions"  ](*,)

  


```

Sudo fdisk -l 

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e826c74

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1306    10485760   27  Unknown
/dev/sdb2   *        1306       16474   121833790    7  HPFS/NTFS
/dev/sdb3           16474       30402   111877121    5  Extended
/dev/sdb4           29830       30402     4589568   82  Linux swap / Solaris
/dev/sdb5           16474       29830   107287552   83  Linux

```What the hell happened?  What'd I do wrong? Is there any way I can save Ubuntu? fdisk still seems recognize that Ubuntu exists? Any help would be greatly appreciated... I'm in Haiti and have an ESL class to teach tomorrow and I need to have my computer functional :(

---

### Post by oldfred on 2011-03-29
Is sdb your internal or external.

I do not think windows works from an external drive. 

Post this to see your entire configuration.
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

If you want to try some things:
Backup partition table to text file and save elsewhere:
sudo sfdisk -d /dev/sda > PT.txt

Fixparts - Repair broken partition tables srs5694
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Fix overlaping partition error srs5694
[http://ubuntuforums.org/showthread.php?t=1667614](http://ubuntuforums.org/showthread.php?t=1667614)
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by Stop Being Such a TOONA on 2011-03-29
Thanks for the reply.  
Sorry I forgot to clarify it's my internal hard drive that is screwed.  So all the information above is from my internal.  

I'll take a look at those links and see if I can figure anything out.\

*NOTE: sda is my external.  [I]sdb is my internal hard drive.
[/I]NOTE2:I figured out how to get Ubuntu mounted.  Now I just need to figure out how to fix the overlapping partitions and recover grub2. 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /BOOTMGR /BOOT/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *          2,048    24,848,383    24,846,336  83 Linux
/dev/sda3         477,861,886   488,396,799    10,534,914   5 Extended
/dev/sda5         477,861,888   488,396,799    10,534,912  82 Linux swap / Solaris
/dev/sda4          24,848,384   477,859,839   453,011,456  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sdb2    *     20,973,568   264,641,147   243,667,580   7 HPFS/NTFS
/dev/sdb3         264,642,558   488,396,799   223,754,242   5 Extended
Extended  partition  linking to another extended partition
/dev/sdb5         264,642,560   479,217,663   214,575,104  83 Linux
/dev/sdb4         479,217,664   488,396,799     9,179,136  82 Linux swap / Solaris

/dev/sdb3 overlaps with /dev/sdb4

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        838b74f8-1e3f-48bc-ae14-6d49e0e7fb9d   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        70b4697b-a564-4397-815d-7c1a035acfea   ext3                                     
/dev/sda5        88d16060-4bde-4393-8386-6def13aeee8b   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FEEC40AEEC4062CF                       ntfs       PQSERVICE                     
/dev/sdb2        8A9EEDEC9EEDD12D                       ntfs       OS                            
/dev/sdb3: PTTYPE="dos" 
/dev/sdb4        cbf33c20-2ad6-44b7-8283-a65fd1c00f43   swap                                     
/dev/sdb5        feb53e31-0e8b-4c93-995f-9e9501c9c0bb   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda4        /media/70b4697b-a564-4397-815d-7c1a035acfea ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb5        /media/external          ext4       (rw)


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
search --no-floppy --fs-uuid --set 838b74f8-1e3f-48bc-ae14-6d49e0e7fb9d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 838b74f8-1e3f-48bc-ae14-6d49e0e7fb9d
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
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 838b74f8-1e3f-48bc-ae14-6d49e0e7fb9d
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=838b74f8-1e3f-48bc-ae14-6d49e0e7fb9d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 838b74f8-1e3f-48bc-ae14-6d49e0e7fb9d
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=838b74f8-1e3f-48bc-ae14-6d49e0e7fb9d ro single 
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
    search --no-floppy --fs-uuid --set 838b74f8-1e3f-48bc-ae14-6d49e0e7fb9d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 838b74f8-1e3f-48bc-ae14-6d49e0e7fb9d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set feec40aeec4062cf
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 8a9eedec9eedd12d
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set feb53e31-0e8b-4c93-995f-9e9501c9c0bb
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=feb53e31-0e8b-4c93-995f-9e9501c9c0bb ro
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set feb53e31-0e8b-4c93-995f-9e9501c9c0bb
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=feb53e31-0e8b-4c93-995f-9e9501c9c0bb ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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
# / was on /dev/sdc2 during installation
UUID=838b74f8-1e3f-48bc-ae14-6d49e0e7fb9d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=88d16060-4bde-4393-8386-6def13aeee8b none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


   9.1GB: boot/grub/core.img
   3.4GB: boot/grub/grub.cfg
    .4GB: boot/initrd.img-2.6.35-22-generic
   9.1GB: boot/vmlinuz-2.6.35-22-generic
    .4GB: initrd.img
   9.1GB: vmlinuz

================================ sdb2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(1)partition(2)\WINDOWS.0 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS.0="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set feb53e31-0e8b-4c93-995f-9e9501c9c0bb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set feb53e31-0e8b-4c93-995f-9e9501c9c0bb
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
    search --no-floppy --fs-uuid --set feb53e31-0e8b-4c93-995f-9e9501c9c0bb
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=feb53e31-0e8b-4c93-995f-9e9501c9c0bb ro   
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set feb53e31-0e8b-4c93-995f-9e9501c9c0bb
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=feb53e31-0e8b-4c93-995f-9e9501c9c0bb ro single 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set feb53e31-0e8b-4c93-995f-9e9501c9c0bb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set feb53e31-0e8b-4c93-995f-9e9501c9c0bb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set feec40aeec4062cf
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 8a9eedec9eedd12d
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=feb53e31-0e8b-4c93-995f-9e9501c9c0bb /               ext4     errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=cbf33c20-2ad6-44b7-8283-a65fd1c00f43 none            swap    sw              0       0

/dev/sdb1 /media/external ntfs-3g defaults,user,locale=en_US.utf8 0 0

=================== sdb5: Location of files loaded by Grub: ===================


 230.1GB: boot/grub/core.img
 234.6GB: boot/grub/grub.cfg
 145.4GB: boot/initrd.img-2.6.35-22-generic
 230.1GB: boot/vmlinuz-2.6.35-22-generic
 145.4GB: initrd.img
 230.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  49 b4 4a ad 2e a1 97 8a  b3 4f 5e 1d 4e 01 99 4a  |I.J......O^.N..J|
00000010  d7 64 fb 4c 72 a8 f6 15  26 a7 95 88 3a ba f3 1c  |.d.Lr...&...:...|
00000020  79 53 88 e8 e5 ab 55 7d  1f e5 6b bd 33 7c d7 9d  |yS....U}..k.3|..|
00000030  49 89 b8 3e d4 86 51 b7  22 3b 3a 9e 2d 10 df ad  |I..>..Q.";:.-...|
00000040  24 f0 7e 5b 57 19 09 c1  97 79 25 f5 75 a4 04 5d  |$.~[W....y%.u..]|
00000050  70 35 0a e9 22 58 66 0a  f0 b1 ec a4 30 92 11 37  |p5.."Xf.....0..7|
00000060  d1 2b 48 70 9b ef 0a 57  5e 5a 5b 52 23 50 a3 97  |.+Hp...W^Z[R#P..|
00000070  d5 3a b0 b7 ca 7a 7c 23  d3 bf 7a 9b 5c 95 0a aa  |.:...z|#..z.\...|
00000080  54 8c 71 06 b7 c6 a6 b4  c7 2b 53 14 a2 1a de 17  |T.q......+S.....|
00000090  b3 a6 63 13 45 7b d6 99  8f a3 ad b3 66 52 0b bb  |..c.E{......fR..|
000000a0  ac d5 46 03 29 b4 29 a9  d3 a1 1b 44 ba b8 02 2d  |..F.).)....D...-|
000000b0  b1 3d d6 e8 2f c8 c1 91  c7 a8 74 ed a4 e9 4f a3  |.=../.....t...O.|
000000c0  d0 42 03 2a ba df c5 9b  36 c4 fa 0f 52 5d a9 d7  |.B.*....6...R]..|
000000d0  63 ae 07 32 30 20 bc e9  83 37 3c e1 b2 e2 e8 a9  |c..20 ...7<.....|
000000e0  11 39 3d 8c 43 52 67 b8  35 fe dc 94 ab b0 c2 87  |.9=.CRg.5.......|
000000f0  5d 69 4d 09 3d 89 62 fe  a9 6a d8 98 a3 fb 72 02  |]iM.=.b..j....r.|
00000100  e7 8c 37 f4 2a 21 8c ce  1a 9f 4b bf 9a 7d 0f 6f  |..7.*!....K..}.o|
00000110  15 ac 2e e2 0b 66 d0 42  33 51 34 27 1d 30 9a 0d  |.....f.B3Q4'.0..|
00000120  2f 60 a6 2d ab 62 aa cf  92 49 e9 27 db 33 1d 3b  |/`.-.b...I.'.3.;|
00000130  a2 7b d7 3a d9 9c 20 60  38 83 aa fd 92 ca 71 c7  |.{.:.. `8.....q.|
00000140  30 f2 a1 06 e9 7d 48 fd  97 f6 36 ae 25 34 aa f7  |0....}H...6.%4..|
00000150  23 ee d6 38 bf a0 42 d8  50 39 2f f3 dd 17 91 2e  |#..8..B.P9/.....|
00000160  6b ea 00 42 2a 7d d8 1e  10 4a 8b a2 d3 ce f3 e2  |k..B*}...J......|
00000170  06 aa e9 79 57 de eb d2  b7 f8 85 7a 22 f3 16 33  |...yW......z"..3|
00000180  c9 b0 6d d7 2e 82 40 67  99 e4 e0 66 d1 fa 9c 6d  |..m...@g...f...m|
00000190  64 e7 de 16 49 77 50 ed  3b a9 19 44 fd 0c f5 79  |d...IwP.;..D...y|
000001a0  9f 58 92 62 69 c5 20 87  71 35 73 a9 e5 be 13 cd  |.X.bi. .q5s.....|
000001b0  ae 3a 55 f6 a4 b9 0b c5  cf 64 4c a4 8c fd 00 fe  |.:U......dL.....|
000001c0  ff ff 05 fe ff ff 01 00  00 00 01 28 ca 0c 00 00  |...........(....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2011-03-29
I think fixparts program will resolve your problem:

Extended  partition  linking to another extended partition

/dev/sdb3 overlaps with /dev/sdb4


You cannot have a primary partition sdb4 inside the extended partiiton sdb3. Either the extended partition end has to be the same end as sdb5 or sdb4 should be just sdb6. Either change is just an edit to partition table, but it is not always easy to calculate starts & ends correctly.

Did you use any windows partitioning tools. We have seen some issues like this with some windows tools.

---

### Post by srs5694 on 2011-03-29
Your /dev/sdb disk has a primary partition located within an extended partition. This is illegal, and is a problem that the Windows XP installer is known to create under certain circumstances. Thus, in answer to your earlier question, "what'd I do wrong," the answer is either "nothing -- the Microsoft programmers screwed up" or "you installed Windows XP," depending on your point of view.

In any event, my [FixParts](http://www.rodsbooks.com/fixparts/) program will fix this problem; or you can use sfdisk to do the job by typing "sudo sfdisk -d /dev/sdb > parts.txt", editing parts.txt to make it legal, and then typing "sudo sfdisk -f /dev/sdb < parts.txt". If you use FixParts, you should be able to simply launch the program, type "p" to verify that the partitions are OK, and then save the partition table by typing "w". The result will be slightly neater, however, if you use the "l" (that's a letter "L") option to change the type of partition #4 (your Linux swap partition) from primary to logical before you save your changes. That said, there are a few other issues, or at least potential issues....

First, I noticed this in the Boot Info Script output:

```

Extended  partition  linking to another extended partition

```

I'm not 100% sure what this means, although I might have an idea. If I'm right, FixParts and fdisk (and probably sfdisk) will handle it fine. If not, then it could be a sign of a more serious problem. I don't see signs of any suspicious gaps between the partitions you do have defined, so I don't think anything's missing, but I could be wrong. In any event, if you use either FixParts or sfdisk to repair the problem, you should be sure that whatever you write includes all five of the partitions you've got now. (FixParts will show only four partitions, since it ignores the extended partition and then creates a new extended partition.)

Another issue is that your GRUB configuration includes references to partitions by number, as in:

```

set root='(hd0,msdos6)'

```

Some of these numbers may need to be changed when you fix your partition table. I'm not sure offhand if GRUB's hd0 is Linux's /dev/sda or /dev/sdb in your configuration, but given other clues, I suspect hd0 is /dev/sdb. If so, you'll probably have to change references to (hd0,msdos6) to (hd0,msdos5) if you fix the problem with FixParts, and perhaps if you use sfdisk (details depend on what you do with sfdisk).

There may be other GRUB configuration issues, too; I haven't scrutinized every line of the GRUB output to see what else might be wrong.

Note that messing with partition tables is inherently risky, no matter how you do it. You'd do well to back up your partition tables with sfdisk before you proceed:

```

sudo sfdisk -d > parts.txt

```

Save the parts.txt file to a USB flash drive, CD-R, or some other medium other than the one you're modifying. It will then serve as insurance; if something goes badly wrong, you can restore your partitions to their current state to try again.

---

### Post by Stop Being Such a TOONA on 2011-03-31
So I've recovered grub properly and now can boot into ubuntu no problem. But I'm still not able to boot into Windows 7.  It still keeps trying to boot into my non-existent version of xp. 
```
 sudo fdisk -l
Disk /dev/sda: 250 GB, 250056737280 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1        1306    10490413   27  (null)
Warning: Partition 1 does not end on cylinder boundary.
/dev/sda2            1306       16474   121836960    7  HPFS/NTFS
Warning: Partition 2 does not end on cylinder boundary.
/dev/sda3           16474       29830   107282070    f  Extended LBA
Warning: Partition 3 does not end on cylinder boundary.
/dev/sda5   *       16474       29830   107282070   83  Linux
Warning: Partition 5 does not end on cylinder boundary.
/dev/sda4           29830       30402     4594590   82  Linux swap
Warning: Partition 4 does not end on cylinder boundary.

```
I'm confused why my harddrive partitions were sdb before and now they're sda...  
Also why are my drives now labeled as (h0,msdos1) instead of (h0,1)? 
Any ideas how I can make fix grub so I can boot into Windows 7 properly?

---

### Post by srs5694 on 2011-03-31
> **Stop Being Such a TOONA said:**
> So I've recovered grub properly and now can boot into ubuntu no problem. But I'm still not able to boot into Windows 7.  It still keeps trying to boot into my non-existent version of xp.

GRUB may have misidentified the OS as Windows XP when in fact it's Windows 7. If so, that by itself is not a problem. Thus, if you're seeing a "Windows XP" entry in GRUB and you haven't already done so, try it. If it boots Windows 7, then my recommendation is to just ignore the misidentification. If you try the "Windows XP" entry in GRUB and it doesn't boot, you'll need to provide more details. I recommend running the Boot Info Script again and posting the results again (since things have clearly changed since the last time you posted those results). You could also try running "sudo update-grub" to update your GRUB configuration. If you do this, test it and, if it doesn't work, post the Boot Info Script output from *after* you run update-grub.

> I'm confused why my harddrive partitions were sdb before and now they're sda...

This can change from one boot to the next or because of changes in BIOS settings, drivers, etc. Don't worry about it -- but be very careful when you access the disks by device filename, in case a change occurs that might lead you to do something inappropriate to a disk!

> Also why are my drives now labeled as (h0,msdos1) instead of (h0,1)?

This is a recent change in GRUB. The "msdos" part clearly identifies the partitioning system as being the Master Boot Record (MBR), aka "msdos," as opposed to the newer GUID Partition Table (GPT) or some other system.

---

### Post by Stop Being Such a TOONA on 2011-03-31
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /BOOTMGR /BOOT/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb3 and 
                       looks at sector 1 of the same hard drive for core.img, 
                       but core.img can not be found at this location.

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1024 MB, 1024966656 bytes
32 heads, 62 sectors/track, 1009 cylinders, total 2001888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             62     2,001,855     2,001,794   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sdb2          20,973,568   264,641,147   243,667,580   7 HPFS/NTFS
/dev/sdb3         264,642,559   479,217,663   214,575,105   f W95 Ext d (LBA)
/dev/sdb5    *    264,642,560   479,217,663   214,575,104  83 Linux
/dev/sdb4         479,217,664   488,396,799     9,179,136  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       e5294ec0-19e3-4aaa-beed-397c1fde3b80   ext3                                     
/dev/sda1        3EB5-BBD7                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FEEC40AEEC4062CF                       ntfs       PQSERVICE                     
/dev/sdb2        8A9EEDEC9EEDD12D                       ntfs       OS                            
/dev/sdb3: PTTYPE="dos" 
/dev/sdb4        cbf33c20-2ad6-44b7-8283-a65fd1c00f43   swap                                     
/dev/sdb5        feb53e31-0e8b-4c93-995f-9e9501c9c0bb   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdb2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(1)partition(2)\WINDOWS.0 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS.0="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set feb53e31-0e8b-4c93-995f-9e9501c9c0bb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set feb53e31-0e8b-4c93-995f-9e9501c9c0bb
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set feb53e31-0e8b-4c93-995f-9e9501c9c0bb
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=feb53e31-0e8b-4c93-995f-9e9501c9c0bb ro   
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set feb53e31-0e8b-4c93-995f-9e9501c9c0bb
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=feb53e31-0e8b-4c93-995f-9e9501c9c0bb ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set feb53e31-0e8b-4c93-995f-9e9501c9c0bb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set feb53e31-0e8b-4c93-995f-9e9501c9c0bb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set feec40aeec4062cf
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 8a9eedec9eedd12d
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
/dev/sdb4       /        ext4     errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
/dev/sdb5      swap      swap 0 0        

/dev/sdb /media ntfs-3g defaults,auto,locale=en_US.utf8 0 0

=================== sdb5: Location of files loaded by Grub: ===================


 230.1GB: boot/grub/core.img
 234.7GB: boot/grub/grub.cfg
 145.4GB: boot/initrd.img-2.6.35-22-generic
 230.1GB: boot/vmlinuz-2.6.35-22-generic
 145.4GB: initrd.img
 230.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 20 00 00 00 00 00  |........>. .....|
00000020  82 8b 1e 00 a0 07 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 d7 bb b5 3e 20  20 20 20 20 20 20 20 20  |..)...>         |
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
00000100  7d 00 66 b8 40 b7 15 00  66 ba 00 00 00 00 bb 00  |}.f.@...f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e cd c2 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
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

### Post by oldfred on 2011-03-31
Your 1GB flash drive is promoted to sda. Some systems do that and cause confusion. Have you tried booting without it? Then the sdb will be sda. That may solve the windows issues. (but you should still move boot flag., see below). Ubuntu uses UUID to override any set root that has the wrong drive.

If the drive is now sdb and it was sda, that may confuse windows. You  can see the boot.ini from XP says drive 1, but we do not see the BCD  data which probably also says drive1 not drive0. If it is now drive0  windows will have problems.
multi(0)disk(0)rdisk([COLOR=Red]1[/COLOR])partition(2)


Grub does not use the boot flag, but windows has to have the boot flag on the boot partition for both booting and for repairs by a windows CD. So you need to move boot flag back to sda2 (sdb2?). Your sda1(sdb1?) says it is a PQSERVICE partition, but it has the full install files and looks larger than a normal recovery. Do you have two full installs of Windows? If so you need to move boot flag to each one at a time and run windows repairs.

---

### Post by Stop Being Such a TOONA on 2011-04-03
Thanks so much for your help!

I've got everything up and running again.  I downloaded a WIN7 recovery CD and repaired the MBR then went in with a live boot and reinstalled grub.

---

