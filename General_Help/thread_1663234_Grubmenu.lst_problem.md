---
title: "Grub/menu.lst problem"
date: 2011-01-09
forum: General Help
---

### Post by electronictim on 2011-01-09
Hi all.
I'm sorry to have to post this...I realise these forums are littered with similar threads...I've read most of them (I think) and followed advice, but can't for the life of me get it to work, so here it is:

Recently installed lubuntu on a partition of a computer with XP already installed.

Now I can't get XP to show up as an option on the grub menu.

Here's the partition structure:
___________________________________

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         912     7325608+  12  Compaq diagnostics
/dev/sda2   *         913        4560    29302560    7  HPFS/NTFS
/dev/sda3            4561        6019    11717633    5  Extended
/dev/sda4            6019       30402   195851264    7  HPFS/NTFS
/dev/sda5            4561        4804     1952768   82  Linux swap / Solaris
/dev/sda6            4804        5411     4881408   83  Linux
/dev/sda7            5412        6019     4881408   83  Linux

Disk /dev/sdb: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         976     7839698    b  W95 FAT32

________________________________

And here's (the most recent incarnation of) the bottom of my menu.lst:
____________________________________

## ## End Default Options ##

title		Ubuntu 10.10, kernel 2.6.35-24-generic
uuid		b717377d-4588-4329-92b2-bb45934729b8
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=b717377d-4588-4329-92b2-bb45934729b8 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid		b717377d-4588-4329-92b2-bb45934729b8
kernel		/boot/vmlinuz-2.6.35-24-generic root=UUID=b717377d-4588-4329-92b2-bb45934729b8 ro  single
initrd		/boot/initrd.img-2.6.35-24-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic
uuid		b717377d-4588-4329-92b2-bb45934729b8
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=b717377d-4588-4329-92b2-bb45934729b8 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-22-generic

title		Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid		b717377d-4588-4329-92b2-bb45934729b8
kernel		/boot/vmlinuz-2.6.35-22-generic root=UUID=b717377d-4588-4329-92b2-bb45934729b8 ro  single
initrd		/boot/initrd.img-2.6.35-22-generic

title		Chainload into GRUB 2
root		b717377d-4588-4329-92b2-bb45934729b8
kernel		/boot/grub/core.img

title		Ubuntu 10.10, memtest86+
uuid		b717377d-4588-4329-92b2-bb45934729b8
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows XP
root		(hd0,1)
makeactive
chainloader	+1

____________________________________-

All I get when I boot up are the 4 Ubuntu options + 2 memory tests.....

Please help!

---

### Post by oldfred on 2011-01-09
Welcome to the forums.

What version of Ubuntu did you install? Grub legacy has not been the default since 9.04.

Grub legacy was not as good at finding other installs as the osprober in grub2.

Post this so we can see your entire configuration.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by tredegar on 2011-01-09
It looks like you have 'buntu 10.10 installed.
If you can boot to it, then in a terminal:

```
sudo grub-install /dev/sda
sudo update-grub
sudo reboot
```
and all should be well, with windows bootable again.

If you can't boot to 10.10 you'll need a live CD (anything >=9.10) and follow [this thread]("http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html")

---

### Post by electronictim on 2011-01-09
Thanks for the reply.
I installed lubuntu 10.04 (the most recent).
Here are the resuts:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda4 starts at sector 96692224.
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

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    14,651,279    14,651,217  12 Compaq diagnostics
/dev/sda2    *     14,651,280    73,256,399    58,605,120   7 HPFS/NTFS
/dev/sda3          73,256,958    96,692,223    23,435,266   5 Extended
/dev/sda5          73,256,960    77,162,495     3,905,536  82 Linux swap / Solaris
/dev/sda6          77,164,544    86,927,359     9,762,816  83 Linux
/dev/sda7          86,929,408    96,692,223     9,762,816  83 Linux
/dev/sda4          96,692,224   488,394,751   391,702,528   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             44    15,679,439    15,679,396   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        488C2F4C8C2F343A                       ntfs       Recovery Partition            
/dev/sda2        9CBCE02BBCDFFDA0                       ntfs       VAIO                          
/dev/sda3: PTTYPE="dos" 
/dev/sda4        BDC9-1E2D                              vfat       Commons                       
/dev/sda5        580fa113-ea74-4c0a-952f-7c9f022e76b4   swap                                     
/dev/sda6        b717377d-4588-4329-92b2-bb45934729b8   ext3                                     
/dev/sda7        dc90daea-6318-41a9-8f41-52b208e95648   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C44B-8D37                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext3       (rw,commit=0)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptOut 
c:\plpbtldr.bin="Start PLoP Boot Manager" 

=========================== sda6/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b717377d-4588-4329-92b2-bb45934729b8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b717377d-4588-4329-92b2-bb45934729b8

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 10.10, kernel 2.6.35-24-generic
uuid        b717377d-4588-4329-92b2-bb45934729b8
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=b717377d-4588-4329-92b2-bb45934729b8 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-24-generic

title        Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
uuid        b717377d-4588-4329-92b2-bb45934729b8
kernel        /boot/vmlinuz-2.6.35-24-generic root=UUID=b717377d-4588-4329-92b2-bb45934729b8 ro  single
initrd        /boot/initrd.img-2.6.35-24-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic
uuid        b717377d-4588-4329-92b2-bb45934729b8
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=b717377d-4588-4329-92b2-bb45934729b8 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid        b717377d-4588-4329-92b2-bb45934729b8
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=b717377d-4588-4329-92b2-bb45934729b8 ro  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Chainload into GRUB 2
root        b717377d-4588-4329-92b2-bb45934729b8
kernel        /boot/grub/core.img

title        Ubuntu 10.10, memtest86+
uuid        b717377d-4588-4329-92b2-bb45934729b8
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Windows XP
root        (hd0,1)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader    +1



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
search --no-floppy --fs-uuid --set b717377d-4588-4329-92b2-bb45934729b8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set b717377d-4588-4329-92b2-bb45934729b8
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set b717377d-4588-4329-92b2-bb45934729b8
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=b717377d-4588-4329-92b2-bb45934729b8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set b717377d-4588-4329-92b2-bb45934729b8
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=b717377d-4588-4329-92b2-bb45934729b8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set b717377d-4588-4329-92b2-bb45934729b8
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b717377d-4588-4329-92b2-bb45934729b8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set b717377d-4588-4329-92b2-bb45934729b8
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b717377d-4588-4329-92b2-bb45934729b8 ro single 
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
    search --no-floppy --fs-uuid --set b717377d-4588-4329-92b2-bb45934729b8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set b717377d-4588-4329-92b2-bb45934729b8
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
UUID=b717377d-4588-4329-92b2-bb45934729b8 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=dc90daea-6318-41a9-8f41-52b208e95648 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=580fa113-ea74-4c0a-952f-7c9f022e76b4 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  40.7GB: boot/grub/core.img
  40.6GB: boot/grub/grub.cfg
  40.6GB: boot/grub/menu.lst
  40.6GB: boot/initrd.img-2.6.35-22-generic
  40.6GB: boot/initrd.img-2.6.35-24-generic
  40.6GB: boot/vmlinuz-2.6.35-22-generic
  40.6GB: boot/vmlinuz-2.6.35-24-generic
  40.6GB: initrd.img
  40.6GB: initrd.img.old
  40.6GB: vmlinuz
  40.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 22 00  |.X.SYSLINUX...".|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 2c 00 00 00  |........?...,...|
00000020  a4 3f ef 00 b3 3b 00 00  00 00 00 00 02 00 00 00  |.?...;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 37 8d 4b c4 4e  4f 20 4e 41 4d 45 20 20  |..)7.K.NO NAME  |
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
00000100  7d 00 66 b8 90 77 00 00  66 ba 00 00 00 00 bb 00  |}.f..w..f.......|
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

### Post by electronictim on 2011-01-09
Thanks tredegar.
Did what you said - I get the grub menu (after pressing esc - by the way - can i increase the time i get to do so somehow?), select Windows, but then a message saying 'Starting up' and a flashing cursor...nothing more.

---

### Post by tredegar on 2011-01-09
OK, grub2 is installed & working.
Windows is now listed but not booting - I don't run win, so can't really help you here, sorry.

However, it might be worth trying to mount your windows partition and see if you can see your files though: Look under "Places", it'll be something like xxGB Filesystem, or maybe even named correctly. Check all the entries till you find what looks like windows. If you can find your important files, rescue them to an external HDD now. (Hopefully you took a backup before you started playing with linux)

To increase the timeout, and configure a lot of other things you need to edit **/etc/default/grub** and then re-run **sudu update-grub**

Details of what to edit and how are [here]("https://help.ubuntu.com/community/Grub2")
Scroll down to (Search for) GRUB_TIMEOUT if that is all you are interested in.

As for win failing to boot, may I suggest you start another thread to solve that problem?

Good luck & best wishes.

---

### Post by oldfred on 2011-01-09
Grub & grub2 often do not get along. I would suggest to cleanly uninstall both & reinstall grub2. Note that while uninstalled you could not boot, so you have to complete the reinstall.

# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

In your results.txt windows partition looks ok. Sometimes you have to run windows repairs. It can be just chkdsk or fixboot.

XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)


Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini

COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.

---

### Post by perspectoff on 2011-01-09
May or may not be the problem, but worth checking:

Using GParted, make sure the "boot" flag for /dev/sda2 was not erased by accident.

The bootable Windows NTFS partition must have a boot flag set.

BTW, are you sure you aren't just impatient with XP now that you've become used to the speed of Ubuntu (lol) ?

---

### Post by electronictim on 2011-01-09
Amazing.  Thanks so much for your help people.  Seems the problem was indeed caused by some sort of bun-fight between Grub and Son of Grub.  I followed oldfred's instructions and all is now well.

PS. Perpectoff - Thanks for the Gparted tip.  The flag was still in place though.  I did wonder whether it was merely a matter of expectation, so went to make myself an extravagant sandwich while XP was trying to boot just to be double-sure....

---

### Post by oldfred on 2011-01-09
Glad it is working.

We sometimes call those kind of sandwiches Dagwoods after the comic strip as he makes monster sandwiches all the time.

---

