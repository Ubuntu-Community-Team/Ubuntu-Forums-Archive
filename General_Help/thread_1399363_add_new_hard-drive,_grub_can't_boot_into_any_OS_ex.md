---
title: "add new hard-drive, grub can't boot into any OS except XP"
date: 2010-02-05
forum: General Help
---

### Post by t3chnique on 2010-02-05
Hello! i trippled boot Ubuntu 9.10, openSUSE 11.2, and Windows XP on sda. 

I configured so SUSE's GRUB takes charge of booting all the OS and it worked out fine and all (openSUSE 11.2 still use GRUB 0.97) 

So recently i added a IDE hard-drive, and the orginal sda where every OS installed on becomes sdb and the newly added IDE hard-drive becomes sda. For some unknown reason to me, SUSE's GRUB still show up every OS boot entry but it can't boot to any except windows XP (weird?). If I disconnect the IDE hard-drive, everything works fine, SUSE's GRUB can boot into all OS.

My question now is i wanted to put Ubuntu's GRUB back in charge and hopefully it will fix everything up. Or is it possible that i can change the hard-drive label (change the IDE drive to sdb and the drive with all OS back to sda, so SUSE's GRUB can find the correct path)

Here's my boot info result
```
============================= Boot Info Summary: ==============================

 => Grub 0.97-os.1 is installed in the MBR of /dev/sda and looks on boot drive 
    #3 in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Acer 3 is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb3 and 
                       looks at sector 87386348 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Welcome to openSUSE 11.2 
                       "Emerald" - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000f191

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   390,716,864   390,716,802   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0af20af2

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sdb2          40,965,750    81,931,499    40,965,750  83 Linux
/dev/sdb3    *     81,931,500   122,897,249    40,965,750  83 Linux
/dev/sdb4         122,897,250   312,576,704   189,679,455   5 Extended
/dev/sdb5         131,090,463   312,576,704   181,486,242   7 HPFS/NTFS
/dev/sdb6         122,897,376   131,090,399     8,193,024  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        10D3B3A779624DE2                       ntfs       daydream                      
/dev/sdb1        6105EA3360DCFD5D                       ntfs       WinXP                         
/dev/sdb2        b6c62392-c557-437a-8c61-6f1c240e105f   ext4       Ubuntu                        
/dev/sdb3        cbc0d65b-6e2f-43d9-89ce-1b9cff905f6f   ext4       Suse                          
/dev/sdb5        46BD9DA058034EAC                       ntfs       Shared                        
/dev/sdb6        b5e318ac-a39b-4217-b0fc-c005c4808cb2   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdb2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set b6c62392-c557-437a-8c61-6f1c240e105f
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set b6c62392-c557-437a-8c61-6f1c240e105f
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=b6c62392-c557-437a-8c61-6f1c240e105f ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set b6c62392-c557-437a-8c61-6f1c240e105f
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=b6c62392-c557-437a-8c61-6f1c240e105f ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set b6c62392-c557-437a-8c61-6f1c240e105f
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=b6c62392-c557-437a-8c61-6f1c240e105f ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set b6c62392-c557-437a-8c61-6f1c240e105f
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=b6c62392-c557-437a-8c61-6f1c240e105f ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6105ea3360dcfd5d
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "openSUSE 11.2 (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set cbc0d65b-6e2f-43d9-89ce-1b9cff905f6f
	linux /boot/vmlinuz-2.6.31.5-0.1-default root=/dev/sda3 resume=/dev/disk/by-id/ata-SAMSUNG_SP1614C_S01XJ10X811688-part6 splash=silent quiet showopts vga=0x314
	initrd /boot/initrd-2.6.31.5-0.1-default
}
menuentry "Failsafe -- openSUSE 11.2 (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set cbc0d65b-6e2f-43d9-89ce-1b9cff905f6f
	linux /boot/vmlinuz-2.6.31.5-0.1-default root=/dev/sda3 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x314
	initrd /boot/initrd-2.6.31.5-0.1-default
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=b6c62392-c557-437a-8c61-6f1c240e105f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b5e318ac-a39b-4217-b0fc-c005c4808cb2 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


  20.9GB: boot/grub/core.img
  20.9GB: boot/grub/grub.cfg
  20.9GB: boot/initrd.img-2.6.31-14-generic
  20.9GB: boot/initrd.img-2.6.31-17-generic
  20.9GB: boot/vmlinuz-2.6.31-14-generic
  20.9GB: boot/vmlinuz-2.6.31-17-generic
  20.9GB: initrd.img
  20.9GB: initrd.img.old
  20.9GB: vmlinuz
  20.9GB: vmlinuz.old

=========================== sdb3/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Sat Jan 30 01:44:24 PST 2010
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,2)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.2
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.31.5-0.1-default root=/dev/sda3 resume=/dev/disk/by-id/ata-SAMSUNG_SP1614C_S01XJ10X811688-part6 splash=silent quiet showopts vga=0x314
    initrd /boot/initrd-2.6.31.5-0.1-default

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.2
    root (hd0,2)
    kernel /boot/vmlinuz-2.6.31.5-0.1-default root=/dev/sda3 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1  x11failsafe vga=0x314
    initrd /boot/initrd-2.6.31.5-0.1-default

###Don't change this comment - YaST2 identifier: Original name: memtest86###
title Memory Test
    kernel (hd0,2)/boot/memtest.bin

#Don't change this comment - YaST2 identifier: Original name: linux#
title Ubuntu 9.10
root (hd0,1)
kernel /vmlinuz root=/dev/sda2 ro quiet splash
initrd /initrd.img 

=============================== sdb3/etc/fstab: ===============================

/dev/sda3            /                    ext4       acl,user_xattr        1 1
/dev/disk/by-id/ata-SAMSUNG_SP1614C_S01XJ10X811688-part6 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-SAMSUNG_SP1614C_S01XJ10X811688-part1 /windows/C           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
/dev/disk/by-id/ata-SAMSUNG_SP1614C_S01XJ10X811688-part5 /windows/D           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sdb3: Location of files loaded by Grub: ===================


  41.9GB: boot/grub/menu.lst
  41.9GB: boot/grub/stage2
  41.9GB: boot/initrd
  41.9GB: boot/initrd-2.6.31.5-0.1-default
  41.9GB: boot/vmlinuz
  41.9GB: boot/vmlinuz-2.6.31.5-0.1-default
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

I tried to re-install GRUB to the MBR by booting up from the 9.10 disc, installed grub and I did
```
sudo grub
grub> find /boot/grub/stage1
 (hd1,2)

grub> root (hd1,2)

grub> setup (hd1,2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,2)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,2)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,2) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.


```

reboot and SUSE's GRUB is still there with the same problem (can't boot into any except XP) and also I've been messing around with the Super GRUB disk but it didn't help either.

Your help and suggestion will be greatly appreciated :p

---

### Post by dcstar on 2010-02-06
> **t3chnique said:**
> 
.........
I tried to **re-install GRUB to the MBR** by booting up from the 9.10 disc, installed grub and I did
```
sudo grub
grub> find /boot/grub/stage1
 (hd1,2)

grub> root (hd1,2)

grub> setup (hd1,2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,2)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,2)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,2) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.


```


No you didn't, you installed Grub onto that partition. This will install Grub onto that disk's MBR:

```
grub> setup (hd1)
```

---

### Post by t3chnique on 2010-02-06
> **dcstar said:**
> No you didn't, you installed Grub onto that partition. This will install Grub onto that disk's MBR:

```
grub> setup (hd1)
```

I did what you suggested and i got some Error parsing number at first but after a while it lets me install grub on hd1 for some reason. Reboot and SUSE's GRUB still there. I can boot into Ubuntu 9.10 by changing to the correct drive 

SUSE's GRUB display the boot option for Ubuntu as 
```
root=/dev/sda2 ro quiet splash
```

If i want to boot into Ubuntu i change it to
```
root=/dev/sdb2 ro quiet splash
```

I don't understand though, I have re-installed Ubuntu's GRUB to the **MBR**, how come SUSE's GRUB still there?

---

