---
title: "Help for an unusual problem"
date: 2010-11-08
forum: General Help
---

### Post by DirtyPC on 2010-11-08
Hello all,
          I trust that you can help me with this problem.
I recently acquired a new motherboard/cpu/ram upgrade. Unfortunately, my DVD drive was connected via IDE, whilst my new motherboard only supports SATA. I plan on getting a new blu - ray SATA drive at Christmas. I was running XP and Ubuntu, and thankfully, I could boot into Ubuntu, but, I cannot boot into XP as I have the infinite boot problem. I would like to add the only USB stick I have is a 512mb one. How would I go about getting XP to repair / reinstall? 

Thanks in advance.

Motherboard and CPU, if its any help.

ASUS m4a785td-v Evo
AMD Phenom X4 945 3.0 GHz

Thanks,
       Harry

---

### Post by oldfred on 2010-11-08
Most motherboard still have one or two old ports. Your specs show 2 PATA ports which are the IDE connections.

I had issues with XP not booting with the AHCI setting in BIOS. XP needs special new drivers to work with AHCI. Check BIOS.

Post this to see what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by DirtyPC on 2010-11-08
Hi,
    I took a different root,
i installed Virtual Box with Xp and then downloaded PeToUsb. My only problem is now when i boot from USB i get a text something error? 

D:

---

### Post by DirtyPC on 2010-11-08
> **oldfred said:**
> Most motherboard still have one or two old ports. Your specs show 2 PATA ports which are the IDE connections.

I had issues with XP not booting with the AHCI setting in BIOS. XP needs special new drivers to work with AHCI. Check BIOS.

Post this to see what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.
AHCI? I don't think i can configure that in my BIOS, however I have ACPI and i tried disabling/enabling that, and it doesnt change anything.

---

### Post by DirtyPC on 2010-11-08
> **harrylucas1 said:**
> Hi,
    I took a different root,
i installed Virtual Box with Xp and then downloaded PeToUsb. My only problem is now when i boot from USB i get a text something error? 

D:
this is what i got```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   309,942,044   309,941,982   7 HPFS/NTFS
/dev/sda2         309,942,045   312,576,704     2,634,660   5 Extended
/dev/sda5         309,942,108   312,576,704     2,634,597  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 527 MB, 527302656 bytes
255 heads, 63 sectors/track, 64 cylinders, total 1029888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     1,029,887     1,029,825   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       54bd01ed-2ae2-45a6-a7c6-0ed7744b777b   ext3                                     
/dev/sda1        D218268718266B25                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        c71fbf24-a77c-4c21-ae6b-7870b2cd581b   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4A83-4C75                              vfat       XP USB                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda1        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1        /media/XP USB            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d218268718266b25
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d218268718266b25
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d218268718266b25
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

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0# 1001 is the USB group ID
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0

================= sda1/Wubi: Location of files loaded by Grub: =================


  66.4GB: boot/grub/grub.cfg
  66.4GB: boot/initrd.img-2.6.35-22-generic
  66.4GB: boot/vmlinuz-2.6.35-22-generic
  66.4GB: initrd.img
  66.4GB: vmlinuz

================================ sdb1/boot.ini: ================================

[Boot Loader]
Timeout=10
Default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[Operating Systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="2. GUI Mode Setup Windows XP, Continue Setup + Start XP" /FASTDETECT

C:\SETUPLDR.bs="1. TXT Mode Setup Windows XP, Never unplug USB-Drive Until After Logon"
```

---

### Post by oldfred on 2010-11-08
AHCI is an Intel thing. So with AMD you would not have it. Sorry for the confusion. 

Not sure if there are any other settings for AMD, as I am not familiar with AMD. Others may be able to help.

---

### Post by DirtyPC on 2010-11-08
Thanks anyway
So does anyone else know how to go around this?

D:

---

### Post by oldfred on 2010-11-08
I went back and looked at boot info results. I do not see anything out of the ordinary. If you can boot the wubi install, your windows boot loader is working and it is something else inside windows.

Sometimes it is just run chkdsk, but you need a CD or USB boot to load a windows repair or XP install that you can use for repair.

chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 

Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

You can use a Vista or 7 repair CD to run chkdsk but do not use it for anything else.
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by DirtyPC on 2010-11-08
> **oldfred said:**
> I went back and looked at boot info results. I do not see anything out of the ordinary. If you can boot the wubi install, your windows boot loader is working and it is something else inside windows.

Sometimes it is just run chkdsk, but you need a CD or USB boot to load a windows repair or XP install that you can use for repair.

chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 

Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

You can use a Vista or 7 repair CD to run chkdsk but do not use it for anything else.
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
hi oldfred

i managed to get into safe mode, and from there i did a system restore, that did absoloutely nothing except get rid of my ubuntu install, i dont have  a CD and all i can do is boot from safe mode. Looks like the only way is to a mount an install iso on a virtual drive.

Thanks,
           Harry

---

### Post by oldfred on 2010-11-08
System restore probably rewrote boot.ini. You can manually add the wubi entry back. 

boot.ini entry:
c:\wubildr.mbr="Ubuntu-Linux"

How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)


If using liveCD to edit:
If editing windows files like boot.ini
(Using nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.

---

