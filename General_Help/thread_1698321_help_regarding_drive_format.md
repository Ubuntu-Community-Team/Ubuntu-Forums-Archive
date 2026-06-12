---
title: "help regarding drive format"
date: 2011-03-02
forum: General Help
---

### Post by debd on 2011-03-02
I have a triple boot harddisk.
win xp on C drive, win7 on E drive and Ubuntu on J drive(in windows)

now that I never use win7, I want to format that partition.

In grub boot menu, their's a option named "win7 loader (on dev/sda1)" which takes me to the win7 boot menu. then selecting "previous versions of windows"
takes me to the xp boot menu.

now, if I format the win7 partition (i.e. the E drive) will i be able to navigate to the xp boot menu from grub?

here is the boot_script_info result.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #11 for (,msdos11)/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM 
                       

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda13: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda14: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,432,559    61,432,497   7 HPFS/NTFS
/dev/sda2          61,432,621   976,751,999   915,319,379   f W95 Ext d (LBA)
/dev/sda5          61,432,623   122,865,119    61,432,497   7 HPFS/NTFS
/dev/sda6         122,865,183   245,746,304   122,881,122   7 HPFS/NTFS
/dev/sda7         245,746,368   368,627,489   122,881,122   7 HPFS/NTFS
/dev/sda8         368,627,553   491,508,674   122,881,122   7 HPFS/NTFS
/dev/sda9         491,508,738   614,389,859   122,881,122   7 HPFS/NTFS
/dev/sda10        737,271,108   976,751,999   239,480,892   7 HPFS/NTFS
/dev/sda11        614,391,808   622,202,879     7,811,072  83 Linux
/dev/sda12        622,204,928   631,967,743     9,762,816  83 Linux
/dev/sda13        631,969,792   635,873,279     3,903,488  82 Linux swap / Solaris
/dev/sda14        635,875,328   737,269,759   101,394,432  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       06749063749056F1                       ntfs       Entertainment                 
/dev/sda11       d82aa4c0-6920-4927-a267-c3663576583a   ext4                                     
/dev/sda12       febf4418-67b4-4346-bfee-9cffc6b79179   ext4                                     
/dev/sda13       0a9ce76c-149a-421c-8346-42d172eed4ea   swap                                     
/dev/sda14       b3d060a1-750a-4e5c-90eb-1193c0ab072d   ext4                                     
/dev/sda1        780CB6D30CB68C1E                       ntfs       windows xp                    
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2424689824686EAC                       ntfs       windows7                      
/dev/sda6        1244702644700F2B                       ntfs       softwares                     
/dev/sda7        A63875EE3875BDBD                       ntfs       games                         
/dev/sda8        2ADC7C02DC7BC69B                       ntfs       E space 2                     
/dev/sda9        984CF9224CF8FC36                       ntfs       new installtions here         
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda14       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda11       /boot                    ext4       (rw,commit=0)
/dev/sda12       /home                    ext4       (rw,user_xattr,commit=0)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT /USEPMTIMER /TUTAG=B9GBXN /KERNEL=TUKernel.exe
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /NOEXECUTE=OPTIN /FASTDETECT /USEPMTIMER /TUTAG=B9GBXN-BAK


============================= sda11/grub/grub.cfg: =============================

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
set root='(hd0,msdos14)'
search --no-floppy --fs-uuid --set b3d060a1-750a-4e5c-90eb-1193c0ab072d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set d82aa4c0-6920-4927-a267-c3663576583a
set locale_dir=($root)/grub/locale
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
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set d82aa4c0-6920-4927-a267-c3663576583a
	linux	/vmlinuz-2.6.35-22-generic root=UUID=b3d060a1-750a-4e5c-90eb-1193c0ab072d ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set d82aa4c0-6920-4927-a267-c3663576583a
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=b3d060a1-750a-4e5c-90eb-1193c0ab072d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set d82aa4c0-6920-4927-a267-c3663576583a
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos11)'
	search --no-floppy --fs-uuid --set d82aa4c0-6920-4927-a267-c3663576583a
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 780cb6d30cb68c1e
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

=================== sda11: Location of files loaded by Grub: ===================


 314.7GB: grub/core.img
 314.7GB: grub/grub.cfg
 314.7GB: initrd.img-2.6.35-22-generic
 314.7GB: vmlinuz-2.6.35-22-generic

=============================== sda14/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda14      /               ext4    errors=remount-ro 0       1
/dev/sda11      /boot           ext4    defaults        0       2
# Commented out by Dropbox
# /dev/sda12      /home           ext4    defaults        0       2
# swap was on /dev/sda13 during installation
UUID=0a9ce76c-149a-421c-8346-42d172eed4ea none            swap    sw              0       0
/dev/sda12 /home ext4 defaults,user_xattr 0 2

=================== sda14: Location of files loaded by Grub: ===================


 325.7GB: initrd.img
 325.7GB: vmlinuz
```

I'll be grateful for any little help .

---

### Post by veggen on 2011-03-02
I don't think Grub will be able to handle that automatically i.e. you'd have to do some configuration to make it work... But I don't know what it might involve :(
There's been a lot of forum threads about similar issues (making Grub see XP existing install) though, so try searching.

---

### Post by coffeecat on 2011-03-02
> **debd said:**
> now, if I format the win7 partition (i.e. the E drive) will i be able to navigate to the xp boot menu from grub?

No! Hold everything! :)

The problem is not with grub, but with the way you have installed your two Windows systems. Windows 7 is on a primary partition, sda1, but XP is on a logical partition, sda5 or sda6, it's not quite clear which - you have a complex setup. The only way that Windows can work from a logical partition is to have its boot files on a primary partition. Your Windows XP boot files are in the Windows 7 sda1 partition. Format the Windows 7 sda1 partition and you will lose your Windows XP boot files => unbootable Windows XP.

You'll need either to reinstall XP to a primary partition or create a small primary partition just for the XP boot files. The latter is possible, but I'm not exactly sure how you would go about it. This link might help:

[http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition](http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition)

---

### Post by veggen on 2011-03-02
Isn't there a way (using XP installation disk) to restore his boot files?
...just asking...

---

### Post by coffeecat on 2011-03-02
> **veggen said:**
> Isn't there a way (using XP installation disk) to restore his boot files?
...just asking...

Possibly, but only if the OP creates a primary partition for them. They won't be able to restore the boot files to sda5 or sda6 because both of those are logical partitions. Or rather, the boot files could probably be copied over but it wouldn't work - Windows cannot boot from a logical partition. And anyway, things are more complex than that. Look at the boot script output. For sda5 and sda6, it says:

```
 Boot sector info:  According to the info in the boot sector, sda5 starts at sector 63.
```and 

```
 Boot sector info:  According to the info in the boot sector, sda6 starts at sector 63.
```Sector 63 is in sda1, where the boot files are. Why is XP on two logical partitions? I don't know. We need more information from the OP.

---

### Post by debd on 2011-03-02
in windows, E drive is the next drive to C drive. I dont quite understand why sda2 doesn't have win7 as in the boot_script info.

 I had the xp installation at the earliest on C: then I installed win7 on E: which both are 30 gb drives.  (the rest are 60 gb partitions exept a 110gb one)
what I believe is : the win7 installation overwrote the xp mbr and then somehow create a link to the xp btmngr that actually gives the opt to boot into xp. ..well m goin nuts...its more like a thiesis :)

remember I said : "In grub boot menu, their's a option named "win7 loader (on dev/sda1)" which takes me to the win7 boot menu. then selecting "previous versions of windows"
takes me to the xp boot menu.

---

### Post by debd on 2011-03-02
in windows, E drive is the next drive to C drive. I dont quite understand why sda2 doesn't have win7 as in the boot_script info.

 I had the xp installation at the earliest on C: then I installed win7 on E: which both are 30 gb drives.  (the rest are 60 gb partitions exept a 110gb one)
what I believe is : the win7 installation overwrote the xp mbr and then somehow create a link to the xp btmngr that actually gives the opt to boot into xp. ..well m goin nuts...its more like a thiesis :)

remember I said : "In grub boot menu, their's a option named "win7 loader (on dev/sda1)" which takes me to the win7 boot menu. then selecting "previous versions of windows"
takes me to the xp boot menu.

---

### Post by Mark Phelps on 2011-03-02
What generally happens, when you install Win7 after a previous Windows OS, is that Win7 writes its boot files to the partition containing that older OS.  From then on, when you boot, you get a Windows menu that will list both Win7 and the older OS.

Grub simply points to that partition and passes control off to the Windows boot loader -- which displays the OS selection menu.

There's no way to have GRUB point INSIDE that menu to a particular selection.

However, if you have a Windows XP CD, you can do the following:
1)Remove the Win7 partition
2)Boot using the WinXP CD and run "fixmbr" and "fixboot"

Those will rewrite the MBR and XP boot files so that, after that, you should be able to boot into the XP partition.

---

### Post by debd on 2011-03-02
after running fixmbr and fixboot, shall I have to restore grub?

btw, after going through tutorials about rewriting the grub mbr, I just wanted to do a few initial steps; and when I tried to run grub in terminal it said grub wasn't installed! though the grub bootmenu exits. what's the deal? it tells me to install grub using apt-get. will it do any harm to the existing grub boot menu?

---

