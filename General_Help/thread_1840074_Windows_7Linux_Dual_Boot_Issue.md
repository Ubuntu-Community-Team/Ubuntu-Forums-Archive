---
title: "Windows 7/Linux Dual Boot Issue"
date: 2011-09-06
forum: General Help
---

### Post by debugman18 on 2011-09-06
Well, I had Windows 7, and figured I'd be adventurous, and install Backtrack alongside it. I use windows for all of my gaming, and backtrack for general goof-offing. Well, GRUB doesn't want to boot into Windows at all. I ran that bootinfo script to get my stuffs to post here.  

 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 5 R1 - Code Name 
                       Revolution 32 bit
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   161,308,664   161,308,602   7 NTFS / exFAT / HPFS
/dev/sda2    *    161,308,665   488,392,064   327,083,400   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1         253,972,478   312,580,095    58,607,618   5 Extended
/dev/sdb5         253,972,480   310,071,295    56,098,816  83 Linux
/dev/sdb6         310,073,344   312,580,095     2,506,752  82 Linux swap / Solaris
/dev/sdb2                  63   253,971,911   253,971,849   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        84882F2F882F1F64                       ntfs       Documents
/dev/sda2        347044377043FE5C                       ntfs       
/dev/sdb2        7AB8BE9CB8BE55FB                       ntfs       Large Documents
/dev/sdb5        8893f8f4-e008-47b0-a1e2-c844ebd96404   ext4       
/dev/sdb6        a2becc34-6cad-4d22-9a33-a4900fbe1488   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sdb5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 8893f8f4-e008-47b0-a1e2-c844ebd96404
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  set gfxpayload=keep
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 8893f8f4-e008-47b0-a1e2-c844ebd96404
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
menuentry 'Ubuntu, with Linux 2.6.39.4' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8893f8f4-e008-47b0-a1e2-c844ebd96404
    linux    /boot/vmlinuz-2.6.39.4 root=UUID=8893f8f4-e008-47b0-a1e2-c844ebd96404 ro   text splash vga=791
    initrd    /boot/initrd.img-2.6.39.4
}
menuentry 'Ubuntu, with Linux 2.6.39.4 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8893f8f4-e008-47b0-a1e2-c844ebd96404
    echo    'Loading Linux 2.6.39.4 ...'
    linux    /boot/vmlinuz-2.6.39.4 root=UUID=8893f8f4-e008-47b0-a1e2-c844ebd96404 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.39.4
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8893f8f4-e008-47b0-a1e2-c844ebd96404
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 8893f8f4-e008-47b0-a1e2-c844ebd96404
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 347044377043FE5C
    drivemap -s (hd0) ${root}
    chainloader +1
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 347044377043FE5C
    drivemap -s (hd0) ${root}
    chainloader +1
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=8893f8f4-e008-47b0-a1e2-c844ebd96404 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=a2becc34-6cad-4d22-9a33-a4900fbe1488 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 139.477790833 = 149.763137536  boot/grub/core.img                             1
 123.687244415 = 132.808167424  boot/grub/grub.cfg                             1
 121.266822815 = 130.209259520  boot/initrdf.img-2.6.39.4                      1
 123.866500854 = 133.000642560  boot/initrd.img-2.6.39.4                       2
 121.282447815 = 130.226036736  boot/initrds.img-2.6.39.4                      1
 139.234420776 = 149.501820928  boot/vmlinuz-2.6.39.4                          1
 123.866500854 = 133.000642560  initrd.img                                     2
 139.234420776 = 149.501820928  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc

Whoever can give me a solution to my problem wins a hug. 
A couple of things to note:
1. I have tried my windows 7 repair disk. It won't detect windows 7.
2. I have my windows 7 files. Like, all of them.
3. Except for my boot files, methinks. Seems that way.

Please help me gang. :)

---

### Post by oldfred on 2011-09-07
You have a windows XP install in sda1 and a Win7 install in sda2.  Windows moves the boot files from the second install into the first one so you can boot either. But your boot.ini from XP refers to rdisk1 which is sdb. Did you switch drives around? Repairs to XP would fix the boot.ini entry or you can manually change it but have to be careful using Ubuntu not to change the line endings. See below.

Do this first and make sure you can boot from sdb directly.
Boot into Backtrack and install grub2's boot loader to sdb before you repair Windows. You can then reset BIOS to boot sdb and boot Backtrack and keep windows all on sda.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

Windows repairs - reset BIOS to boot sda, so windows thinks everything is on sda:

Your boot flag is on sda2, but that is not bootable as is. You need to  move boot flag (active partition in Windows) to sda1. Then your XP  windows repairs should work.

Your two Win7 boot files are missing from sda2 (or were in another partition). Put boot flag back on sda2, the Win7 repairs should replace them or if you have backups you can copy them back. Or you can run the win7 repairs on sda2 and it should restore them to that partition. Normal installs of Win7 have a 100MB boot/recover partition with your two missing files in red below and the main install has the third. But win7 can be in one partition also.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7
[COLOR=Red]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 


oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

I run Win7 chkdsk on my XP partition and it put a win7 boot sector into the XP partition (which is what you have in sda1) it still booted for a while but later I had issues and restored a XP boot sector.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
[COLOR=Red]bootsect.exe /nt52 c:[/COLOR]  *compatible* with operating systems older (XP) than Windows Vista. (you may want this in sda1)
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by debugman18 on 2011-09-07
Awesome, I'm really glad to see a solution. And I'm really not sure why XP is showing up as existent, I used to have it. No longer, though. I'll try it out and let you know the results. Much appreciated.

Worked perfect. Grub boot says its Windows XP, but I'll just edit the menu to say 7. Thanks muchly.

---

### Post by oldfred on 2011-09-07
Glad you are able to boot. If it is saying XP, it must be seeing the XP boot files in sda1. Did you also repair sda2?

Also if you are in Win7 and do not have the separate repairCD.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

