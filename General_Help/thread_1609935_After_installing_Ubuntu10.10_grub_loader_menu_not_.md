---
title: "After installing Ubuntu10.10 grub loader menu not showing"
date: 2010-10-31
forum: General Help
---

### Post by boss_aadi on 2010-10-31
Hi All,

After installing Ubuntu 10.10 dual boot with Windows 7(not inside Windows 7) and restarting I come to a blank screen with a blinking underscore.I assume the GRUB boot loader is missing or i installed Grub in some other partitions.
Now i unable to enter in to Windows 7 OS.

Please Help...
Thank you...

---

### Post by boss_aadi on 2010-10-31
Hi All,

After installing Ubuntu 10.10 dual boot with Windows 7(not inside Windows 7) and restarting I come to a blank screen with a blinking underscore(Now i am able to enter into Ubuntu Only).I assume the GRUB boot loader is missing or i installed Grub in some other partitions.
Now i unable to enter in to Windows 7 OS.

Please Help...
Thank you...

---

### Post by Quackers on 2010-10-31
It will give a better idea of your system if you can boot from the cd and select "try Ubuntu" then, after getting an internet connection go to the site below and download the boot script to your dekstop, then run it using the command given on that site. This will produce a Results.txt file on your desktop. Please copy the contents of that file and paste it in between code tags in your next post. For code tags select New Reply then click on the # symbol in the toolbar.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by uRock on 2010-10-31
Duplicate threads merged. Please do not create duplicate threads.

Thanks,
uRock

---

### Post by boss_aadi on 2010-10-31
Thabks for your reply...i got RESULT.TXT

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for (,msdos8)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 473031696 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848    61,442,047    61,235,200   7 HPFS/NTFS
/dev/sda3          61,442,048   271,157,247   209,715,200   7 HPFS/NTFS
/dev/sda4         271,159,294   488,396,799   217,237,506   f W95 Ext d (LBA)
/dev/sda5         271,159,296   353,079,295    81,920,000   7 HPFS/NTFS
/dev/sda6         353,081,344   435,001,343    81,920,000   7 HPFS/NTFS
/dev/sda7         435,003,392   436,955,135     1,951,744  82 Linux swap / Solaris
/dev/sda8         436,957,184   488,396,799    51,439,616  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        18A22F06A22EE848                       ntfs       System Reserved               
/dev/sda2        5A724B54724B33D3                       ntfs                                     
/dev/sda3        AA6698196697E3FB                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        8402A18602A17DB4                       ntfs       New Volume                    
/dev/sda6        8C1CB29E1CB2832E                       ntfs       New Volume                    
/dev/sda7        5dce0011-4120-48e6-9050-7a8a98637a01   swap                                     
/dev/sda8        86ddc697-8273-4317-b4dc-8812176913a1   ext4                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /media/sda2              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /media/sda3              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /media/sda5              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6        /media/sda6              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda8/boot/grub/menu.lst: ===========================

title Windows 7
root(hd0,0)
savedefault
makeactive
chainloader   +1

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 86ddc697-8273-4317-b4dc-8812176913a1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 86ddc697-8273-4317-b4dc-8812176913a1
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=15
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
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 86ddc697-8273-4317-b4dc-8812176913a1
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=86ddc697-8273-4317-b4dc-8812176913a1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 86ddc697-8273-4317-b4dc-8812176913a1
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=86ddc697-8273-4317-b4dc-8812176913a1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry “Windows 7&#8243; {
set root=(hd0,2)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 86ddc697-8273-4317-b4dc-8812176913a1
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 86ddc697-8273-4317-b4dc-8812176913a1
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda8 during installation
UUID=86ddc697-8273-4317-b4dc-8812176913a1  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda7 during installation
UUID=5dce0011-4120-48e6-9050-7a8a98637a01  none         swap  sw                   0  0  
/dev/sda2                                  /media/sda2  ntfs  defaults             0  0  
/dev/sda3                                  /media/sda3  ntfs  defaults             0  0  
/dev/sda5                                  /media/sda5  ntfs  defaults             0  0  
/dev/sda6                                  /media/sda6  ntfs  defaults             0  0  

=================== sda8: Location of files loaded by Grub: ===================


 228.1GB: boot/grub/core.img
 235.5GB: boot/grub/grub.cfg
 235.2GB: boot/grub/menu.lst
 229.1GB: boot/initrd.img-2.6.35-22-generic
 229.9GB: boot/vmlinuz-2.6.35-22-generic
 229.1GB: initrd.img
 229.9GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by Quackers on 2010-10-31
Grub2 is installed in the mbr of sda which is where it should be. However it seems that at least a part of grub (legacy?) is installed in sda1 (grldr). Grub2 is looking for its boot files in sda8, which is fine. However   /boot/grub/menu.lst (which is a part of grub legacy (the old version of grub) is also in that partition.

I think it may be best if you follow the guide below with regard to purging and re-installing grub.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

By all means wait for a second opinion, or better options which may be offered :-)

---

### Post by boss_aadi on 2010-11-13
> **Quackers said:**
> Grub2 is installed in the mbr of sda which is where it should be. However it seems that at least a part of grub (legacy?) is installed in sda1 (grldr). Grub2 is looking for its boot files in sda8, which is fine. However   /boot/grub/menu.lst (which is a part of grub legacy (the old version of grub) is also in that partition.

I think it may be best if you follow the guide below with regard to purging and re-installing grub.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

By all means wait for a second opinion, or better options which may be offered :-)

Thank you...

---

### Post by Quackers on 2010-11-13
You're welcome. Is everything up and running now? :-)

---

### Post by boss_aadi on 2010-11-13
> **Quackers said:**
> You're welcome. Is everything up and running now? :-)

Now i able to view win7 OS in GRUB Menu, but when i am trying to open it, it is showing BOOTMGR Missing...

---

