---
title: "Partition table problem Grub2"
date: 2011-09-22
forum: General Help
---

### Post by valllllll2000 on 2011-09-22
Hi,
I have done something to my partitions I don't know what exactly but Windows doesn't boot anymore. It appeared in the list at boot: I have windows and ubuntu 11.04. First the windows wouldn't boot so I did update-grub and now windows is not on the list. Windows files are still there and ubuntu boots normally so what can I do to solve that (I want to try something before having to reinstall everything. Is there a way?

Here are the results of the sfdisk command:
ubuntu@ubuntu:~$ sudo sfdisk -luS

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048    206847     204800   7  HPFS/NTFS
/dev/sda2        206848 507270071  507063224   7  HPFS/NTFS
/dev/sda3     507271166 947263487  439992322   5  Extended
/dev/sda4     947263488 976771071   29507584   7  HPFS/NTFS
/dev/sda5     507271168 929343487  422072320  83  Linux
/dev/sda6     929345536 947263487   17917952  82  Linux swap / Solaris

and my /etc/default grub contains:
GRUB_DEFAULT=5
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=20
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

thanks a lot in advance

---

### Post by oldfred on 2011-09-22
This should show your entire configuration:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by valllllll2000 on 2011-09-23
wow thanks great script, here are my results

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: tipo de sistema de ficheros '' desconocido

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   507,270,071   507,063,224   7 NTFS / exFAT / HPFS
/dev/sda3         507,271,166   947,263,487   439,992,322   5 Extended
/dev/sda5         507,271,168   929,343,487   422,072,320  83 Linux
/dev/sda6         929,345,536   947,263,487    17,917,952  82 Linux swap / Solaris
/dev/sda4         947,263,488   976,771,071    29,507,584   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disco /dev/sdc: 3980 MB, 3980394496 bytes
9 cabezas, 9 sectores/pista, 95977 cilindros, 7774208 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          8,064     7,774,207     7,766,144   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        CCE8A9EEE8A9D6CC                       ntfs       OS
/dev/sda4        6C881B1A881AE1FE                       ntfs       HP_RECOVERY
/dev/sda5        450c3618-b8f1-4c80-b767-6018e086e409   ext4       
/dev/sda6        ec2f0f7b-769f-46db-8957-f8e8b7f7de35   swap       
/dev/sdc1        B805-7488                              vfat       KINGSTON

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set default="5"
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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 450c3618-b8f1-4c80-b767-6018e086e409
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 450c3618-b8f1-4c80-b767-6018e086e409
set locale_dir=($root)/boot/grub/locale
set lang=fr_FR
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=20
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
menuentry 'Ubuntu, avec Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 450c3618-b8f1-4c80-b767-6018e086e409
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=450c3618-b8f1-4c80-b767-6018e086e409 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, avec Linux 2.6.38-11-generic (mode de dépannage)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 450c3618-b8f1-4c80-b767-6018e086e409
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=450c3618-b8f1-4c80-b767-6018e086e409 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, avec Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 450c3618-b8f1-4c80-b767-6018e086e409
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=450c3618-b8f1-4c80-b767-6018e086e409 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, avec Linux 2.6.38-10-generic (mode de dépannage)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 450c3618-b8f1-4c80-b767-6018e086e409
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=450c3618-b8f1-4c80-b767-6018e086e409 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, avec Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 450c3618-b8f1-4c80-b767-6018e086e409
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=450c3618-b8f1-4c80-b767-6018e086e409 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, avec Linux 2.6.38-8-generic (mode de dépannage)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 450c3618-b8f1-4c80-b767-6018e086e409
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=450c3618-b8f1-4c80-b767-6018e086e409 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, avec Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 450c3618-b8f1-4c80-b767-6018e086e409
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=450c3618-b8f1-4c80-b767-6018e086e409 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, avec Linux 2.6.35-28-generic (mode de dépannage)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 450c3618-b8f1-4c80-b767-6018e086e409
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=450c3618-b8f1-4c80-b767-6018e086e409 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 450c3618-b8f1-4c80-b767-6018e086e409
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 450c3618-b8f1-4c80-b767-6018e086e409
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos4)'
	search --no-floppy --fs-uuid --set=root 6C881B1A881AE1FE
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
# Commented out by Dropbox
# UUID=450c3618-b8f1-4c80-b767-6018e086e409 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ec2f0f7b-769f-46db-8957-f8e8b7f7de35 none            swap    sw              0       0
UUID=450c3618-b8f1-4c80-b767-6018e086e409 / ext4 errors=remount-ro,user_xattr 0 1
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 414.013969421 = 444.544114688  boot/grub/core.img                             1
 280.472400665 = 301.154947072  boot/grub/grub.cfg                             1
 242.948242188 = 260.863688704  boot/initrd.img-2.6.35-28-generic              2
 244.554271698 = 262.588149760  boot/initrd.img-2.6.38-10-generic              2
 374.640209198 = 402.266861568  boot/initrd.img-2.6.38-11-generic              2
 243.640205383 = 261.606678528  boot/initrd.img-2.6.38-8-generic               2
 242.479492188 = 260.360372224  boot/vmlinuz-2.6.35-28-generic                 2
 243.815742493 = 261.795160064  boot/vmlinuz-2.6.38-10-generic                 1
 374.550117493 = 402.170126336  boot/vmlinuz-2.6.38-11-generic                 1
 248.460269928 = 266.782183424  boot/vmlinuz-2.6.38-8-generic                  1
 374.640209198 = 402.266861568  initrd.img                                     2
 244.554271698 = 262.588149760  initrd.img.old                                 2
 374.550117493 = 402.170126336  vmlinuz                                        1
 243.815742493 = 261.795160064  vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by oldfred on 2011-09-23
It has a problem with the sda1 partition which is the Windows 100MB boot/recovery partition. Since that is the recovery partition you need a separate Windows repairCD. Did you create one, or know someone else with Windows? I would try chkdsk on sda1 first.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

The other choice would be to install the boot files into the sda2 partition which would in effect obsolete the separate /boot Windows partition. But you need the Windows repair CD to do that and have to move the boot flag or active partition from sda1 to sda2.

---

### Post by valllllll2000 on 2011-09-23
> **oldfred said:**
> 

The other choice would be to install the boot files into the sda2 partition which would in effect obsolete the separate /boot Windows partition. But you need the Windows repair CD to do that and have to move the boot flag or active partition from sda1 to sda2.

I have a windows 7 recovery Cd for that computer(luckily I did it) but could you explain more what I have to do? Will I lose all the windows programs and will have to reinstall it all? Also will I lose the hidden recovery partition?

thanks a lot

---

### Post by oldfred on 2011-09-23
Chkdsk is just a Windows repair of a NTFS partition with issues. It often solves issues. Your main install is in sda2 and it looks like it mounts and is ok, so you should be able to see it from Ubuntu or a liveCD. The hidden boot/recovery partition is not essential and you can repair the main install and boot from that. Part of the reason Windows 7 has a separate boot is so a user can encrypt the main partition as the initial boot files cannot be encrypted. 

Of course you should have good backups.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by valllllll2000 on 2011-09-24
thanks oldfred but I still don't understand what I have to do. I have checked and chkdisk is not available in the package manager it's only for windows but my windows doesn't start. The windows repair partition is working and I tried the "solve start up problems" or some option like that but it says "we can't solve the problem". How can I make the normal widows partition bootable instead of the repair one?

EDIT: I used the gparted tool (it doesn't work with live cd  so I used it with my normal ubuntu). I made sda2 bootable insteaad of sd1 but windows still doesn't appear on the list at start up. Why???

---

### Post by oldfred on 2011-09-24
From the Window repair CD are you not getting to a repair screen?

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  (have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by valllllll2000 on 2011-09-25
thanks oldfred I have finally managed to solve my boot problems and can now boot on both windows and ubuntu. Here are the steps:

I ran chkdsk C: /r and /f a few times but it was still returning errors.
I then ran:
BootRec.exe /FixBoot
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd 

but that din't fix all the problems so at the end I decided to run:
bootrec  /fixmbr and then windows would boot normally but I lost grub so booting ubuntu was not possible. I then used the ubuntu live cd and installed boot-repair who who fixed all the rest of the problems.

---

### Post by oldfred on 2011-09-25
Glad something worked. 

It seems some of the Windows repairs depend on each other and you then have to run the repairs more than once to get everything repaired.

---

