---
title: "Upgrade to GRUB2; Can see Windows, but won't boot"
date: 2010-07-06
forum: General Help
---

### Post by ScarletWyvern on 2010-07-06
Today, I upgraded to GRUB2 from legacy GRUB. I run a dual boot of Ubuntu and Vista, and Ubuntu boots perfectly fine from GRUB2.

I've gathered that it's common for a Windows entry to disappear after install GRUB2, but that's not the case for me. My Vista entry is still there.

The problem is that when I try to boot it, it will get to the loading screen before the login screen, and then the computer will restart.

I've searched around the Internet, but all I can find are things related to a Windows installation not appearing in GRUB2... I'd really appreciate any help.

---

### Post by imondanet174 on 2010-07-06
Hello ScarletWyvern,
 
Does Windows Vista actually begin to boot or not ?
 
If not then you can try fixing the Vista installation using the recovery disc 
 
```
 
bootsect /nt60 [Your_Vista_Drive_Letter]

```
 
Followed by reinstalling grub2 
 
```
 
sudo grub-install --root-directory=[Your_Absolute_Ubuntu_Root_Path] /dev/sda

```
 
(Assuming you want to install it on the MBR)
 
Susequently run 
 
```
 
sudo update-grub

```
 
You can view your config file grub.cfg to check if its what you want
 
```
 
sudo gedit /boot/grub/grub.cfg
 
                OR
 
cat /boot/grub/grub.cfg | more

```
 
Ideally grub should detect your Windows Vista Installation.

---

### Post by ScarletWyvern on 2010-07-06
Hi, thanks for the post.

Vista DOES begin to boot.

It boots to the splash screen, but the computer restarts itself before Vista is able to reach the login screen.

I'm almost positive that GRUB2 caused this somehow, since Vista was just working fine last night, and installing GRUB2 is the only real change I've made to my system.

---

### Post by imondanet174 on 2010-07-06
Seems to be a problem with Vista
 
You can run the Automatic System Recovery on the Windows Vista disc and then see what happens.

---

### Post by confused57 on 2010-07-06
You can run the bootinfo script to see if grub2 is installed to the bootsector of your Vista partition:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If that is the case, you can use testdisk to repair:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by ScarletWyvern on 2010-07-06
When I installed GRUB2, I'm fairly sure I installed it to the MBR as everything suggested I do.

I attached the results since they were quite long.

---

### Post by confused57 on 2010-07-06
It looks like grub2 isn't installed to your Vista bootsector, here's the results of your bootinfo script in code tags, if someone else wants to take a look at it:
```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   104,856,254   104,856,192   7 HPFS/NTFS
/dev/sda3         104,856,255   128,246,894    23,390,640   5 Extended
/dev/sda5         104,856,318   125,821,079    20,964,762  83 Linux
/dev/sda6         125,821,143   128,246,894     2,425,752  82 Linux swap / Solaris
/dev/sda4         128,246,895   234,436,544   106,189,650  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3E307AD638979553                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        01bb807a-6064-4484-98b5-fbcb0df938d8   ext4                                     
/dev/sda5        d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5   ext4                                     
/dev/sda6        a31f87a5-340f-4cea-8acb-16fdfff684b5   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,relatime,errors=remount-ro)
/dev/sda4        /home                    ext4       (rw,nosuid,nodev)
/dev/sda1        /media/vista             fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=786

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Chainload into GRUB 2
uuid		d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5
kernel		/boot/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
uuid		d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5 ro quiet splash vga=786
initrd		/boot/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid		d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5 ro single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid		d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5 ro quiet splash vga=786
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5 ro single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid		d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5 ro quiet splash vga=786
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5 ro single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid		d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5 ro quiet splash vga=786
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid		d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5 ro single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.04 LTS, memtest86+
uuid		d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title		Other operating systems:
# root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

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
search --no-floppy --fs-uuid --set d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5
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
search --no-floppy --fs-uuid --set d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3e307ad638979553
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
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=d7ce7ab2-ab64-47d8-b5e2-fe7b981748c5 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a31f87a5-340f-4cea-8acb-16fdfff684b5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# Mount /home partition
/dev/sda4       /home           ext4    nodev,nosuid    0      2
# Windows Vista partition
/dev/sda1       /media/vista      ntfs    rw,suid,dev,exec,auto,user,async        0       0

=================== sda5: Location of files loaded by Grub: ===================


  61.7GB: boot/grub/core.img
  60.9GB: boot/grub/grub.cfg
  55.1GB: boot/grub/menu.lst
  64.3GB: boot/initrd.img-2.6.32-23-generic
  62.5GB: boot/vmlinuz-2.6.32-23-generic
  64.3GB: initrd.img
  62.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb
```

darkod or oldfred should be able to help you.

---

### Post by confused57 on 2010-07-06
> **imondanet174 said:**
> Seems to be a problem with Vista
 
You can run the Automatic System Recovery on the Windows Vista disc and then see what happens.

You might want to try this to see if Vista will boot with it's own mbr IPL, if you don't have a Vista install disk, you can download the Vista rescue disk:
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

Here's how to reinstall grub2 to the mbr, using the ubuntu 10.04 live cd:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Another thing you could do is try a basic Vista 40_custom entry:
```
gksudo gedit /etc/grub.d/40_custom
```
try adding an entry similar to this:
```
menuentry "Chainload Windows Vista" {
    set root=(hd0,1)
    chainloader +1   
}

```
Then run update-grub for the changes to take effect:
```
sudo update-grub
```
This should help determine if there's a problem with your current grub2 Vista entry.

---

### Post by wilee-nilee on 2010-07-06
From the bootscript

complete the upgrade:  **upgrade-from-grub-legacy**

Did you run ```
sudo upgrade-from-grub-legacy
```

In Ubuntu after the grub2 upgrade and reboot. 

Here is a link to the grub2 wiki if you go to Upgrading to GRUB 2 in (grub vs grub2) step #6 you will see this command, and know the mbr is sda.
[https://help.ubuntu.com/community/Grub2#GRUB%20vs%20GRUB%202](https://help.ubuntu.com/community/Grub2#GRUB%20vs%20GRUB%202)

---

### Post by ScarletWyvern on 2010-07-06
I've already done that.

The boot script says that I've got GRUB2 installed in the MBR of sda.

I'm trying the custom menu entry with the chainloader right now.

EDIT: That didn't work. Vista still gets to it's loading screen and conks out just before the login screen.

---

### Post by confused57 on 2010-07-06
You might want to wait until someone more experienced with Vista boot problems sees your thread who can help you.

In the meantime, if you don't have a Vista install disk, you could download the Vista rescue disk provided in the first link I gave you in my previous post, just case you need to repair Vista's boot.

---

### Post by ScarletWyvern on 2010-07-06
Bump?

---

### Post by oldfred on 2010-07-06
I do not see anything wrong in the results.txt. At some point you may want to remove the menu.lst from old grub.

It sounds like windows has issues but I do not know if the standard fixes will work.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

If you replace the MBR you will have to reinstall grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by ScarletWyvern on 2010-07-06
chkdsk and BootRec.exe fixed everything up.

Vista's booting fine now.

Thanks!

---

