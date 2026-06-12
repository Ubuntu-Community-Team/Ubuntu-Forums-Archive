---
title: "finding which grub files are being used?"
date: 2012-03-09
forum: General Help
---

### Post by garyed on 2012-03-09
I've got a bunch of HD's & quite a few different distros & installations of Grub2 on my system. Even running boot_info_script*** gives me a few different possibilities to choose from but it helps speed the process of finding which grub files are being used. Is there some kind of command that can look at the MBR & tell which grub files are being used? Is there a way to actually view the MBR?

---

### Post by garyed on 2012-03-10
The easiest thing I've found so far that works is to change the Grub_Timeout
in the /etc/default/grub file in each distro & whichever one matches the actual boot time tells me where the files are. There's got to be a better way. I even tried doing a hexdump on the MBR but not knowing what those numbers mean doesn't help me any. Anyone have any ideas?

---

### Post by Dave_L on 2012-03-10
```
$ sudo dd if=/dev/sda of=mbr.dat bs=512 count=1

$ file mbr.dat
mbr.dat: x86 boot sector; partition 1: ID=0x83, active, starthead 0, startsector 1, 104856254 sectors; partition 2: ID=0x5, starthead 254, startsector 484492188, 3904980 sectors, code offset 0x63
```

You could try doing the above, and use gparted to look for matching numbers.

(Be careful when using the dd command.)

---

### Post by oldfred on 2012-03-10
Boot_info script. 

I run it as part of my rsync backup just to document my 3 drives and multiple installs. The new git/test version has some fixes with grub 1.99 where the current one may not show exactly which partition grub in the MBR is booting from.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

The current version which has some instructions, but is not updated yet.
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

I like to have some repair tools in my toolbox. This one also runs the git version of boot script.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by garyed on 2012-03-10
I tried the dd & file command with similar outputs to what was posted but Gparted didn't help decipher anything. Here is the results of the new bootinfoscript:
```

                   Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Lucid Puppy Linux Linux 
                       2.6.33.5-rt25 [i686 arch]
    Boot files:        /etc/fstab

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sdd1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 7.10
    Boot files:        /boot/grub/menu.lst /etc/fstab

sdd2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdd5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdd7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   488,392,064   488,392,002   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   105,482,789   105,482,727  83 Linux
/dev/sdb2         105,482,851   780,518,024   675,035,174   5 Extended
/dev/sdb5         105,482,853   778,172,534   672,689,682  83 Linux
/dev/sdb6         778,172,598   780,518,024     2,345,427  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   312,560,639   312,560,577   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             63    97,659,134    97,659,072  83 Linux
/dev/sdd2          97,659,259   312,576,704   214,917,446   5 Extended
/dev/sdd5          97,659,261   128,375,414    30,716,154  83 Linux
/dev/sdd6         128,375,478   307,451,969   179,076,492  83 Linux
/dev/sdd7         307,451,970   312,576,704     5,124,735  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        4463-14F5                              vfat       ZADA
/dev/sdb1        90b840c4-146c-49d5-b1dd-e12f3f0b7fa8   ext4       
/dev/sdb5        7fb7dab9-d787-4ef5-99bc-21be54935a36   ext3       Puppy-Studio
/dev/sdb6        d093a873-defd-48a4-9e81-54e47828202c   swap       
/dev/sdc1        906C4EA36C4E83C6                       ntfs       Duality
/dev/sdd1        19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5   ext3       Gusty
/dev/sdd5        9491c0ca-97d5-4b39-819a-671b97879dbe   ext4       Lucid-Studio
/dev/sdd6        08258798-0555-42b1-80af-cacb43f99c0c   ext4       Home-10.04
/dev/sdd7        d2f0f089-7888-41be-8a33-7123fab40f40   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd3,1)'
search --no-floppy --fs-uuid --set 90b840c4-146c-49d5-b1dd-e12f3f0b7fa8
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
set root='(hd3,1)'
search --no-floppy --fs-uuid --set 90b840c4-146c-49d5-b1dd-e12f3f0b7fa8
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 90b840c4-146c-49d5-b1dd-e12f3f0b7fa8
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=90b840c4-146c-49d5-b1dd-e12f3f0b7fa8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 90b840c4-146c-49d5-b1dd-e12f3f0b7fa8
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=90b840c4-146c-49d5-b1dd-e12f3f0b7fa8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 90b840c4-146c-49d5-b1dd-e12f3f0b7fa8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 90b840c4-146c-49d5-b1dd-e12f3f0b7fa8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 906c4ea36c4e83c6
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 7.10, kernel 2.6.22-14-rt (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5
    linux /boot/vmlinuz-2.6.22-14-rt root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro quiet splash
    initrd /boot/initrd.img-2.6.22-14-rt
}
menuentry "Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5
    linux /boot/vmlinuz-2.6.22-14-rt root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro single
    initrd /boot/initrd.img-2.6.22-14-rt
}
menuentry "Ubuntu 7.10, memtest86+ (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5
    linux /boot/memtest86+.bin 
}
menuentry "Lucid - Ubuntu Studio (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 9491c0ca-97d5-4b39-819a-671b97879dbe
    linux /boot/vmlinuz-2.6.32-28-preempt root=UUID=9491c0ca-97d5-4b39-819a-671b97879dbe ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-preempt
}
menuentry "Lucid - Kernel Testing (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 9491c0ca-97d5-4b39-819a-671b97879dbe
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=9491c0ca-97d5-4b39-819a-671b97879dbe ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Hitachi-Lucid (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 9491c0ca-97d5-4b39-819a-671b97879dbe
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=90b840c4-146c-49d5-b1dd-e12f3f0b7fa8 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Recovery Mode  (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 9491c0ca-97d5-4b39-819a-671b97879dbe
    linux /boot/vmlinuz-2.6.32-28-preempt root=UUID=9491c0ca-97d5-4b39-819a-671b97879dbe ro single
    initrd /boot/initrd.img-2.6.32-28-preempt
}
menuentry "unknown Linux distribution (on /dev/sdd5)" {
    insmod ext2
    set root='(hd3,5)'
    search --no-floppy --fs-uuid --set 7fb7dab9-d787-4ef5-99bc-21be54935a36
    linux /boot/vmlinuz root=/dev/sdd5
}
menuentry "unknown Linux distribution (on /dev/sdd5)" {
    insmod ext2
    set root='(hd3,5)'
    search --no-floppy --fs-uuid --set 7fb7dab9-d787-4ef5-99bc-21be54935a36
    linux /boot/vmlinuz root=/dev/sdd5
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=90b840c4-146c-49d5-b1dd-e12f3f0b7fa8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=d093a873-defd-48a4-9e81-54e47828202c none            swap    sw              0       0
# swap was on /dev/sdd5 during installation
UUID=d2f0f089-7888-41be-8a33-7123fab40f40 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  44.141120434 = 47.396167168   boot/grub/core.img                             1
  44.160449505 = 47.416921600   boot/grub/grub.cfg                             2
  44.148532391 = 47.404125696   boot/initrd.img-2.6.32-21-generic              1
   0.142455578 = 0.152960512    boot/vmlinuz-2.6.32-21-generic                 1
  44.148532391 = 47.404125696   initrd.img                                     1
   0.142455578 = 0.152960512    vmlinuz                                        1

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/sdb5     /            ext3     defaults               0 1
none          /proc        proc     defaults               0 0
none          /sys         sysfs    defaults               0 0
none          /dev/pts     devpts   gid=2,mode=620         0 0
/dev/fd0      /mnt/floppy  auto     noauto,rw              0 0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 278.573683262 = 299.116214784  boot/vmlinuz                                   2

================================ sdc1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=========================== sdd1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
default           4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10
splashimage=(hd2,0)/boot/grub/splash1.xpm.gz 
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
# kopt=root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title        Ubuntu 7.10, kernel 2.6.22-14-rt
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.22-14-rt root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-rt
quiet

title        Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root        (hd2,0)
kernel        /boot/vmlinuz-2.6.22-14-rt root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro single
initrd        /boot/initrd.img-2.6.22-14-rt

# title        Ubuntu 7.10, kernel 2.6.22-14-generic
# root        (hd2,0)
# kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro quiet splash
# initrd        /boot/initrd.img-2.6.22-14-generic
# quiet

# title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
# root        (hd2,0)
# kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro single
# initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd2,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1

--------------------------------------------------------------------------------

=============================== sdd1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=d2f0f089-7888-4100-be8a-337123fab40f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hda1      /media/music_c   ntfs-3g defaults,utf8,umask=007,gid=46 0 1
/dev/sda1      /media/music_d   vfat   iocharset=utf8,umask=000 0  0    
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.698543072 = 0.750054912    boot/grub/menu.lst                             1
   0.721915722 = 0.775151104    boot/grub/stage2                               2
   0.698523998 = 0.750034432    boot/initrd.img-2.6.22-14-generic              3
   0.706447124 = 0.758541824    boot/initrd.img-2.6.22-14-generic.bak          3
   0.721808910 = 0.775036416    boot/initrd.img-2.6.22-14-rt                   4
   0.720927715 = 0.774090240    boot/initrd.img-2.6.22-14-rt.bak               3
   0.708198071 = 0.760421888    boot/vmlinuz-2.6.22-14-generic                 2
   0.723620892 = 0.776982016    boot/vmlinuz-2.6.22-14-rt                      2
   0.721808910 = 0.775036416    initrd.img                                     4
   0.698523998 = 0.750034432    initrd.img.old                                 3
   0.723620892 = 0.776982016    vmlinuz                                        2
   0.708198071 = 0.760421888    vmlinuz.old                                    2

=========================== sdd5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set default="1"
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
set root='(hd3,5)'
search --no-floppy --fs-uuid --set 9491c0ca-97d5-4b39-819a-671b97879dbe
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
set root='(hd3,5)'
search --no-floppy --fs-uuid --set 9491c0ca-97d5-4b39-819a-671b97879dbe
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd3,5)'
search --no-floppy --fs-uuid --set 9491c0ca-97d5-4b39-819a-671b97879dbe
insmod jpeg
if background_image /usr/share/images/desktop-base/star.jpg ; then
  set color_normal=white/black
  set color_highlight=yellow/light-cyan
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/45_custom ###

# Main Ubuntu Kernel
menuentry 'Lucid - Ubuntu Studio' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,5)'
    search --no-floppy --fs-uuid --set 9491c0ca-97d5-4b39-819a-671b97879dbe
    linux    /boot/vmlinuz-2.6.32-28-preempt root=UUID=9491c0ca-97d5-4b39-819a-671b97879dbe ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-preempt
}

# Lucid on Hitachi
menuentry 'Hitachi-Lucid' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 90b840c4-146c-49d5-b1dd-e12f3f0b7fa8
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=90b840c4-146c-49d5-b1dd-e12f3f0b7fa8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}


# Windows
menuentry "Microsoft Windows XP Home Edition " {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 906c4ea36c4e83c6
    drivemap -s (hd0) ${root}
    chainloader +1
}

# Gusty
menuentry "Gusty - Ubuntu 7.10 " {
    insmod ext2
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set 19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5
    linux /boot/vmlinuz-2.6.22-14-rt root=UUID=19bfe0aa-2af1-4ea2-88ba-f2894fdcdab5 ro quiet splash
    initrd /boot/initrd.img-2.6.22-14-rt
}

# Recovery mode
menuentry 'Recovery Mode ' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd3,6)'
    search --no-floppy --fs-uuid --set 9491c0ca-97d5-4b39-819a-671b97879dbe
    echo    'Loading Linux 2.6.32-28-preempt ...'
    linux    /boot/vmlinuz-2.6.32-28-preempt root=UUID=9491c0ca-97d5-4b39-819a-671b97879dbe ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-preempt
}

# Puppy Linux Studio

menuentry "Puppy Studio" {
        insmod ext2
        set root='(hd3,5)'          
        linux /boot/vmlinuz root=/dev/sdb5 pmedia=atahd
}
### END /etc/grub.d/45_custom ###
--------------------------------------------------------------------------------

=============================== sdd5/etc/fstab: ================================

--------------------------------------------------------------------------------
 /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd6 during installation
UUID=9491c0ca-97d5-4b39-819a-671b97879dbe /               ext4    errors=remount-ro   0       1
                                     
# /home was on /dev/sdd7 during installation
UUID=08258798-0555-42b1-80af-cacb43f99c0c /home           ext4    defaults        0       2
 
# swap was on /dev/sdc5 during installation
 UUID=d2f0f089-7888-41be-8a33-7123fab40f40 none            swap    sw              0       0

# /dev/sdd1      /media/gusty      ext3    defaults   0        0                      
# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdd5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  53.581442356 = 57.532635648   boot/grub/core.img                             1
  51.376341343 = 55.164926464   boot/grub/grub.cfg                             1
  52.032007694 = 55.868942848   boot/initrd.img-2.6.32-21-generic              1
  51.455618382 = 55.250049536   boot/initrd.img-2.6.32-21-preempt              1
  51.969957829 = 55.802317312   boot/initrd.img-2.6.32-28-preempt              1
  51.975615025 = 55.808391680   boot/vmlinuz-2.6.32-21-generic                 1
  46.831144810 = 50.284558848   boot/vmlinuz-2.6.32-21-preempt                 1
  51.865900517 = 55.690586624   boot/vmlinuz-2.6.32-28-preempt                 1
  51.969957829 = 55.802317312   initrd.img                                     1
  51.455618382 = 55.250049536   initrd.img.old                                 1
  51.865900517 = 55.690586624   vmlinuz                                        1
  46.831144810 = 50.284558848   vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sde 



```

---

### Post by oldfred on 2012-03-10
Script does not always show drive. You are booting from either sda or sdc from the install in sdd5.

I would install grub2's boot loader to sdd, just to have the boot loader on the same drive as the install.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdd"  then just run:
sudo grub-install /dev/sdd
#If that returns any errors run:
sudo grub-install --recheck /dev/sdd
sudo update-grub
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

You can do the same for the install in sdb, if you boot into it and then install grub2's boot loader to sdb's MBR.

You also have this in your Windows which may prevent grub2's os-prober from correctly finding the Windows install.

/boot/grub/core.img

---

### Post by garyed on 2012-03-10
Before I go any further let me make it clear that I am not having any problem booting into any of my OS's so I don't want to reinstall anything.
I was just curious as to which grub files the MBR was pointing to. It all started when I changed the grub_timeout in /etc/default/grub & then did the "update-grub" command & it didn't change the time at boot up. I realized I may be working with the wrong grub file. It occurred to me that there should be a simple command that would give that information since a lot of us have multiple distros on the same machine.

---

### Post by Dave_L on 2012-03-10
I'm curious about this too.

In the output from "file mbr.dat" I posted above, do you know if "active" indicates the boot partition?

---

### Post by garyed on 2012-03-10
> **Dave_L said:**
> I'm curious about this too.

In the output from "file mbr.dat" I posted above, do you know if "active" indicates the boot partition?
I don't know because my output is a little different than yours.
Here it is for my file that I named mbrcontent:
> 
mbrcontent: x86 boot sector; GRand Unified Bootloader, stage1 version 0x3, boot drive 0x80, stage2 address 0x2000, stage2 segment 0x200; partition 1: ID=0xc, active, starthead 1, startsector 63, 488392002 sectors, code offset 0x63



---

### Post by oldfred on 2012-03-10
Active is a Windows term for the boot flag. Windows uses the boot flag to know which partition to jump to as Windows has more boot code in the partition boot sector. Grub does not use a boot flag and normally does not have additional code in the partition boot sector.

From what I see of the output of file mbr.dat is just a dump of the partition table not the MBR.

Info on MBR
[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

Some of the boot info with grub is in the sectors after the MBR where core.img is.

---

### Post by garyed on 2012-03-11
There's something interesting I found in the file output.
If you look at the part that says "patition ID= 0x83" the 83 corresponds to the ID from "fdisk -l" that says Linux. So "ID=0x5" would be 5 & thats the id for the extended partition. Mine says "ID=0xc" &  "c" is the ID for FAT32 which is how that particular drive is formatted. My problem is trying to find where the other grub files are since they're not on that drive at all.

---

### Post by oldfred on 2012-03-11
I have different grub2 boot loaders in every drive. But when its boots each drive, the install that is first on the menu controls all the settings. 

Editing grub in any other install has no change to boot configuration of the grub that is in control. 

In my case it can get confusing if I boot a second entry that is the first entry from a different drive. Then only when I boot that different drive would those new settings be in charge.

---

### Post by garyed on 2012-03-11
Something else I noticed is there must be a bug in the bootinfoscript too.
If you look at my earlier post where my RESULTS.txt showed the drives grub2 was installed it also said it looked for grub files on partition 5. Both drives are just one single partition so I know the files can't be there.

---

### Post by oldfred on 2012-03-11
Script has worked that way for a long time. Not sure if it is script or grub and how it reports which drive it boot from. 

You can see which drive grub will reinstall to from this:

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

