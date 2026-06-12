---
title: "grub clobbered after upgrade to 11.4"
date: 2011-05-14
forum: General Help
---

### Post by nrrdnull on 2011-05-14
I recently upgraded to 11.4 on my dual Windows and Ubuntu laptop, and it broke something to do with GRUB. I  wasn't able to boot either Windows XP or the upgraded Ubuntu  installation; I only received an error message about an unset variable  that GRUB needed.  I used a live CD to reinstall GRUB on /dev/sda and  now I can boot into Ubuntu. Yay!  But Windows is missing from my bootable OS  list.   Boo!  I'm sorry I'm being a bit vague here, but I'm new to boot/grub/MBR  disasters.

I took the advice given in someone else's thread and ran 'boot_info_script055.sh'; I received the following output:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2can.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub 0.97 in the file /ubuntu.bin looks at sector 
                       168916901 of the same hard drive for the stage2 file. 
                       A stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #6 for /boot/grub/menu.lst.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /NTLDR /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 168916901 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /COMMAND.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 213102225.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda6 and 
                       looks at sector 168916901 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    98,301,734    98,301,672   7 HPFS/NTFS
/dev/sda2         224,879,760   234,435,599     9,555,840  12 Compaq diagnostics
/dev/sda3          98,301,859   224,877,869   126,576,011   5 Extended
/dev/sda5         213,102,225   224,877,869    11,775,645   b W95 FAT32
/dev/sda6          98,301,861   204,716,294   106,414,434  83 Linux
/dev/sda7         204,716,358   213,102,224     8,385,867  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        42F8AB43F8AB3457                       ntfs       Local Disk                    
/dev/sda2        1177-A580                              vfat       SERVICEV001                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        465C-7E3D                              vfat       OS SHARE                      
/dev/sda6        4eb6ae88-960a-4fd0-8853-3b5a381bc045   ext2                                     
/dev/sda7        4200e5de-4e43-4452-90d1-b29743ad11a8   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext2       (rw,errors=remount-ro)
/dev/sda5        /media/OS SHARE          vfat       (rw)
/dev/sda1        /media/Windows           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\ubuntu.bin="Ubuntu Linux" 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\ 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\ = "PC-DOS" 

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 4eb6ae88-960a-4fd0-8853-3b5a381bc045
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 4eb6ae88-960a-4fd0-8853-3b5a381bc045
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 4eb6ae88-960a-4fd0-8853-3b5a381bc045
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=4eb6ae88-960a-4fd0-8853-3b5a381bc045 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 4eb6ae88-960a-4fd0-8853-3b5a381bc045
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=4eb6ae88-960a-4fd0-8853-3b5a381bc045 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 4eb6ae88-960a-4fd0-8853-3b5a381bc045
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=4eb6ae88-960a-4fd0-8853-3b5a381bc045 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 4eb6ae88-960a-4fd0-8853-3b5a381bc045
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=4eb6ae88-960a-4fd0-8853-3b5a381bc045 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 4eb6ae88-960a-4fd0-8853-3b5a381bc045
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 4eb6ae88-960a-4fd0-8853-3b5a381bc045
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
/dev/sda6       /               ext2    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=4200e5de-4e43-4452-90d1-b29743ad11a8 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  80.8GB: boot/grub/core.img
  80.9GB: boot/grub/grub.cfg
  80.7GB: boot/initrd.img-2.6.35-28-generic
  80.7GB: boot/initrd.img-2.6.38-8-generic
  80.7GB: boot/vmlinuz-2.6.35-28-generic
  80.7GB: boot/vmlinuz-2.6.38-8-generic
  80.7GB: initrd.img
  80.7GB: initrd.img.old
  80.7GB: vmlinuz
  80.7GB: vmlinuz.old

```Does this problem sound fixable?  I'd hate to have to do a complete reinstall of two OS's.

---

### Post by wilee-nilee on 2011-05-14
So you have a number of problems you have grub-legacy installed or showing in the XP, and a additional file I don't recognise. You also have grub-legacy showing in the Ubuntu. All probably fixable lets get some opinions of others familiar in this area.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:    [B] Grub 0.97 in the file /ubuntu.bin looks at sector 
                       168916901 of the same hard drive for the stage2 file. 
                       A stage2 file is at this location on /dev/sda. Stage2 
                       looks on partition #6 for /boot/grub/menu.lst.[/B]
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /NTLDR /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type: [B] Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 168916901 of the same hard drive for 
                       the stage2 file. A stage2 file is [/B]at this location on 
                     **  /dev/sda. Stage2 looks on **partition #6 for 
                      ** /boot/grub/menu.lst. No errors **found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /COMMAND.COM

 
 

sda6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  [B]Grub 0.97 is installed in the boot sector of sda6 and 
                       looks at sector 168916901 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.[/B]
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.

---

### Post by nrrdnull on 2011-05-14
Maybe I can clear up some confusion, too.  I have a windows partition (/dev/sda1), the Lenovo-installed Windows recovery partition (I believe this is /dev/sda2).  /dev/sda5 is a fat32 partition I use to transfer files between my OS's (now not needed since I have altered XP to be able to read and write to ext2/ext3 filesystems) and Ubuntu mounted on /dev/sda6.

---

### Post by wilee-nilee on 2011-05-14
> **nrrdnull said:**
> Maybe I can clear up some confusion, too.  I have a windows partition (/dev/sda1), the Lenovo-installed Windows recovery partition (I believe this is /dev/sda2).  /dev/sda5 is a fat32 partition I use to transfer files between my OS's (now not needed since I have altered XP to be able to read and write to ext2/ext3 filesystems) and Ubuntu mounted on /dev/sda6.

That will help thanks, you will need to remove all the grub legacy as highlighted to have XP work, lets have others take a look. You also have this grub-legacy=Grub0.97 indicated in sda6.

Do you have a XP install cd?, and a Ubuntu live cd of Natty?

---

### Post by nrrdnull on 2011-05-14
> **wilee-nilee said:**
> 
Do you have a XP install cd?, and a Ubuntu live cd of Natty?

I have a live USB thumbdrive of Natty and I believe I have my XP install CDs somewhere.

---

### Post by wilee-nilee on 2011-05-14
> **nrrdnull said:**
> I have a live USB thumbdrive of Natty and I believe I have my XP install CDs somewhere.

You will more than likely need both when we get the Pro advice, this is a somewhat tricky fix, So you want when you get the correct info to read carefully.

Tricky really in the detail, if the XP disc is used you will be moving bootflags, with the gparted partitioner on the Natty cd, or from a install of gparted in the Natty, install.

There are manual ways to remove the grub from the two XP partitions this is all depending on factors of the helpers instructions.

---

### Post by drs305 on 2011-05-14
Try booting into Windows from the Grub prompt (press 'c' from the Grub menu, hold SHIFT during boot if you don't get the menu):

```
insmod ntfs
set root=(hd0,1)
drivemap -s (hd0) ${root}  # Note root braces, not parens
chainloader +1
boot
```

I don't know if having Grub .97 in the PBR will affect the boot.

---

### Post by nrrdnull on 2011-05-14
I was able to get into the grub prompt and enter your commands. The boot command produced the 'old' grub menu I had, I selected Windows XP and it booted successfully into XP. So far so good!

Edit: Just to be clear, rebooting from Windows brings me to the 'new' grub menu and I cannot from there boot back into Windows.

---

### Post by drs305 on 2011-05-14
> **nrrdnull said:**
> I was able to get into the grub prompt and enter your commands. The boot command produced the 'old' grub menu I had, I selected Windows XP and it booted successfully into XP. So far so good!

Edit: Just to be clear, rebooting from Windows brings me to the 'new' grub menu and I cannot from there boot back into Windows.

Ok, what I suspect is happening is that when you entered the commands, the system was picking up the old Grub menu installed in the *partition* boot record of sda1. 

So apparently Windows needs to be restored there using a Windows repair disk. Again, I am not much of a Windows user, so I don't want to venture too far on this subject. You most likely need to run one or both of the repair commands from a Windows repair disk. 

Repairing Windows may remove Grub, but that is easily restored. And when you do that, only restore it to the MBR and not to any of the partitions.

---

### Post by nrrdnull on 2011-05-15
> **drs305 said:**
> Repairing Windows may remove Grub, but that is easily restored. And when you do that, only restore it to the MBR and not to any of the partitions.

Assuming this happens (and all goes well) how do I restore Grub to the master boot record?  This, I believe, is what I attempted originally which I bungled.

---

