---
title: "Installing Grub?"
date: 2010-11-20
forum: General Help
---

### Post by Bob555 on 2010-11-20
When I first installed ubuntu I had 2 hard drves, 1 with a single xp partition, and another with 2 partitions (1 with xp and 1 new one for ubuntu to be installed on). I just left the bootloader on the default which happened to be the first hard drive, even though ubuntu was installed on the other one.  This became a problem when I upgraded my system cause it doesn't have IDE ports, so I can't use that drive now.  I tried installing grub a few ways (using the live cd). And now whenever I boot up I get taken to a grub prompt, no menu or anything.  At this point the only thing I can think of is to just reinstall ubuntu and let the insaller do it, but I don't want to reinstall/reconfigure everything again. Any ideas?

---

### Post by wilee-nilee on 2010-11-20
Post the bootscript in my signature. when you post the text click on the # in the reply panel and put the text in between the code tags

---

### Post by Bob555 on 2010-11-20
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

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
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 570738377 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

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

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2    *        112,640    18,171,903    18,059,264   7 HPFS/NTFS
/dev/sda3          18,171,904 1,953,521,663 1,935,349,760   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   441,353,744   441,353,682   7 HPFS/NTFS
/dev/sdb2         441,353,745   622,936,439   181,582,695  83 Linux
/dev/sdb3         622,936,440   625,137,344     2,200,905  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 999 MB, 999816704 bytes
255 heads, 63 sectors/track, 121 cylinders, total 1952767 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     1,952,766     1,952,704   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07DA-0817                              vfat       DellUtility                   
/dev/sda2        04582B63582B532A                       ntfs       RECOVERY                      
/dev/sda3        9E482E5D482E3505                       ntfs       OS                            
/dev/sda: PTTYPE="dos" 
/dev/sdb1        473A756305019A16                       ntfs                                     
/dev/sdb2        d06dfac6-2444-4690-afee-562fb7ff70b0   ext3                                     
/dev/sdb3        8e806990-bc35-4df7-9990-2199b3c6cb25   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        C0BA-D50F                              vfat       PIBB_XP                       
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set d06dfac6-2444-4690-afee-562fb7ff70b0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set d06dfac6-2444-4690-afee-562fb7ff70b0
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set d06dfac6-2444-4690-afee-562fb7ff70b0
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d06dfac6-2444-4690-afee-562fb7ff70b0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set d06dfac6-2444-4690-afee-562fb7ff70b0
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d06dfac6-2444-4690-afee-562fb7ff70b0 ro single 
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
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set d06dfac6-2444-4690-afee-562fb7ff70b0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set d06dfac6-2444-4690-afee-562fb7ff70b0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set dc3c245c3c243444
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 473a756305019a16
    drivemap -s (hd0) ${root}
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

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=d06dfac6-2444-4690-afee-562fb7ff70b0 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=8e806990-bc35-4df7-9990-2199b3c6cb25 none            swap    sw              0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


=================== sdb2: Location of files loaded by Grub: ===================


 292.1GB: boot/grub/core.img
 292.2GB: boot/grub/grub.cfg
 292.2GB: boot/grub/stage2
 292.2GB: boot/initrd.img-2.6.35-22-generic
 293.0GB: boot/vmlinuz-2.6.35-22-generic
 292.2GB: initrd.img
 293.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 

```

---

### Post by wilee-nilee on 2010-11-20
sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 570738377 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/**grub/grub.cfg** /etc/fstab /boot/[B]grub/core.img
[/B]

So you have the grub-legacy in the highlights and grub2. You also have some other problems. But this is probably fixable all around if everything is in place. 

For me could you say exactly what is booting as of now. It looks like you have XP and W7 so I personally want to get enough information, and others help since by and large we try to work together on this stuff.

---

### Post by wilee-nilee on 2010-11-20
Put sda first to be read in the bios it has the MS bootloader and see if that works. I recognize you can't boot anything, it looks like sda is first to be read but, sometimes the script can misread some things.

Just trying to see whats going on here.

---

### Post by Bob555 on 2010-11-20
Strangely it now works now, I did  what I did before at [http://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](http://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) and it worked this time. That boot script now says I have grub 2 installed, which I guess is why it wasn't working before. But I don't know what I did wrong the first time.

---

### Post by wilee-nilee on 2010-11-20
> **Bob555 said:**
> Strangely it now works now, I did  what I did before at [http://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](http://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) and it worked this time. That boot script now says I have grub 2 installed, which I guess is why it wasn't working before. But I don't know what I did wrong the first time.

I think you used a earlier cd with grub legacy and that would of caused the dual grub types as I posted.

Glad its working but I would run that script for your self to make sure grub-legacy is out of the sdb2 area I highlighted.

---

