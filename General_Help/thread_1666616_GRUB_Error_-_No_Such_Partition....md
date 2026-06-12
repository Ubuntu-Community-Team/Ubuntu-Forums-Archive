---
title: "GRUB Error - No Such Partition..."
date: 2011-01-13
forum: General Help
---

### Post by porkchop_001 on 2011-01-13
Hi Guys,

Just when I had everything going well on my machine (a healthy Windows 7 and Ubuntu 10.10 partition) my little brother goes a head and screws it up.

Cutting a long and painful story short - he's deleted my Ubuntu partition from within windows. Now, when I boot up my machine, I get a Grub error that states 'No such partition' and doesn't allow me to do anything. I've attached a screenshot below.

[http://img825.imageshack.us/i/img00185201101141449.jpg/](http://img825.imageshack.us/i/img00185201101141449.jpg/)

Does anyone know how I can rectify this? I'm assuming I'll have to use the Live CD and remove GRUB or something? I just need to get into my Windows 7 side that's all.

Any help would be greatly appreciated. Thanks in advance :)

---

### Post by Quackers on 2011-01-14
If you just want Windows you can repair the mbr with a Windows repair disc.
If you want Ubuntu back, re-install it, then grub should get everything bootable again.

---

### Post by Rubi1200 on 2011-01-14
As Quackers mentioned, you need to fix the MBR to get Windows booting again:
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by MARP1961 on 2011-01-14
If you reinstall Ubuntu using an Ubuntu CD it will repair Grub Bootloader which will then allow you to boot into either Windows or Ubuntu without the need to 'repair' the Windows MBR. Just go careful and make sure you don't allow Ubuntu to install over the Windows partition as well! If you just want Windows on it's own, you will need a Windows install or repair CD to fix MBR.

---

### Post by porkchop_001 on 2011-01-14
Hi Guys,

I went ahead and re-installed Ubuntu. All was working fine. I logged out of Ubuntu, once it had installed, and headed back into Windows to do some stuff (GRUB was working fine - hence being able to boot back into Windows).

Then when I reset my machine it's gone back to the 'error:no such partition' again. What the flip is going on? I just re-installed it! It was working fine. This one has me quite confused I assure you. Did I install Ubuntu on an incorrect partition? I had some free space on my hard drive so  formatted it was ext4 and set the mount point to '/'. Is that correct?

Annoyed face! Thanks for your support.

---

### Post by Rubi1200 on 2011-01-14
From within Ubuntu or a LiveCD, post the output from running the boot info script linked at the bottom of my post.

Thanks.

---

### Post by Quackers on 2011-01-14
+1 for the boot script.
Is this a Dell machine by any chance? With Dell Data Safe?

---

### Post by porkchop_001 on 2011-01-14
> **Rubi1200 said:**
> From within Ubuntu or a LiveCD, post the output from running the boot info script linked at the bottom of my post.

Thanks.

Here we are:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,265,151,544 1,264,944,697   7 HPFS/NTFS
/dev/sda3       1,265,152,000 1,459,709,951   194,557,952   7 HPFS/NTFS
/dev/sda4       1,459,711,998 1,953,523,711   493,811,714   5 Extended
/dev/sda5       1,459,712,000 1,933,598,719   473,886,720  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2004 MB, 2004877312 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     3,913,191     3,913,130   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2C5E21A75E216AB2                       ntfs       System Reserved               
/dev/sda2        A802238902235C16                       ntfs                                     
/dev/sda3        C0A2AB6BA2AB649E                       ntfs       Music                         
/dev/sda4: PTTYPE="dos" 
/dev/sda5        016bc578-99c1-46dc-b215-7792e27db2ea   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1874-5F34                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 016bc578-99c1-46dc-b215-7792e27db2ea
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 016bc578-99c1-46dc-b215-7792e27db2ea
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 016bc578-99c1-46dc-b215-7792e27db2ea
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=016bc578-99c1-46dc-b215-7792e27db2ea ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 016bc578-99c1-46dc-b215-7792e27db2ea
    echo    'Loading Linux 2.6.35-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=016bc578-99c1-46dc-b215-7792e27db2ea ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 016bc578-99c1-46dc-b215-7792e27db2ea
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 016bc578-99c1-46dc-b215-7792e27db2ea
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2c5e21a75e216ab2
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=016bc578-99c1-46dc-b215-7792e27db2ea /               ext4    errors=remount-ro 0       1

=================== sda5: Location of files loaded by Grub: ===================


 899.9GB: boot/grub/core.img
 855.0GB: boot/grub/grub.cfg
 747.9GB: boot/initrd.img-2.6.35-24-generic-pae
 899.9GB: boot/vmlinuz-2.6.35-24-generic-pae
 747.9GB: initrd.img
 899.9GB: vmlinuz
```

---

### Post by porkchop_001 on 2011-01-14
> **Quackers said:**
> +1 for the boot script.
Is this a Dell machine by any chance? With Dell Data Safe?

No - it's a custom machine I built myself :)

---

### Post by Quackers on 2011-01-14
Grub is looking for its boot files in sda6. There isn't a sda6 :-) The Ubuntu boot files are in sda5.
You will need to re-install grub.
You also have grldr in with the Windows boot files which shouldn't be there.
You may be able to delete that file from within Windows - not sure. If not you may need to repair the Windows bootloader, then re-install grub.
See what Rubi1200 thinks.

---

### Post by porkchop_001 on 2011-01-14
Okay sounds good - we'll await his response. Unless you can tell me how to re-install GRUB?

---

### Post by Quackers on 2011-01-14
Yes I can do that, but if you need to repair the Windows bootloader you will have to re-install grub again :-)
Either from the Ubuntu desktop or, if you can't get to that, from the Ubuntu Live cd desktop, you should open up a terminal and run these commands. It is easier to copy/paste them into the terminal, one line at a time, pressing enter after each line.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Then reboot. At this stage Ubuntu may boot directly. If it does open a terminal and run ```
sudo update-grub
``` and watch to see if your Windows Loader is picked up as grub.cfg is run.
If it is reboot and choose Windows from the new grub menu.

If you want to repair Windows mbr first, you will need a Windows 7 repair disc. Have you made one?
And does Windows boot now?

---

### Post by jjpcexpert on 2011-01-14
This is where testdisk really comes into it's own. Also when Vista's limited accounts come into their own.

Just run testdisk and recover the partition.

---

### Post by porkchop_001 on 2011-01-14
> **Quackers said:**
> Yes I can do that, but if you need to repair the Windows bootloader you will have to re-install grub again :-)
Either from the Ubuntu desktop or, if you can't get to that, from the Ubuntu Live cd desktop, you should open up a terminal and run these commands. It is easier to copy/paste them into the terminal, one line at a time, pressing enter after each line.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```Then reboot. At this stage Ubuntu may boot directly. If it does open a terminal and run ```
sudo update-grub
``` and watch to see if your Windows Loader is picked up as grub.cfg is run.
If it is reboot and choose Windows from the new grub menu.

If you want to repair Windows mbr first, you will need a Windows 7 repair disc. Have you made one?
And does Windows boot now?

Hi Quackers. This sadly didn't work. Once I executed the terminal commands, and re-booted my machine, it just turned into a black screen. There's no more 'no such partition' message. It just goes straight to the blank screen. Any clues?

---

### Post by porkchop_001 on 2011-01-14
> **jjpcexpert said:**
> This is where testdisk really comes into it's own. Also when Vista's limited accounts come into their own.

Just run testdisk and recover the partition.

Hi JJ. You'll have to explain this a tad mroe clearly. Where is testdisk? Is it a Windows application - or is it on Ubuntu? Should I be doing this prior to talking Quackers advice or should it be done once the GRUB issue has been fixed? Thanks :)

---

### Post by Rubi1200 on 2011-01-14
Hi,
testdisk can be used for, amongst other things, rebuilding the MBR. In your case, I do not think it is necessary.

There are 2 things I suggest you try now:

1. Boot the LiveCD and navigate to the root of the Windows drive and delete the **grldr** file there.

Reboot and see if that fixes the issue.

2. if above still gets you no further, then use the LiveCD and re-run and post the results of the boot info script again so we can see what has changed.

Thanks.

---

### Post by porkchop_001 on 2011-01-14
I can't find the grldr. A few places I Googled said what you said - that it's just lying in C drive hidden. When I navigate to it in Ubuntu, and I show hidden files, nothing shows up. Any ideas where it may be hidden? :(

---

### Post by wilee-nilee on 2011-01-14
Is this a western digital HD and have you ever had Ubuntu working on it, after rebooting?

---

### Post by porkchop_001 on 2011-01-14
I'm not sure if it's a Western Digital. I made it from custom parts just recently.

I've had Ubuntu on it before. I re-installed 10.10 last night and rebooted it, used Windows for a while, then when I restarted the machine again the 'no such partition' error came up.

---

### Post by Quackers on 2011-01-14
Hi, as Rubi1200 suggested, can you re-run the boot script please, so that we can see what has changed.

---

### Post by porkchop_001 on 2011-01-14
Sure. Here it is:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,265,151,544 1,264,944,697   7 HPFS/NTFS
/dev/sda3       1,265,152,000 1,459,709,951   194,557,952   7 HPFS/NTFS
/dev/sda4       1,459,711,998 1,953,523,711   493,811,714   5 Extended
/dev/sda5       1,459,712,000 1,933,598,719   473,886,720  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2004 MB, 2004877312 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     3,913,191     3,913,130   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2C5E21A75E216AB2                       ntfs       System Reserved               
/dev/sda2        A802238902235C16                       ntfs                                     
/dev/sda3        C0A2AB6BA2AB649E                       ntfs       Music                         
/dev/sda4: PTTYPE="dos" 
/dev/sda5        016bc578-99c1-46dc-b215-7792e27db2ea   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1874-5F34                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/A802238902235C16  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 016bc578-99c1-46dc-b215-7792e27db2ea
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 016bc578-99c1-46dc-b215-7792e27db2ea
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 016bc578-99c1-46dc-b215-7792e27db2ea
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=016bc578-99c1-46dc-b215-7792e27db2ea ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 016bc578-99c1-46dc-b215-7792e27db2ea
    echo    'Loading Linux 2.6.35-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=016bc578-99c1-46dc-b215-7792e27db2ea ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 016bc578-99c1-46dc-b215-7792e27db2ea
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 016bc578-99c1-46dc-b215-7792e27db2ea
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 2c5e21a75e216ab2
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=016bc578-99c1-46dc-b215-7792e27db2ea /               ext4    errors=remount-ro 0       1

=================== sda5: Location of files loaded by Grub: ===================


 899.9GB: boot/grub/core.img
 855.0GB: boot/grub/grub.cfg
 747.9GB: boot/initrd.img-2.6.35-24-generic-pae
 899.9GB: boot/vmlinuz-2.6.35-24-generic-pae
 747.9GB: initrd.img
 899.9GB: vmlinuz
```

---

### Post by porkchop_001 on 2011-01-14
Is there a way I can simply re-install Ubuntu and resolve this issue? Because I only had Ubuntu on for about 20min before I rebooted into Windows and, subsequently, ran into this problem - I haven't got anything valuable on there.

Is there an option I can change when installing 10.10 that can resolve this?

---

### Post by Quackers on 2011-01-14
Well, grub is in the right place, and it's looking for its boot files in the right place now. However, near the end of the boot script, the etc/fstab entry for /root is showing as /dev/sda6. This needs changing to /dev/sda5. The UUID quoted in etc/fstab for sda6 is actually the UUID for sda5, so that can be left.

I suspect the way to change this will involve chroot'ing into sda5 from the live cd desktop and editing the file.
I'll write some commands for you. I'll be back :-)

---

### Post by Quackers on 2011-01-14
Yes, you can re-install Ubuntu if you wish. Be sure to use the same /root partition (/dev/sda5). I also notice that you have no swap partition.

This will not solve the Windows booting problem. You still need to delete the grldr file, or run bootrec.exe /fixmbr from the Windows repair disc.

---

### Post by porkchop_001 on 2011-01-14
Okay. Well I'm not sure what to do first. I haven't got a Windows Repair disk so would you recommend removing the grldr file first? I didn't have much luck finding it before - I went into the C: directory and viewed the hidden files and was unable to find anything. Any ideas?

---

### Post by Quackers on 2011-01-14
How did you choose to view hidden files?

---

### Post by porkchop_001 on 2011-01-14
Ctrl+H

---

### Post by Quackers on 2011-01-14
Did that show the Windows boot files in the root of C: partition (ie /bootmgr /Boot/BCD)?

---

### Post by porkchop_001 on 2011-01-14
Not that I can see. Here's a screenshot of what I'm seeing at the moment (with the files hidden):

[http://img560.imageshack.us/i/screenshotaix.png/](http://img560.imageshack.us/i/screenshotaix.png/)

---

### Post by Quackers on 2011-01-14
You appear to be in a folder called PCAT. Go back to "boot"

---

### Post by porkchop_001 on 2011-01-14
Okay I'm now here:

[http://img502.imageshack.us/i/screenshot1ld.png/](http://img502.imageshack.us/i/screenshot1ld.png/)

Still no grldr file :(

---

### Post by Quackers on 2011-01-14
Now you seem to be in Windows/Boot/DVD/EFI/en-US
what does it look like in just Windows/Boot ?

---

### Post by porkchop_001 on 2011-01-14
In Windows/Boot there are four folders - DVD, EFI, Fonts, and PCAT

---

### Post by Quackers on 2011-01-14
Hmm, here's mine using Nautilus

---

### Post by porkchop_001 on 2011-01-14
> **Quackers said:**
> Well, grub is in the right place, and it's looking for its boot files in the right place now. However, near the end of the boot script, the etc/fstab entry for /root is showing as /dev/sda6. This needs changing to /dev/sda5. The UUID quoted in etc/fstab for sda6 is actually the UUID for sda5, so that can be left.

I suspect the way to change this will involve chroot'ing into sda5 from the live cd desktop and editing the file.
I'll write some commands for you. I'll be back :-)

I just read this ^^^^ (I must have skipped over it before - sorry!). Is it still worth trying to do or shoudl I just go ahead and re-install everything? I'm now in the process of copying my Windows data (music, pictures etc.) onto an external HDD so once that's done maybe I should just wipe the entire machine and start with fresh installations of both Windows and Ubuntu?

---

### Post by Quackers on 2011-01-14
Well that would certainly do it :-)
Do you have a Windows installation disc? Or recovery dvd's?

---

### Post by porkchop_001 on 2011-01-14
Sadly no - I have neither. Is that an issue? :( my brother has a (legal) version of Windows that I made an ISO of before he left for overseas. Is that of use?

---

### Post by Quackers on 2011-01-14
I'm not sure whether that will install. I suspect not.

---

### Post by porkchop_001 on 2011-01-14
Okay - case closed then. I'll let you attend to the needs of others. Thanks so much for all your help Quackers. I'll go ahead and backup my data - then do a fresh install. Makes sense...a new year, a fresh install ;) thanks again ;)

---

### Post by Quackers on 2011-01-14
You can download Win 7 repair discs from here

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

which can repair the mbr in both Vista and Win 7.

---

### Post by porkchop_001 on 2011-01-14
Okay - will check it out

---

### Post by Quackers on 2011-01-14
Yep, have a think about things.
There's no need to trash Windows. It's definitely fixable. There are options :-)
Bedtime for me now :-)

---

