---
title: "New Dual-boot but cannot load windows7(grub problem)"
date: 2011-04-12
forum: General Help
---

### Post by bryanftw on 2011-04-12
Finally made the switch over to ubuntu, but I needed to keep my windows7 for several reasons. Let just start by saying I have two hard drives, a 200gig(which holds my windows7 partition) and a 500gig(has a 100gig partition which has ubuntu on it). After finally getting 10.04 to install on the 100gig partition and everything running right, I tried to load up windows7 and got an error. 
Something along to lines of "the partition does not exist". I believe I messed up on the last step on the install, as I might of just been careless. I remember reading somewhere that if using multiple hard drives grub may get messed up in one way or another. IS there a way to fix this and make grub realize that window7 is on another partition, or am I out of luck?

edit: Id like to add that grub is recognizing windows7, it just will not load off the other partition(I think)

---

### Post by bryanftw on 2011-04-12
bump?

---

### Post by Hedgehog1 on 2011-04-12
Lets see what things look like on your drives. Then we can show you your options!

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by bryanftw on 2011-04-12
ok, working on that now

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       18370798 sectors, but according to the info from 
                       fdisk, it has 18374799 sectors.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   372,345,119   372,345,057  42 SFS
/dev/sda2         372,345,120   390,719,919    18,374,800  42 SFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              34       262,177       262,144 Microsoft Windows
/dev/sdb2         262,178   679,494,365   679,232,188 Linux or Data
/dev/sdb3     679,495,680   679,497,727         2,048 Bios Boot Partition
/dev/sdb4     679,497,728   964,937,727   285,440,000 Linux or Data
/dev/sdb5     964,937,728   976,773,119    11,835,392 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A224AFE124AFB727                       ntfs       Storage                       
/dev/sda2        2C88743C8874071C                       ntfs       Recovery                      
/dev/sda: PTTYPE="dos" 
/dev/sdb2        16AB131F75B3A2EB                       ntfs       msf                           
/dev/sdb4        b4e34baa-54e7-457a-a6e7-234de0c1e083   ext4                                     
/dev/sdb5        76f9bab4-b43f-4b6d-95f5-7385e0f18eab   swap                                     
/dev/sdb: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb4/boot/grub/grub.cfg: ===========================

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
set root='(hd1,4)'
search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
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
set root='(hd1,4)'
search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
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
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=b4e34baa-54e7-457a-a6e7-234de0c1e083 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=b4e34baa-54e7-457a-a6e7-234de0c1e083 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=b4e34baa-54e7-457a-a6e7-234de0c1e083 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=b4e34baa-54e7-457a-a6e7-234de0c1e083 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,4)'
    search --no-floppy --fs-uuid --set b4e34baa-54e7-457a-a6e7-234de0c1e083
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a224afe124afb727
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb4 during installation
UUID=b4e34baa-54e7-457a-a6e7-234de0c1e083 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=76f9bab4-b43f-4b6d-95f5-7385e0f18eab none            swap    sw              0       0

=================== sdb4: Location of files loaded by Grub: ===================


 457.5GB: boot/grub/core.img
 376.0GB: boot/grub/grub.cfg
 457.7GB: boot/initrd.img-2.6.32-28-generic
 457.6GB: boot/initrd.img-2.6.32-30-generic
 457.5GB: boot/vmlinuz-2.6.32-28-generic
 457.5GB: boot/vmlinuz-2.6.32-30-generic
 457.6GB: initrd.img
 457.7GB: initrd.img.old
 457.5GB: vmlinuz
 457.5GB: vmlinuz.old
```

---

### Post by oldfred on 2011-04-13
You need a setting in your grub file to also see MBR(msdos) drives.

gpt drive with MBR drive for 10.04 or before. Fixed in 10.10
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:GTP_MS_DOS](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:GTP_MS_DOS)


But you have another problem. Your sda is converted to dynamic disk or SFS. Only windows works with dynamic and I do not know if grub will chainload into it or not. I suspect not.

While it would be best to remove the dynamic partitioning, that is difficult. Another alternative is to install grub2 to sdb, and boot sdb. You can then install the standard windows boot loader to sda and chainload to the MBR rather than the windows partition.

SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

To install grub2 to sdb.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
Change BIOS to boot sdb, the 500GB drive.

---

