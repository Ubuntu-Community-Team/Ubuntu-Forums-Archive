---
title: "Grub issue"
date: 2010-07-30
forum: General Help
---

### Post by Annapolis on 2010-07-30
I am new to Linux and I am having trouble with the grub boot menu. I have a dual boot system, Windows XP 32 bit and Ubuntu 10.04 64 bit. Windows was preexisting when I installed Ubuntu. The install went fine but when I restarted, the Grub menu gives the option of the Windows boot loader but when I tab to that and press enter the screen goes black and the curser just blinks in the upper left corner...no XP boot. The XP drive is there as I can mount it from Ubuntu side but when I try to boot into it it does not seem to be there. What have I done and what can be done so that I can boot into the XP side? Any help would be greatly appreciated.
Annapolis

---

### Post by john newbuntu on 2010-07-30
Hi Annapolis, Welcome to the Ubuntu Forums.
It is possible that you might have overwritten the Windows boot sector with Ubuntu's GRUB2 causing this problem.  To rectify this, you could try one of the following:

1. Follow the instructions in this post from the section "How to restore Windows XP bootloader"
[http://ubuntuforums.org/showpost.php?p=6391959&postcount=1](http://ubuntuforums.org/showpost.php?p=6391959&postcount=1)

2. If the above step does not help, try the solution posted in:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If neither of these help, we may need more information.  Kindly follow the procedure detailed here and post the output of boot info script:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Annapolis on 2010-08-13
OK, first, thanks for the help, I got the XP side back up. I reinstalled Ubuntu to the second drive again and looked for the menu.lst file to see check the chain loader but I have no menu.lst file in the Grub folder. I ran the boot info script and got this;

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #2048 on boot drive #2
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    69,240,831    69,238,784  83 Linux
/dev/sda2          69,242,878    72,302,591     3,059,714   5 Extended
/dev/sda5          69,242,880    72,302,591     3,059,712  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    72,292,499    72,292,437   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        a21dba4f-a821-4137-ab1d-9c5f95b9b8d9   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f432d0da-5ef5-4736-a63e-1c76bb3cac06   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        DE34885134882E99                       ntfs       New Volume                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        E6AC2926AC28F2AB                       ntfs                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set a21dba4f-a821-4137-ab1d-9c5f95b9b8d9
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set a21dba4f-a821-4137-ab1d-9c5f95b9b8d9
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a21dba4f-a821-4137-ab1d-9c5f95b9b8d9
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a21dba4f-a821-4137-ab1d-9c5f95b9b8d9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a21dba4f-a821-4137-ab1d-9c5f95b9b8d9
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a21dba4f-a821-4137-ab1d-9c5f95b9b8d9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a21dba4f-a821-4137-ab1d-9c5f95b9b8d9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a21dba4f-a821-4137-ab1d-9c5f95b9b8d9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set e6ac2926ac28f2ab
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f432d0da-5ef5-4736-a63e-1c76bb3cac06 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/core.img
  32.9GB: boot/grub/grub.cfg
   2.4GB: boot/initrd.img-2.6.32-21-generic
   2.3GB: boot/vmlinuz-2.6.32-21-generic
   2.4GB: initrd.img
   2.3GB: vmlinuz

================================ sdc1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT=OPTIN 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="COD4 10K" /FASTDETECT //NOEXECUTE=OPTIN

I am sure there is something that I am not doing correctly but I do not have the knowledge base to figure out what that might be. The option listed above of COD$ 10K was a 0 raid I had configured that is no longer alive, I just have not edited the boot .ini file. I would appreciate any additional help you could give me.
Annapolis

---

### Post by oldfred on 2010-08-13
OK, I am confused.

You have a neosmart loader in the XP sdc1 partition. You have win7 or vista files in the XP partition - /bootmgr /Boot/BCD so the osprober sees it as win7. Did you have win7 before?

Your boot.ini says it is rdisk 0 or disk 1 but is sdc or disk2?

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro  soft Windows XP Professional" /FASTDETECT=OPTIN 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="COD4 10K" /FASTDETECT //NOEXECUTE=OPTIN

If you want the neosmart loader I have no idea about that. Otherwise you need to repair the windows sdc1 partition to have a windows boot loader in the boot sector. Testdisk may work or you have to use the windows repair disk to run fixboot.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Windows really likes to be the first disk and usually works best. Grub usually adds a map device command to make windows think it is first but your windows boot does not show that.

You said you had raid and that will often confuse grub.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by Annapolis on 2010-08-13
OK, I have done some rearranging. I removed the disk I was not using, now there are just two disks. I also reconnected the two disks to the mother board so that XP is sda and Linux is sdb. That should remove some of the confusion. Now as for the Win 7 boot loader, I had previously installed the Win 7 beta to run along side of the XP OS. The Win 7 OS is gone but the boot loader is still there. I think that may be the biggest problem but I would also think that what ever Windows bootloader I was using it would see and boot into a Windows OS. Never the less I ran the boot info script again as well as the update-grub command. Here they are.

**Grub first;**
 eric@Ubuntu:~$ sudo update-grub  
 Generating grub.cfg ...  
 Found linux image: /boot/vmlinuz-2.6.32-21-generic  
 Found initrd image: /boot/initrd.img-2.6.32-21-generic  
 Found memtest86+ image: /boot/memtest86+.bin  
 Found Windows 7 (loader) on /dev/sda1  
 done  
 eric@Ubuntu:~$
 

 **Boot info script;**
 

  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #2048 on boot drive #2
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 4502736 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    69,240,831    69,238,784  83 Linux
/dev/sdb2          69,242,878    72,302,591     3,059,714   5 Extended
/dev/sdb5          69,242,880    72,302,591     3,059,712  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E6AC2926AC28F2AB                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        a5b50645-152f-42ba-b82a-ac32fa42b690   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        f432d0da-5ef5-4736-a63e-1c76bb3cac06   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

; This boot.ini was automatically generated by NeoSmart Technologies' BootGrabber.exe 
; Use EasyBCD from [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) to manage your bootloader 
 
[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP on C:\" /fastdetect 

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set a5b50645-152f-42ba-b82a-ac32fa42b690
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set a5b50645-152f-42ba-b82a-ac32fa42b690
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a5b50645-152f-42ba-b82a-ac32fa42b690
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a5b50645-152f-42ba-b82a-ac32fa42b690 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a5b50645-152f-42ba-b82a-ac32fa42b690
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a5b50645-152f-42ba-b82a-ac32fa42b690 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a5b50645-152f-42ba-b82a-ac32fa42b690
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a5b50645-152f-42ba-b82a-ac32fa42b690
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e6ac2926ac28f2ab
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=a5b50645-152f-42ba-b82a-ac32fa42b690 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=f432d0da-5ef5-4736-a63e-1c76bb3cac06 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.3GB: boot/grub/core.img
   4.4GB: boot/grub/grub.cfg
   2.3GB: boot/initrd.img-2.6.32-21-generic
   2.2GB: boot/vmlinuz-2.6.32-21-generic
   2.3GB: initrd.img
   2.2GB: vmlinuz

At the moment the only way I can boot into either of the OS's is to change the dish boot order in the BIOS. What have done wrong with the install? I hope I have also cleared up some of the confusion. Thanks!
Annapolis

---

### Post by oldfred on 2010-08-13
These are from win7 and can be deleted (or if you are concerned copied somewhere and then deleted once you confirm there is no issue). Even though grub's osprober calls it win7 I would expect you to boot XP. After you remove the win7 files, the osprober on a grub-update should rename it XP.

I do not see how you are booting Ubuntu. It is now on sdb but the only boot loader is in the Ubuntu partition but is not set up correctly.

I would suggest installing grub2 to the MBR of sdb and changing BIOS to boot sdb. From that you can then boot either windows or Ubuntu. If you ever have an issue with sdb the windows will still boot via BIOS from sda.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

or 

Install MBR from LiveCD, Ubuntu install on sdb1 and want grub2 in drive sdb's MBR:

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sdb

You still have this in the windows boot sector, is this how you want to boot? It may need changing to the windows boot loader with XP's repair - fixboot.

    BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #2048 on boot drive #2 

The script says it is wrong but it may be correct as you do have a grub installed in the Ubuntu boot sector. That is not recommended but will work at least temporarily. They say it is less reliable as it uses block lists and if any boot files are moved you will have to reinstall to fix it.

---

### Post by Annapolis on 2010-08-14
I determined what the problem was...me! Not knowing what I am doing I was trying to place the grub in the wrong place by clicking on the advanced tab during the OS install procedure. I guess I was placing it in the wrong partition. I went back and did a clean install allowing Ubuntu to place the grub in the default location and now all is well. Live and learn and I have much to learn. Thanks for the help!
Annapolis

---

### Post by oldfred on 2010-08-14
Glad you got it working. 

Sometimes reinstall is easier, but you only should have had to reinstall grub. When you have more than one drive grub will normally install to sda, so you do have to use the advance button to install to another drive sdb, sdc etc, but not normally a partition sda1, sda2 etc.

---

