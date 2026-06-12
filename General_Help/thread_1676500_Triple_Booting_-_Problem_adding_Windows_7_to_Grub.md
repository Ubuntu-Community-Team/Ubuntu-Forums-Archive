---
title: "Triple Booting - Problem adding Windows 7 to Grub"
date: 2011-01-27
forum: General Help
---

### Post by shokkapic on 2011-01-27
Dear Ubuntu Community,

I'm trying to triple boot Ubuntu, Mac OSX and Windows 7.

I have two HDD, with the following partitions:
HDD 0 >  Partition 1 = Windows 7
            >  Partition 2 = Partition to store documents

HDD 1 > Partition 1 = Mac OSX
            > Rest = Ubuntu and its swap partitions, etc.

I run update-grub but Windows 7 wasn't detected (Ubuntu and Mac OSX were, and are displayed at the boot list).

I've added a new file to /etc/grub.d called 06_windows, with the contents:
```
#! /bin/sh -e
echo “Adding Windows” >&2
cat << EOF
menuentry “Windows 7&#8243; {
set root=(hd0,1)
chainloader +1
}
EOF
```I wrote chmod a+x 06_windows and then update-grub:
```
Generating grub.cfg ...
“Adding Windows”
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found Mac OS X on /dev/sdb2
Found memtest86+ image: /boot/memtest86+.bin
done

```When I rebooted the laptop, there was no entry called Windows 7. I then booted Ubuntu, normally, and the following message appeared:
```
**udevd-work[96]: '/sbin/blkid -o udev -p /dev/sda1' unexpected exit with status 0x000b**
```Ubuntu booted without further problems, but my sda1 partition isn't mounted (the one that boots Windows 7). The others are.

fdisk -l shows:
```
pedro@Pedro-Linux:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 250.1 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x67540756

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16227   122672131    7  HPFS/NTFS
/dev/sda2           16227       32302   121522176    7  HPFS/NTFS

```Also, I tried to find out the UUID of the sda1 partition, but
```
sudo blkid
``` throws a "Segmentation Fault" error at terminal.


Any help is very appreciated. :)

---

### Post by Mark Phelps on 2011-01-27
Have you tried running Win7 since then and confirmed that it still works OK?  I would do that first.  Then, run chkdsk against the Win7 partition to rule out any filesystem corruption.

After that, try "sudo update-grub" again in Ubuntu.

I have encountered problems myself where the OS prober does NOT show the other OS's when update-grub is run, but checking the grub.cfg file afterward DOES show the added entries.

---

### Post by shokkapic on 2011-01-27
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,gpt6)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 40.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb5: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   245,344,324   245,344,262   7 HPFS/NTFS
/dev/sda2         245,348,352   488,392,703   243,044,352   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1   488,397,167   488,397,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              40       409,639       409,600 System/Boot Partition
/dev/sdb2         409,640   195,722,143   195,312,504 HFS+
/dev/sdb4     391,294,976   488,134,983    96,840,008 HFS+
/dev/sdb5     196,052,992   196,055,039         2,048 Bios Boot Partition
/dev/sdb6     196,055,040   383,266,815   187,211,776 Linux or Data
/dev/sdb7     383,266,816   391,294,975     8,028,160 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        82D295FED295F69F                       ntfs       DOCUMENTOS                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        70D6-1701                              vfat       EFI                           
/dev/sdb2        df600f5b-a797-3997-8a92-f68df51723e1   hfsplus    HDD                           
/dev/sdb4        a3eaedb9-7ee5-3f1a-bcdb-42e9ec1aa65e   hfsplus    Backup HDD                    
/dev/sdb6        984ba0b7-6eb7-4cad-bfe1-2be02ab9eed6   ext4                                     
/dev/sdb7        464721b5-e3fe-449d-b9a9-964486d44e74   swap                                     
/dev/sdb: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb2        /media/HDD               hfsplus    (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb6/boot/grub/grub.cfg: ===========================

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

insmod part_gpt
insmod ext2
set root='(hd1,gpt6)'
search --no-floppy --fs-uuid --set 984ba0b7-6eb7-4cad-bfe1-2be02ab9eed6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(hd1,gpt6)'
search --no-floppy --fs-uuid --set 984ba0b7-6eb7-4cad-bfe1-2be02ab9eed6
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

### BEGIN /etc/grub.d/10_windows ###
menuentry &#8220;Windows 7&#8243; {
set root=(hd0,1)
chainloader +1
}
### END /etc/grub.d/10_windows ###

### BEGIN /etc/grub.d/15_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt6)'
    search --no-floppy --fs-uuid --set 984ba0b7-6eb7-4cad-bfe1-2be02ab9eed6
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=984ba0b7-6eb7-4cad-bfe1-2be02ab9eed6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt6)'
    search --no-floppy --fs-uuid --set 984ba0b7-6eb7-4cad-bfe1-2be02ab9eed6
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=984ba0b7-6eb7-4cad-bfe1-2be02ab9eed6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
### END /etc/grub.d/15_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sdb2)" {
    insmod part_gpt
    insmod hfsplus
    set root='(hd1,gpt2)'
    search --no-floppy --fs-uuid --set 998b6d0568b9f7ca
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 998b6d0568b9f7ca uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sdb2)" {
    insmod part_gpt
    insmod hfsplus
    set root='(hd1,gpt2)'
    search --no-floppy --fs-uuid --set 998b6d0568b9f7ca
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 998b6d0568b9f7ca uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/31_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt6)'
    search --no-floppy --fs-uuid --set 984ba0b7-6eb7-4cad-bfe1-2be02ab9eed6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd1,gpt6)'
    search --no-floppy --fs-uuid --set 984ba0b7-6eb7-4cad-bfe1-2be02ab9eed6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/31_memtest86+ ###

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
UUID=984ba0b7-6eb7-4cad-bfe1-2be02ab9eed6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=464721b5-e3fe-449d-b9a9-964486d44e74 none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


 154.2GB: boot/grub/core.img
 139.3GB: boot/grub/grub.cfg
 102.2GB: boot/initrd.img-2.6.35-24-generic
 154.2GB: boot/vmlinuz-2.6.35-24-generic
 102.2GB: initrd.img
 154.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e d8 8e c0 56 be 00  |.1...........V..|
00000010  7c bf 00 e0 fc b9 00 02  f3 a4 5e 68 1f e0 c3 66  ||.........^h...f|
00000020  8b 44 08 66 a3 00 e6 88  16 04 e6 c7 06 0a e6 00  |.D.f............|
00000030  10 66 31 c9 66 41 b0 02  66 ba 00 e2 00 00 e8 a3  |.f1.fA..f.......|
00000040  00 66 a1 28 e4 66 0f c8  66 c1 e8 09 66 a3 06 e6  |.f.(.f..f...f...|
00000050  a1 00 e4 3d 48 58 74 05  3d 48 2b 75 58 b0 04 8d  |...=HXt.=H+uX...|
00000060  36 ed e3 8d 3e 20 e5 e8  96 01 75 49 8d b6 1d 01  |6...> ....uI....|
00000070  8b 34 81 3c 00 02 75 3d  66 8b 5c 5c 66 0f cb 66  |.4.<..u=f.\\f..f|
00000080  81 c3 ff 01 00 00 66 c1  eb 09 81 fb 7f 03 77 25  |......f.......w%|
00000090  66 8b 44 08 66 0f c8 66  31 c9 66 ba 00 02 02 00  |f.D.f..f1.f.....|
000000a0  8d 7c 68 e8 4e 02 bf f0  e1 e8 6d 00 8a 16 04 e6  |.|h.N.....m.....|
000000b0  ea 00 02 00 20 bf e7 e3  e8 5e 00 f4 eb fd 66 60  |.... ....^....f`|
000000c0  89 c3 66 31 c0 88 d8 81  fb 40 00 72 02 b0 40 e8  |..f1.....@.r..@.|
000000d0  12 00 29 c3 74 0b 66 01  c1 c1 e0 09 66 01 c2 eb  |..).t.f.....f...|
000000e0  e1 66 61 c3 66 60 06 89  e5 89 d3 80 e7 0f 66 c1  |.fa.f`........f.|
000000f0  ea 04 30 d2 8e c2 1e 1e  66 03 0e 00 e6 66 51 06  |..0.....f....fQ.|
00000100  53 30 e4 50 68 10 00 8a  16 04 e6 89 e6 b4 42 cd  |S0.Ph.........B.|
00000110  13 72 a2 89 ec 07 66 61  c3 66 60 57 be dd e3 e8  |.r....fa.f`W....|
00000120  07 00 5e e8 03 00 66 61  c3 bb 01 00 ac 3c 00 74  |..^...fa.....<.t|
00000130  06 b4 0e cd 10 eb f5 c3  66 60 ad 86 e0 ab 3c 00  |........f`....<.|
00000140  74 23 89 c1 ad 86 e0 80  3e 01 e4 58 74 14 09 c0  |t#......>..Xt...|
00000150  75 01 48 80 fc 00 77 0a  3c 41 72 06 3c 5a 77 02  |u.H...w.<Ar.<Zw.|
00000160  04 20 ab e2 df 66 61 c3  66 60 b2 00 66 8b 44 02  |. ...fa.f`..f.D.|
00000170  66 3b 45 02 75 0f 80 3c  00 75 0a 66 8b 44 06 66  |f;E.u..<.u.f.D.f|
00000180  3b 45 06 74 48 77 44 72  3d 66 60 31 d2 87 f7 66  |;E.tHwDr=f`1...f|
00000190  ad 66 89 c1 87 f7 66 ad  66 39 c8 77 2e 72 27 87  |.f....f.f9.w.r'.|
000001a0  f7 ad 89 c1 87 f7 ad 80  f9 00 74 1f 39 c8 74 0b  |..........t.9.t.|
000001b0  77 07 fe ce 89 c1 e9 02  00 fe c6 f3 a7 77 0c 72  |w............w.r|
000001c0  05 88 f2 e9 07 00 fe ca  e9 02 00 fe c2 88 96 14  |................|
000001d0  00 80 fa 00 66 61 c3 50  57 8b 3e 0a e6 57 47 47  |....fa.PW.>..WGG|
000001e0  49 49 b0 00 f3 aa 89 3e  0a e6 5d 89 2d 5f 58 c3  |II.....>..].-_X.|
000001f0  2f 62 6f 6f 74 00 00 00  00 00 00 00 00 00 55 aa  |/boot.........U.|
00000200


```Windows 7 boots fine. I'll run chkdsk now.
Though "Windows 7" entry appears at grub.cfg, it doesn't appear on the Boot Menu. I can only launch Windows 7 through a Chameleon DVD I have here.

---

### Post by shokkapic on 2011-01-27
CHKDKS showed no errors.

If I try to
```
sudo mount dev/sda1 /mnt/win7
``` it displays a "Segmentation Fault" error.

---

