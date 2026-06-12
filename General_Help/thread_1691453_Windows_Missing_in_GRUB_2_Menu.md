---
title: "Windows Missing in GRUB 2 Menu"
date: 2011-02-19
forum: General Help
---

### Post by nabilalk on 2011-02-19
Hey all, I followed instructions [here]("http://ubuntuforums.org/showpost.php?p=8293207&postcount=2") to restore Grub2 and get Win 7 back in the Grub2 menu. After completing the commands I got the an error: > Cannot find list of partitions!

```
ubuntu@ubuntu:~$ sudo bash # DANGEROUS! ENTER COMMANDS EXACTLY!
root@ubuntu:~# mount /dev/sda1 /mnt
root@ubuntu:~# mount -o bind /proc /mnt/proc
root@ubuntu:~# mount -o bind /dev /mnt/dev
root@ubuntu:~# chroot /mnt bash
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-020632-generic
Found initrd image: /boot/initrd.img-2.6.32-020632-generic
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/# exit
exit
root@ubuntu:~# exit

```

performing sudo update-grub2 yields > error: cannot find a device for / (is /dev mounted?).
```
ubuntu@ubuntu:~$ sudo update-grub2
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```

**fsdisk output for reference**
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x70fcf334

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1370    11004493+  83  Linux
/dev/sda2   *        1371        1383      102400    7  HPFS/NTFS
/dev/sda3            1383        6669    42461184    7  HPFS/NTFS
/dev/sda4            6670       19457   102719610    5  Extended
/dev/sda5            6670       19264   101169306    b  W95 FAT32
/dev/sda6           19265       19457     1550241   82  Linux swap / Solaris

Disk /dev/sdb: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         984     7896064    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(982, 254, 63) logical=(983, 36, 13)

```

Grub2 menu lists my Ubuntu install but not Windows 7. 
Where do I go from here? Many thanks.:guitar:

---

### Post by wilee-nilee on 2011-02-19
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by nabilalk on 2011-02-19
Grub2 is not detecting the Windows partition. I can't boot into Windows. I even tried to repair MBR via a Windows repair disk, but that didn't work either. Here is the output requested. Can't I just manually edit the grub.cfg file and add entries for Windows?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 16306783 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Fat32
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 107137548.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    22,009,049    22,008,987  83 Linux
/dev/sda2    *     22,009,856    22,214,655       204,800   7 HPFS/NTFS
/dev/sda3          22,214,656   107,137,023    84,922,368   7 HPFS/NTFS
/dev/sda4         107,137,485   312,576,704   205,439,220   5 Extended
/dev/sda5         107,137,548   309,476,159   202,338,612   b W95 FAT32
/dev/sda6         309,476,223   312,576,704     3,100,482  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    15,794,175    15,792,128   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              iso9660    Ubuntu 10.10 i386             
/dev/loop1                                              squashfs                                 
/dev/sda1        1ace6a67-4ba1-41f5-a460-d54fc7aa988d   ext3                                     
/dev/sda2: ambivalent result (probably more filesystems on the device, use wipefs(8) to see more details)
/dev/sda3        EED83904D838CD19                       ntfs                                     
/dev/sda5        B86D-1BC9                              vfat       DRIVE_HARD                    
/dev/sda6        e606560f-33bc-4041-b16a-747aa62fe75a   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        18F1-1375                              vfat       MULTIBOOT                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /isodevice               vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /cdrom                   iso9660    (ro,noatime)
/dev/loop1       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/1ace6a67-4ba1-41f5-a460-d54fc7aa988d ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/sda1              ext3       (rw)
/dev/sda1        /mnt                     ext3       (rw)
/dev             /mnt/dev                 none       (rw,bind)
/dev/sda5        /media/DRIVE_HARD        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda3        /media/EED83904D838CD19  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=1ace6a67-4ba1-41f5-a460-d54fc7aa988d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1ace6a67-4ba1-41f5-a460-d54fc7aa988d

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

title        Chainload into GRUB 2
uuid        1ace6a67-4ba1-41f5-a460-d54fc7aa988d
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        1ace6a67-4ba1-41f5-a460-d54fc7aa988d
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=1ace6a67-4ba1-41f5-a460-d54fc7aa988d ro quiet splash
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        1ace6a67-4ba1-41f5-a460-d54fc7aa988d
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=1ace6a67-4ba1-41f5-a460-d54fc7aa988d ro single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.28-13-generic
uuid        1ace6a67-4ba1-41f5-a460-d54fc7aa988d
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=1ace6a67-4ba1-41f5-a460-d54fc7aa988d ro quiet splash
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-13-generic (recovery mode)
uuid        1ace6a67-4ba1-41f5-a460-d54fc7aa988d
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=1ace6a67-4ba1-41f5-a460-d54fc7aa988d ro single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.10, memtest86+
uuid        1ace6a67-4ba1-41f5-a460-d54fc7aa988d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows 7 (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set default="${saved_entry}"
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 1ace6a67-4ba1-41f5-a460-d54fc7aa988d
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 1ace6a67-4ba1-41f5-a460-d54fc7aa988d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-020632-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1ace6a67-4ba1-41f5-a460-d54fc7aa988d
    linux    /boot/vmlinuz-2.6.32-020632-generic root=UUID=1ace6a67-4ba1-41f5-a460-d54fc7aa988d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-020632-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-020632-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1ace6a67-4ba1-41f5-a460-d54fc7aa988d
    echo    'Loading Linux 2.6.32-020632-generic ...'
    linux    /boot/vmlinuz-2.6.32-020632-generic root=UUID=1ace6a67-4ba1-41f5-a460-d54fc7aa988d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-020632-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1ace6a67-4ba1-41f5-a460-d54fc7aa988d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1ace6a67-4ba1-41f5-a460-d54fc7aa988d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                        /proc          proc         defaults                                     0  0  
# / was on /dev/sda1 during installation
UUID=1ace6a67-4ba1-41f5-a460-d54fc7aa988d   /              ext3         relatime,errors=remount-ro                   0  1  
 dev/sda2    swap            swap        defaults            0    0
/dev/scd0                                   /media/cdrom0  udf,iso9660  user,noauto,exec,utf8                        0  0  
/dev/sda5                                   /media/sda5    vfat         uid=1000,gid=1000,users,dmask=027,fmask=137  0  0  


=================== sda1: Location of files loaded by Grub: ===================


   8.3GB: boot/grub/core.img
   8.4GB: boot/grub/grub.cfg
   8.4GB: boot/grub/menu.lst
   8.4GB: boot/initrd.img-2.6.32-020632-generic
   8.4GB: boot/vmlinuz-2.6.32-020632-generic
   8.4GB: initrd.img.old
   8.4GB: vmlinuz.old

================================ sdb1/menu.lst: ================================

default 0
timeout 30
color NORMAL HIGHLIGHT HELPTEXT HEADING
splashimage=/splash.xpm.gz
foreground=FFFFFF
background=000000

# Suggested by Erhan Sohail
title Boot First Hard Drive (HDD)
map (hd0) (hd1)
map (hd1) (hd0)
map --hook
chainloader (hd0)+1
rootnoverify (hd0)

title Restart
reboot

title Shutdown
halt

title --- Custom MultiBoot Entries ---
root

title Ubuntu 10.10 (GNOME Desktop)
find --set-root /ubuntu-10.10-desktop.iso
map /ubuntu-10.10-desktop.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent iso-scan/filename=/ubuntu-10.10-desktop.iso splash
initrd /casper/initrd.lz

# YOU must modify this entry if it does not boot
title Unlisted ISO
find --set-root --ignore-floppies --ignore-cd /TEST.iso
map --heads=0 --sectors-per-track=0 /TEST.iso (hd32)
map --hook
chainloader (hd32)

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: menu.lst
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 f8 f0 00 04 78 00 00  00 00 00 00 02 00 00 00  |.....x..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 75 13 f1 18 4e  4f 20 4e 41 4d 45 20 20  |..)u...NO NAME  |
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
00000100  7d 00 66 b8 2c f0 00 00  66 ba 00 00 00 00 bb 00  |}.f.,...f.......|
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


=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by wilee-nilee on 2011-02-19
So you have a mixture of grub-legacy and grub2 installed could be purged probably and reloaded with grub2.

Your missing the /bootmgr /Boot/BCD that would be in the sda2 boot partition, can be put in sda3 with the bootlflag on the partition first.

You seem to have extra partitions and the 10.10 is a ext3.

Really you could back up what you need and get more organized and up to date with fresh installs. It would be faster and if you can't look at the script yourself and recognize what is missing probably your best move.:)

---

### Post by nabilalk on 2011-02-19
> **wilee-nilee said:**
> So you have a mixture of grub-legacy and grub2 installed could be purged probably and reloaded with grub2.

Your missing the /bootmgr /Boot/BCD that would be in the sda2 boot partition, can be put in sda3 with the bootlflag on the partition first.

You seem to have extra partitions and the 10.10 is a ext3.

Really you could back up what you need and get more organized and up to date with fresh installs. It would be faster and if you can't look at the script yourself and recognize what is missing probably your best move.:)
Thanks for your analysis. I have extra partitions for storage, those are deliberate. I'm willing to do a fresh Ubuntu install, however I need Win 7 for school and I don't want to reinstall Windows. What do I need to do to boot into Windows and I can deal with the reinstall of Ubuntu later?

---

### Post by wilee-nilee on 2011-02-19
> **nabilalk said:**
> Thanks for your analysis. I have extra partitions for storage, those are deliberate. I'm willing to do a fresh Ubuntu install, however I need Win 7 for school and I don't want to reinstall Windows. What do I need to do to boot into Windows and I can deal with the reinstall of Ubuntu later?

So the windows; I would move the bootflag to sda3 with gparted from a live Ubuntu cd, or from gparted installed in Ubuntu. Right click on sda3 then manage flags mark it as boot.

Then run the W7 repair from the booted recovery or install disc three times. the sda2 partition is only relevant if your using the windows encryption.

You may need to run a chkdsk /r at some point if you get W7 showing the missing files in sda3 as I posted. You will need to run the bootscript to see this.

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   **/bootmgr /Boot/BCD** /Windows/System32/winload.exe

To be honest your system is a bit askew and your in danger of a failure that will be having a failure again if you don't get grub squared up. Just because it boots Ubuntu does not mean it will soon or W7. You have grub2 in the mbr but grub-legacy showing in the script; this is not good, and easily fixable, don't just overlook this.

In this script is a line that you didn't finish the grub update and this command to run, in the Ubuntu install.
sudo upgrade-from-grub-legacy

---

### Post by nabilalk on 2011-02-20
[MBR Repair instructions]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html") I'm back in Windows :-) Now I have to reinstall Ubuntu, without screwing up the MBR. 

How do I install Ubuntu and make sure Grub detects Win7 this time?

---

### Post by wilee-nilee on 2011-02-20
> **nabilalk said:**
> [MBR Repair instructions]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html") I'm back in Windows :-) Now I have to reinstall Ubuntu, without screwing up the MBR. 

How do I install Ubuntu and make sure Grub detects Win7 this time?

If you wipe the Ubuntu you have now the grub2 bootloader in 10,04 will automatically find it upon reinstalling. The main problem you had was the missing W7 boot files niether grub's would work without the /bootmgr /Boot/BCD 

So make sure you do a custom install to a premade partition set up with gparted, just to be sure you keep everything thing else intact.

Glad you got Windows back I was wondering.:)

---

### Post by nabilalk on 2011-02-20
> **wilee-nilee said:**
> If you wipe the Ubuntu you have now the grub2 bootloader in 10,04 will automatically find it upon reinstalling. The main problem you had was the missing W7 boot files niether grub's would work without the /bootmgr /Boot/BCD 

So make sure you do a custom install to a premade partition set up with gparted, just to be sure you keep everything thing else intact.

Glad you got Windows back I was wondering.:)

Thanks for all your help.

---

