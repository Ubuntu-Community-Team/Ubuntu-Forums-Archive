---
title: "Dual-boot Windows 7 and Ubuntu gone wrong"
date: 2010-09-16
forum: General Help
---

### Post by KadirÖ on 2010-09-16
**Information about my HP Laptop:**

> Processor: 2x AMD Turion II Ultra Dual-core Mobile M620
Memory: 6GB of ram(Only 3,6GB used, because of Ubuntu Netbook not being 64-bit)
Ubuntu: Ubuntu 10.04 LTS(Kernel: Linux 2.6.32-21-generic (i686))
Windows: Windows 7 64-bit
Graphics card: ATI graphics card 1GB
**Full bootscript report: At bottom.**

It all started like this..

I bought my HP-laptop 4 weeks ago. 2 days ago I decided to dual-boot the pre-installed Windows 7 with Ubuntu Netbook. Thought it was a good idea.

Well, I created a partition for Ubuntu on 100GB on my current HDD and the whole disk went from a Primary Disc to Basic Disc(because of having more than 4 partitions).
After that I decided to delete the partitions created by HP called HP_TOOLS and HP_RECOVERY. I did.

After that I went and booted up with my USB and installed Ubuntu Netbook without SWAP-partition through advanced partition, as it didn't come up with "Install Ubuntu beside Windows" or anything like that, that I've seen others do.
At the advanded partition windows I chose the 100GB partition and checked "Reformat to Ext4 journaled". The mountpoint was "/".
It went fine and I loaded up Ubuntu Netbook after that.

Everything worked fine - I could load Windows 7 and Ubuntu Netbook through the GRUB bootloader.

But then it came.. Ubuntu Netbook decided to update to the latest Kernel I guess? and it did, well.. after that I haven't been able to load up Windows 7.

When I try to load up Windows 7, it goes on to the screen with the dots making the logo - doesn't even finish the logo - and then it freezes for a second, comes up with a blue-screen of death with errors for 0,5 seconds(so I can't read what it says), and then reboots.


This is my problem - I just want to be able to boot up my Windows 7. Could it have anything to do with Ubuntu Netbook changing something in the BIOS by itself, so I can't boot up Windows 7 64-bit?


Bootscript:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *  1,053,650,942 1,250,263,039   196,612,098   5 Extended
/dev/sda5       1,053,650,944 1,242,175,487   188,524,544  83 Linux
/dev/sda6       1,242,177,536 1,250,263,039     8,085,504  82 Linux swap / Solaris
/dev/sda2               2,048       409,599       407,552  42 SFS
/dev/sda3             409,600 1,053,648,895 1,053,239,296  42 SFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        74DE4D6CDE4D2826                       ntfs       SYSTEM                        
/dev/sda3        E64ADC344ADBFEED                       ntfs                                     
/dev/sda5        7ae67b97-e867-4932-b9a7-912cabd8dd1d   ext4                                     
/dev/sda6        0803011f-b789-435a-9862-ab296c682e02   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 74de4d6cde4d2826
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set e64adc344adbfeed
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0803011f-b789-435a-9862-ab296c682e02 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 593.3GB: boot/grub/core.img
 593.3GB: boot/grub/grub.cfg
 593.3GB: boot/initrd.img-2.6.32-21-generic
 593.4GB: boot/initrd.img-2.6.32-24-generic
 593.2GB: boot/vmlinuz-2.6.32-21-generic
 593.2GB: boot/vmlinuz-2.6.32-24-generic
 593.4GB: initrd.img
 593.3GB: initrd.img.old
 593.2GB: vmlinuz
 593.2GB: vmlinuz.old
```

Tried the chkdsk, wouldn't allow me to do it. Plus, when I run the other commands it says that it couldn't find any Windows installations.
I tried start-up repair - doesn't work.

---

### Post by blazemore on 2010-09-17
Could you please post the output of
```
sudo fdisk -l
```

---

### Post by crackbuntu on 2010-09-17
try this :


[LIST=1]
[*]Repair the startup of windows 7 using the installation disc, this will remove grub and correct BSOD
[*]delete the 100gb ubuntu ext4 partition using norton partition magic or any other program
[*]dump an iso of the UBUNTU installation inside a local disc on windows 7.
[*]extract the image using winrar or any other program.
[*]place a copy of the iso image u extracted into the extracted folder.
[*]run wubi.exe (from the extracted folder) and install ubuntu easily.
[*]u will have dual boot option of microsoft where u select windows 7 or ubuntu, selecting ubuntu will then load the GRUB which is safer if ubuntu crashes sometime.
[/LIST]
hope this helps :|
please mind my bad english :)
regards

---

### Post by RJ12 on 2010-09-17
I actually wouldn't recommend using WUBI for a permanent install, it just causes problems...

---

### Post by dnguyen1963 on 2010-09-17
> **KadirÖ said:**
> **Information about my HP Laptop:**



It all started like this..

I bought my HP-laptop 4 weeks ago. 2 days ago I decided to dual-boot the pre-installed Windows 7 with Ubuntu Netbook. Thought it was a good idea.

Well, I created a partition for Ubuntu on 100GB on my current HDD and the whole disk went from a Primary Disc to Basic Disc(because of having more than 4 partitions).
After that I decided to delete the partitions created by HP called HP_TOOLS and HP_RECOVERY. I did.

After that I went and booted up with my USB and installed Ubuntu Netbook without SWAP-partition through advanced partition, as it didn't come up with "Install Ubuntu beside Windows" or anything like that, that I've seen others do.
At the advanded partition windows I chose the 100GB partition and checked "Reformat to Ext4 journaled". The mountpoint was "/".
It went fine and I loaded up Ubuntu Netbook after that.

Everything worked fine - I could load Windows 7 and Ubuntu Netbook through the GRUB bootloader.

But then it came.. Ubuntu Netbook decided to update to the latest Kernel I guess? and it did, well.. after that I haven't been able to load up Windows 7.

When I try to load up Windows 7, it goes on to the screen with the dots making the logo - doesn't even finish the logo - and then it freezes for a second, comes up with a blue-screen of death with errors for 0,5 seconds(so I can't read what it says), and then reboots.


This is my problem - I just want to be able to boot up my Windows 7. Could it have anything to do with Ubuntu Netbook changing something in the BIOS by itself, so I can't boot up Windows 7 64-bit?


Bootscript:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *  1,053,650,942 1,250,263,039   196,612,098   5 Extended
/dev/sda5       1,053,650,944 1,242,175,487   188,524,544  83 Linux
/dev/sda6       1,242,177,536 1,250,263,039     8,085,504  82 Linux swap / Solaris
/dev/sda2               2,048       409,599       407,552  42 SFS
/dev/sda3             409,600 1,053,648,895 1,053,239,296  42 SFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        74DE4D6CDE4D2826                       ntfs       SYSTEM                        
/dev/sda3        E64ADC344ADBFEED                       ntfs                                     
/dev/sda5        7ae67b97-e867-4932-b9a7-912cabd8dd1d   ext4                                     
/dev/sda6        0803011f-b789-435a-9862-ab296c682e02   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 7ae67b97-e867-4932-b9a7-912cabd8dd1d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 74de4d6cde4d2826
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set e64adc344adbfeed
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7ae67b97-e867-4932-b9a7-912cabd8dd1d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0803011f-b789-435a-9862-ab296c682e02 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 593.3GB: boot/grub/core.img
 593.3GB: boot/grub/grub.cfg
 593.3GB: boot/initrd.img-2.6.32-21-generic
 593.4GB: boot/initrd.img-2.6.32-24-generic
 593.2GB: boot/vmlinuz-2.6.32-21-generic
 593.2GB: boot/vmlinuz-2.6.32-24-generic
 593.4GB: initrd.img
 593.3GB: initrd.img.old
 593.2GB: vmlinuz
 593.2GB: vmlinuz.old
```

Tried the chkdsk, wouldn't allow me to do it. Plus, when I run the other commands it says that it couldn't find any Windows installations.
I tried start-up repair - doesn't work.

Oh boys...you should have not deleted the recovery partition from W7.  Have you created recovery disks after you bought your computer?  Here is what I would do.  Delete the current Ubuntu and Repair W7 (Hopefully, you have the recovery disks) then use Windows Management to shrink W7 partition.  Companies are cutting cost everywhere.  I bought a HP laptop and had no recovery disks anywhere.  Everything was on the HD. I had to create the recovery disks myself. After shrinking W7 partition, you would have an unallocated space for installing Ubuntu.  Repeat...Do Not install Ubuntu without shrinking W7 partition first.  W7 is very naughty when something else is messing with its HD. You should then be able to install Ubuntu.

Good luck.

---

### Post by Mark Phelps on 2010-09-17
When Win7 was working, did you have the foresight to use the Backup feature to create and burn a Win7 Repair CD?  Probably not ...

Since that feature is now built-in to the OS, some OEMs are no longer providing ANY CDs with their machines.

If you don't have that disk (or an equivalent), you will NOT be able to repair the Win7 boot loader.  In that case, go to the link below (using Ubuntu), download and burn the appropriate Win7 Repair CD image, boot using that CD, and run Startup Repair three times:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by Mark Phelps on 2010-09-17
Sorry -- accidental double-post

---

### Post by KadirÖ on 2010-09-18
> **blazemore said:**
> Could you please post the output of
```
sudo fdisk -l
```
```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfdd42cde

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           65587       77826    98306049    5  Extended
/dev/sda2               1          26      203776   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3              26       65587   526619648   42  SFS
/dev/sda5           65587       77322    94262272   83  Linux
/dev/sda6           77322       77826     4042752   82  Linux swap / Solaris

Partition table entries are not in disk order

```

> **crackbuntu said:**
> try this :


[LIST=1]
[*]Repair the startup of windows 7 using the installation disc, this will remove grub and correct BSOD
[*]delete the 100gb ubuntu ext4 partition using norton partition magic or any other program
[*]dump an iso of the UBUNTU installation inside a local disc on windows 7.
[*]extract the image using winrar or any other program.
[*]place a copy of the iso image u extracted into the extracted folder.
[*]run wubi.exe (from the extracted folder) and install ubuntu easily.
[*]u will have dual boot option of microsoft where u select windows 7 or ubuntu, selecting ubuntu will then load the GRUB which is safer if ubuntu crashes sometime.
[/LIST]
hope this helps :|
please mind my bad english :)
regards
I wont use WUBI.

> **Mark Phelps said:**
> When Win7 was working, did you have the foresight to use the Backup feature to create and burn a Win7 Repair CD?  Probably not ...

Since that feature is now built-in to the OS, some OEMs are no longer providing ANY CDs with their machines.

If you don't have that disk (or an equivalent), you will NOT be able to repair the Win7 boot loader.  In that case, go to the link below (using Ubuntu), download and burn the appropriate Win7 Repair CD image, boot using that CD, and run Startup Repair three times:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

You're right about your statement that, I didn't have a Win7 repair CD. Well, I do got the whole installation CD for Win7 Ultimate on my USB - tried to do Start-Up Repair and it would say there was a problem that, it could not fix.

---

### Post by Mark Phelps on 2010-09-18
> **KadirÖ said:**
> Well, I do got the whole installation CD for Win7 Ultimate on my USB - tried to do Start-Up Repair and it would say there was a problem that, it could not fix.

Well, that's a real disappointment -- especially with MS and their inability to create diagnostic software that can repair their OSs.

You may just have to reinstall Win7 to get it working agin.

You could also check with the premier Win7 forum (sevenforums.com) to see what their experts advise.  There may be other ways for you to repair Win7 without having to reinstall it.

---

### Post by KadirÖ on 2010-09-18
> **Mark Phelps said:**
> Well, that's a real disappointment -- especially with MS and their inability to create diagnostic software that can repair their OSs.

You may just have to reinstall Win7 to get it working agin.

You could also check with the premier Win7 forum (sevenforums.com) to see what their experts advise.  There may be other ways for you to repair Win7 without having to reinstall it.

Okay, thank you.

---

### Post by mysoogal on 2010-09-26
I've been using the wubi installer not only for Ubuntu  8.10 and 9.04, 10.04 but also for mint Linux 9 for a long time 

there are no issues running wubi inside windows 7, Dual-boot within windows 7 creates no issues for me :KS

this is the system info

> 
System:    Host linuxmint Kernel 2.6.32-21-generic i686 (32 bit) Distro Linux Mint 9 Isadora
CPU:       Single core Intel Celeron 540 (UP) clocked at 1862.017 MHz 
Graphics:  Card Intel Mobile GM965/GL960 Integrated Graphics Controller tty res: 128x28 Gfx Data: N/A for root user
Disks:     HDD Total Size: 80.0GB (62.9% used)
Info:      Processes 144 Uptime 30 min Memory 272.3/2003.9MB Client Shell inxi 1.3.2 


---

### Post by SimonJones on 2010-10-21
Sorry for high-jacking this thread, but is there a solution? I too have a new laptop with Windows 7 on it. When I install Xubuntu, the Windows BSOD appears. A reinstall of Windows works but of course no Xubuntu. I have done this three times always the same result. Why can't I dual boot or is it Karma keeping me using Windows?

---

### Post by Quackers on 2010-10-21
KadirO when booting from your repair USB have you tried going to the command prompt and running 
bootrec /rebuildbcd
It could be worth a try before re-installing.

---

