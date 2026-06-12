---
title: "error: no such device"
date: 2010-11-09
forum: General Help
---

### Post by onesojourner on 2010-11-09
after a failed update attempt from 10.04 to 10.10 I tried to just do a fresh install of 10.10. 

This is the error message I am getting:

error: no such device 3f83145b-1925-4793-b0c5-2779446c6b1b

I have tried reinstalling grub with no luck. I have 4 hdd in this machine and I have had various ubuntu installs on them over the years so that may be causing issues. I also ran something that was supposed to delete the mbr and I ran it for each hdd. Currently I am booted into a 10.10 live cd.thanks in advance for your help.

---

### Post by drs305 on 2010-11-09
Please go to this site and download / run the boot info script. Post the contents of RESULTS.txt. It should help us figure out what has gone wrong.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

If you would like to try to boot directly from the grub rescue prompt:
Highlight the menuentry you want.
Cursor to the "search" line and delete it by holding down the DEL key.
Go to the "linux" line and change the section "root=UUID=<some UUID>" to "root=/dev/sdXY", with sdXY being your Ubuntu partition (for instance *root=/dev/sda5*).
CTRL-x to boot.

---

### Post by onesojourner on 2010-11-09
Here you go:

```
       Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    61,304,039    61,303,977  83 Linux
/dev/sda2          61,304,832   113,063,935    51,759,104   7 HPFS/NTFS
/dev/sda3    *    113,065,470   144,086,984    31,021,515  83 Linux
/dev/sda4         144,086,985   976,768,064   832,681,080   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63       996,029       995,967  82 Linux swap / Solaris
/dev/sdb2             996,030    20,691,719    19,695,690  83 Linux
/dev/sdb3    *     20,691,720 1,953,520,064 1,932,828,345   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048    20,482,047    20,480,000  83 Linux
/dev/sdc2          20,482,875 2,930,272,064 2,909,789,190   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048    30,722,047    30,720,000  83 Linux
/dev/sdd2          30,722,048 3,907,022,847 3,876,300,800   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        16b2ce52-75d2-4427-8f9b-47aed2350631   ext4                                     
/dev/sda2        FC8883248882DC90                       ntfs                                     
/dev/sda3        8d254d99-cc7d-47ac-9052-d30f7b66d10c   ext4                                     
/dev/sda4        DEE0D663E0D64207                       ntfs       main                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        90fad9af-08a2-424b-abe6-7827f74d2589   swap                                     
/dev/sdb2        233c94f0-5316-405f-9f47-9339d16698a9   ext4                                     
/dev/sdb3        5C8C87558C87291A                       ntfs       1t                            
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        aaac6522-2293-4f85-859e-4890c44c1917   ext4                                     
/dev/sdc2        B8E47E70E47E312C                       ntfs       1.5T                          
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        97d4636d-8b81-407f-9024-90cbfe771228   xfs                                      
/dev/sdd2        CC3E79883E796BF8                       ntfs       2T                            
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 16b2ce52-75d2-4427-8f9b-47aed2350631
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 16b2ce52-75d2-4427-8f9b-47aed2350631
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 16b2ce52-75d2-4427-8f9b-47aed2350631
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=16b2ce52-75d2-4427-8f9b-47aed2350631 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 16b2ce52-75d2-4427-8f9b-47aed2350631
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=16b2ce52-75d2-4427-8f9b-47aed2350631 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 16b2ce52-75d2-4427-8f9b-47aed2350631
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 16b2ce52-75d2-4427-8f9b-47aed2350631
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 5c8c87558c87291a
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=16b2ce52-75d2-4427-8f9b-47aed2350631 /               ext4    errors=remount-ro 0       1
# /1storage was on /dev/sda4 during installation
UUID=DEE0D663E0D64207 /1storage       ntfs    defaults,umask=007,gid=46 0       0
# /2storage was on /dev/sdb3 during installation
UUID=5C8C87558C87291A /2storage       ntfs    defaults,umask=007,gid=46 0       0
# /3storage was on /dev/sdc2 during installation
UUID=B8E47E70E47E312C /3storage       ntfs    defaults,umask=007,gid=46 0       0
# /4storage was on /dev/sdd2 during installation
UUID=CC3E79883E796BF8 /4storage       ntfs    defaults,umask=007,gid=46 0       0
# /home/backup was on /dev/sda3 during installation
UUID=8d254d99-cc7d-47ac-9052-d30f7b66d10c /home/backup    ext4    defaults        0       2
# /storage4 was on /dev/sdd1 during installation
UUID=97d4636d-8b81-407f-9024-90cbfe771228 /storage4       xfs     defaults        0       2
# /store2 was on /dev/sdc1 during installation
UUID=aaac6522-2293-4f85-859e-4890c44c1917 /store2         ext4    defaults        0       2
# /tmp was on /dev/sdb2 during installation
UUID=233c94f0-5316-405f-9f47-9339d16698a9 /tmp            ext4    defaults        0       2
# /windows was on /dev/sda2 during installation
UUID=FC8883248882DC90 /windows        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sdb1 during installation
UUID=90fad9af-08a2-424b-abe6-7827f74d2589 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
  23.8GB: boot/grub/grub.cfg
  24.4GB: boot/initrd.img-2.6.35-22-generic-pae
  21.6GB: boot/vmlinuz-2.6.35-22-generic-pae
  24.4GB: initrd.img
  21.6GB: vmlinuz

```

---

### Post by drs305 on 2010-11-09
If your BIOS points to what RESULTS.txt identifies as sda it will probably boot to Ubuntu.

I see your Windows boot files are on sdb, so there is a decent chance that the drive RESULTS.txt identifies as sdb is the one that the system initially tries to boot. That would fail because sdb's MBR points Grub to sdb1, which has no Ubuntu files.

So I would recommend looking at BIOS and make sure it points to sda. If that doesn't fix it we can reinstall grub from the LiveCD.

---

### Post by onesojourner on 2010-11-09
The only option in my bois that I can see has the first boot device set as cdrom then hdd. Is that waht you mean?

---

### Post by drs305 on 2010-11-09
> **onesojourner said:**
> The only option in my bois that I can see has the first boot device set as cdrom then hdd. Is that waht you mean?

Yes, but...

If you click on the 'hdd' it may expand to show each of your hard drives, which you can then order. Or there could be another setting in the BIOS in another section that lists the drives and lets you rearrange the order.

For instance, in one section it may give you the options of hard drive, CDROM, removable, etc. If not in the same section, another one may show you each drive and allow you to move them up/down in the list. You would want your Ubuntu drive at the top of the list.

---

### Post by onesojourner on 2010-11-09
I don't think there is any way for me to move them around but they are in order by sata ports. the drive with ubuntu is listed as 0 the others are listed 1,2,3

---

### Post by drs305 on 2010-11-09
The error message is being generated because there is no partition identified by that UUID listed in RESULTS.txt.

If you can boot to the LiveCD, mount your Ubuntu partition and then reinstall grub. Note you mount the partition in the first command but only the drive in the second.

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

This may or may not solve the issue. You will probably have to chroot into the partition and run update-grub to refresh grub.cfg (Running update-grub from the LiveCD without chrooting won't work). The chroot instructions link are in my signature line.

---

### Post by onesojourner on 2010-11-09
thanks again for walking me through all that. To catch any one else up that might be able to help I reinstalled grub but my issue remains. here is my new boot info script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    61,304,039    61,303,977  83 Linux
/dev/sda2          61,304,832   113,063,935    51,759,104   7 HPFS/NTFS
/dev/sda3    *    113,065,470   144,086,984    31,021,515  83 Linux
/dev/sda4         144,086,985   976,768,064   832,681,080   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63       996,029       995,967  82 Linux swap / Solaris
/dev/sdb2             996,030    20,691,719    19,695,690  83 Linux
/dev/sdb3    *     20,691,720 1,953,520,064 1,932,828,345   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048    20,482,047    20,480,000  83 Linux
/dev/sdc2          20,482,875 2,930,272,064 2,909,789,190   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048    30,722,047    30,720,000  83 Linux
/dev/sdd2          30,722,048 3,907,022,847 3,876,300,800   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        16b2ce52-75d2-4427-8f9b-47aed2350631   ext4                                     
/dev/sda2        FC8883248882DC90                       ntfs                                     
/dev/sda3        8d254d99-cc7d-47ac-9052-d30f7b66d10c   ext4                                     
/dev/sda4        DEE0D663E0D64207                       ntfs       main                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        90fad9af-08a2-424b-abe6-7827f74d2589   swap                                     
/dev/sdb2        233c94f0-5316-405f-9f47-9339d16698a9   ext4                                     
/dev/sdb3        5C8C87558C87291A                       ntfs       1t                            
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        aaac6522-2293-4f85-859e-4890c44c1917   ext4                                     
/dev/sdc2        B8E47E70E47E312C                       ntfs       1.5T                          
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        97d4636d-8b81-407f-9024-90cbfe771228   xfs                                      
/dev/sdd2        CC3E79883E796BF8                       ntfs       2T                            
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 16b2ce52-75d2-4427-8f9b-47aed2350631
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 16b2ce52-75d2-4427-8f9b-47aed2350631
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 16b2ce52-75d2-4427-8f9b-47aed2350631
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=16b2ce52-75d2-4427-8f9b-47aed2350631 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 16b2ce52-75d2-4427-8f9b-47aed2350631
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=16b2ce52-75d2-4427-8f9b-47aed2350631 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 16b2ce52-75d2-4427-8f9b-47aed2350631
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 16b2ce52-75d2-4427-8f9b-47aed2350631
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=16b2ce52-75d2-4427-8f9b-47aed2350631 /               ext4    errors=remount-ro 0       1
# /1storage was on /dev/sda4 during installation
UUID=DEE0D663E0D64207 /1storage       ntfs    defaults,umask=007,gid=46 0       0
# /2storage was on /dev/sdb3 during installation
UUID=5C8C87558C87291A /2storage       ntfs    defaults,umask=007,gid=46 0       0
# /3storage was on /dev/sdc2 during installation
UUID=B8E47E70E47E312C /3storage       ntfs    defaults,umask=007,gid=46 0       0
# /4storage was on /dev/sdd2 during installation
UUID=CC3E79883E796BF8 /4storage       ntfs    defaults,umask=007,gid=46 0       0
# /home/backup was on /dev/sda3 during installation
UUID=8d254d99-cc7d-47ac-9052-d30f7b66d10c /home/backup    ext4    defaults        0       2
# /storage4 was on /dev/sdd1 during installation
UUID=97d4636d-8b81-407f-9024-90cbfe771228 /storage4       xfs     defaults        0       2
# /store2 was on /dev/sdc1 during installation
UUID=aaac6522-2293-4f85-859e-4890c44c1917 /store2         ext4    defaults        0       2
# /tmp was on /dev/sdb2 during installation
UUID=233c94f0-5316-405f-9f47-9339d16698a9 /tmp            ext4    defaults        0       2
# /windows was on /dev/sda2 during installation
UUID=FC8883248882DC90 /windows        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sdb1 during installation
UUID=90fad9af-08a2-424b-abe6-7827f74d2589 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
  19.5GB: boot/grub/grub.cfg
  24.4GB: boot/initrd.img-2.6.35-22-generic-pae
  21.6GB: boot/vmlinuz-2.6.35-22-generic-pae
  24.4GB: initrd.img
  21.6GB: vmlinuz

```

---

### Post by onesojourner on 2010-11-09
well after hours and hours I am up and running again. It did turn out to be a hdd issue in my bios. Thanks again drs305 you were a huge help with this.

> **drs305 said:**
> Yes, but...

If you click on the 'hdd' it may expand to show each of your hard drives, which you can then order. Or there could be another setting in the BIOS in another section that lists the drives and lets you rearrange the order.

For instance, in one section it may give you the options of hard drive, CDROM, removable, etc. If not in the same section, another one may show you each drive and allow you to move them up/down in the list. You would want your Ubuntu drive at the top of the list.

---

### Post by drs305 on 2010-11-09
First attempted to boot from the grub prompt. The RESULTS.txt indicated sda1 but the files were eventually found on (hd3,1) using the "ls (hdX,Y)/boot/grub" command. Nevertheless, booting from the grub prompt failed as the modules would not load and a "grub xputs" message resulted. 

*chrooting* and reinstalling grub-common and grub-pc were accomplished without error but still produced the same failure message for the non-existent UUID.

With that revelation, the OP *chrooted* once again, reinstalled grub-common and grub-pc, ran "grub-install --recheck /dev/sda", and for good measure created a device.map file using "grub-mkdevicemap". 

With the BIOS reset to boot the Ubuntu partition the system finally booted to Ubuntu. Although this possibility was mentioned earlier in the thread, the inability to boot from the grub prompt and the "xputs" error delayed making this change until several other steps were taken. Which of the step(s) in the previous paragraph could have been omitted is unknown.

---

