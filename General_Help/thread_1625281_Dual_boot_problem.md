---
title: "Dual boot problem"
date: 2010-11-18
forum: General Help
---

### Post by FlameCow on 2010-11-18
I'm dual booting Ubuntu and Windows XP on my mom's computer. I partitioned it correctly (I believe), and now I can't select to boot from Windows on startup, it automatically goes to Ubuntu. I can't access my Windows partition either. Did I lose all of the information on my Windows partition?

Also, when I try to open the hard drive through "computer", I get this error:
Unable to mount location
Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0x6577656e  size: 4096  usa_ofs: 29811  usa_count: 30239: Invalid argument
Actual VCN (0x90a0d3e7669642f) of index buffer is different from expected VCN (0x1).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by oldfred on 2010-11-19
Welcome to the forum.

Do you have the  XP windows CD You should run chkdsk on the NTFS partition(s). You have to run until there are no errors as it does not always fix everything on each pass.

To see exactly what is installed where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.

---

### Post by Chiller89 on 2010-11-19
To fix this you need to select the windows partition and then add the ubuntu install to the windows bootloader.
 First boot off the XP disk and go into the recovery console.
 Then type "disk part" (I cant remember if its one word or two, try both.)
 It will load disk part.
 Type in "list disk". (Hit enter after each of these commands.)
 Type select and the disk number that contains windows.
 Then type list part.
 Then type select and the partition number that contains windows (should look something like this, "select partition 1")
 Now just type active.
 Now exit and restart your pc.
 It should now boot into Windows.
 To get Ubuntu back, all you need to do is get a program like EasyBCd to  add the Ubuntu entry to the windows bootloader, as clearly the Ubuntu  loader (GRUB) isn't seeing the windows partition.
 Hope this helps :)

---

### Post by garvinrick4 on 2010-11-19
+1 on post #2

---

### Post by FlameCow on 2010-11-19
So do you guys think I lost all of my data on my Windows partition? I'll try to find my XP cd..

---

### Post by Rubi1200 on 2010-11-19
> **FlameCow said:**
> So do you guys think I lost all of my data on my Windows partition? I'll try to find my XP cd..
+2 on post #2

Please post the results of the boot info script mentioned in oldfred's post.

The information will tell us where everything is and whether it can be easily recovered etc.

Without this information, we are in the dark and taking rash action could make the situation worse.

---

### Post by FlameCow on 2010-11-19
> **oldfred said:**
> Welcome to the forum.

Do you have the  XP windows CD You should run chkdsk on the NTFS partition(s). You have to run until there are no errors as it does not always fix everything on each pass.

To see exactly what is installed where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.

Here are the results.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   691,196,624   691,196,562   7 HPFS/NTFS
/dev/sda2         691,196,686   703,281,151    12,084,466   5 Extended
/dev/sda5         691,196,688   695,098,140     3,901,453  82 Linux swap / Solaris
/dev/sda6         695,099,392   702,808,063     7,708,672  83 Linux
/dev/sda7         702,810,112   703,281,151       471,040  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A6D0F45CD0F43461                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2bf49cbe-a46f-4a50-b0e2-ed1b45c1f956   swap                                     
/dev/sda6        fdb317f0-d6df-4a42-95c4-b238f3afaa27   ext4                                     
/dev/sda7        fb863535-115f-4679-8e48-417faac4c89b   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set fdb317f0-d6df-4a42-95c4-b238f3afaa27
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set fdb317f0-d6df-4a42-95c4-b238f3afaa27
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set fdb317f0-d6df-4a42-95c4-b238f3afaa27
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fdb317f0-d6df-4a42-95c4-b238f3afaa27 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set fdb317f0-d6df-4a42-95c4-b238f3afaa27
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=fdb317f0-d6df-4a42-95c4-b238f3afaa27 ro single 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set fdb317f0-d6df-4a42-95c4-b238f3afaa27
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set fdb317f0-d6df-4a42-95c4-b238f3afaa27
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=fdb317f0-d6df-4a42-95c4-b238f3afaa27 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=fb863535-115f-4679-8e48-417faac4c89b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 357.3GB: boot/grub/core.img
 356.6GB: boot/grub/grub.cfg
 359.1GB: boot/initrd.img-2.6.35-22-generic
 358.9GB: boot/vmlinuz-2.6.35-22-generic
 359.1GB: initrd.img
 358.9GB: vmlinuz
=============================== StdErr Messages: ===============================

ls: reading directory sda1/: Input/output error
```


I'm going to bed now. I'll post more in the morning. Thanks for helping, guys!

---

### Post by karthick87 on 2010-11-19
I think you MBR is damaged.To repair it from ubuntu install 

```
sudo apt-get install ms-sys
```This package is used for writing MBR records.Now you should find out the partition where Windows is installed.For that type the following in terminal

```
sudo fdisk -l
``` That will list all the partitions similar to the one below..

   > Device Boot      Start         End      Blocks   Id  System
**/dev/sda1   *           1        3188    25607578+   7  HPFS/NTFS**
/dev/sda2            3189        4462    10233405   83  Linux
/dev/sda3            4463       19458   120449002+   f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda5            4463        9561    40957686    7  HPFS/NTFS
/dev/sda6            9562       14660    40957686    7  HPFS/NTFS
/dev/sda7           14661       19255    36905984   83  Linux
/dev/sda8           19255       19458     1626112   82  Linux swap / Solaris


In this case 
/dev/sda1   *           1        3188    25607578+   7  HPFS/NTFS

is the windows xp installed partition..
The ***/dev/sda1*** is the  partition and  **HPFS/*NTFS*** tells us that's a Windows  formatted partition.  So your Windows partition exists on your drive sda.Now type the following in terminal

```
sudo ms-sys -m /dev/sda
```Now reboot the system,your windows will be back..

---

### Post by oldfred on 2010-11-19
If you are booting Ubuntu MBR is ok. Installing a windows boot loader will probably prevent you from booting.

The script shows you still have your large NTFS partition, but it only shows one of the 3 needed boot files /ntldr. You should have all three like this from mine:

Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

Have you run chkdsk? That may correct something as you seem to have some errors.

Do you have good backups of your windows data? After the chkdsk you should be able to mount the NTFS partition and copy data.

There are several ways to get the boot files back and repair your XP partiton. One is totally from Ubuntu, most use the windows XP CD. You need all 3 files and possibly repair the windows boot sector to get it to boot. This assumes all the other files for windows are intact in the /windows & /windows/system & /windows/system32.


XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
or:

BOOTCFG  /rebuild  #to rebuild boot.ini
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)

---

### Post by karthick87 on 2010-11-19
+1 on Post #9

---

