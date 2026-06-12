---
title: "Accidentally deleted partitions"
date: 2010-12-25
forum: General Help
---

### Post by nonicknm on 2010-12-25
Hello everyone,
I've a little experience about Ubuntu. I'm using Ubuntu with Windows 7 as dual boot for 1 year. Three days ago I decided to upgrade my Ubuntu version to 10.10. I've created a live version of installer on my USB stick and I've successfully logged in into live version. After some time I clicked install and accidentally I gave a command like install Ubuntu to all hard drive. Installer have given error and denied to continue but it has removed the partitioning records from hard drive. So as you guessed :) everything within hard drive have got unreadable :)

everything until here is the story part. I've written in order to inform the reader.

After a few hours of searching around, I've discovered a miracle called Testdisk. Following the instructions carefully I've managed to return partitions except the System Allocated space of Windows 7 which exists on the starting 100MB of memory. But I'm able to see my files within C: drive of Windows 7

Then my problem has became logging into Windows. Somehow I skip following the instructions on the website of Testdisk and I've used the command called 'Write TestDisk MBR code to first sector' so at that moment my first sector was the C: drive of Windows 7 where OS was originally installed and where my files are kept. So I cannot see the files within C: because the starting bytes set to something else and I want to undo what I've done so far. 
I just want to backup my files within C: somehow. Can you help me?

---

### Post by oldfred on 2010-12-25
First sector is MBR, either grub or windows boot loader is normally in that but I have seen testdisk in one or two bootscript lists.

Windows boot loader (and grub) just jump to code in the windows partition boot sector which is the first sector of the partition (not first on harddrive).

If no files were overwritten you should still be able to boot windows. The new normal install of win 7 is the 100MB boot/recovery partition which has two boot files and the main install that has all the rest of the boot code. Moving boot flag to main install and running windows repairs can then make the main install bootable and in effect obsoleting the 100MB boot partition.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

We can see in boot script if at least most of system looks ok or not. But if you want to read ahead as I will not be back on line till either late today or tomorrow for just a while.
 
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

oldfred's Windows Vista/Win7 repair links:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

---

### Post by nonicknm on 2010-12-25
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   410,364,359   410,157,512   7 HPFS/NTFS
/dev/sda3         410,364,360   478,720,927    68,356,568  83 Linux
/dev/sda4         478,720,935   488,408,129     9,687,195   f W95 Ext d (LBA)
/dev/sda5         478,720,998   488,392,045     9,671,048  82 Linux swap / Solaris

/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2021 MB, 2021654528 bytes
255 heads, 63 sectors/track, 245 cylinders, total 3948544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,948,543     3,948,481   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4E561F4D561F34E5                       ntfs       Sistem Ayr&#305;ld&#305;              
/dev/sda2        0012428812428320                       ntfs                                     
/dev/sda3        d038d5d6-ec49-443d-85ac-8033a3c9fcaf   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        c4647551-848e-4aee-9986-5f4998e5db5c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        447F-B334                              vfat       IRFAN                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/d038d5d6-ec49-443d-85ac-8033a3c9fcaf ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/Sistem Ayr&#305;ld&#305;  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set d038d5d6-ec49-443d-85ac-8033a3c9fcaf
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set d038d5d6-ec49-443d-85ac-8033a3c9fcaf
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
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set d038d5d6-ec49-443d-85ac-8033a3c9fcaf
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=d038d5d6-ec49-443d-85ac-8033a3c9fcaf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set d038d5d6-ec49-443d-85ac-8033a3c9fcaf
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=d038d5d6-ec49-443d-85ac-8033a3c9fcaf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set d038d5d6-ec49-443d-85ac-8033a3c9fcaf
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=d038d5d6-ec49-443d-85ac-8033a3c9fcaf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set d038d5d6-ec49-443d-85ac-8033a3c9fcaf
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=d038d5d6-ec49-443d-85ac-8033a3c9fcaf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set d038d5d6-ec49-443d-85ac-8033a3c9fcaf
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=d038d5d6-ec49-443d-85ac-8033a3c9fcaf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set d038d5d6-ec49-443d-85ac-8033a3c9fcaf
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=d038d5d6-ec49-443d-85ac-8033a3c9fcaf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set d038d5d6-ec49-443d-85ac-8033a3c9fcaf
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=d038d5d6-ec49-443d-85ac-8033a3c9fcaf ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set d038d5d6-ec49-443d-85ac-8033a3c9fcaf
    echo    'Loading Linux 2.6.31-19-generic ...'
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=d038d5d6-ec49-443d-85ac-8033a3c9fcaf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set d038d5d6-ec49-443d-85ac-8033a3c9fcaf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set d038d5d6-ec49-443d-85ac-8033a3c9fcaf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4e561f4d561f34e5
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=d038d5d6-ec49-443d-85ac-8033a3c9fcaf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c4647551-848e-4aee-9986-5f4998e5db5c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 210.4GB: boot/grub/core.img
 215.3GB: boot/grub/grub.cfg
 211.6GB: boot/initrd.img-2.6.31-19-generic
 213.5GB: boot/initrd.img-2.6.32-24-generic
 213.8GB: boot/initrd.img-2.6.32-25-generic
 213.8GB: boot/initrd.img-2.6.32-26-generic
 211.3GB: boot/vmlinuz-2.6.31-19-generic
 212.3GB: boot/vmlinuz-2.6.32-24-generic
 213.4GB: boot/vmlinuz-2.6.32-25-generic
 213.4GB: boot/vmlinuz-2.6.32-26-generic
 213.8GB: initrd.img
 213.8GB: initrd.img.old
 213.4GB: vmlinuz
 213.4GB: vmlinuz.old
=============================== StdErr Messages: ===============================

ls: reading directory sda2/: Input/output error

```This is the output of the bootinfoscript.
Problem is that I guess I've written over some bytes when I've used 'Write TestDisk MBR code to first sector' of TestDisk because my partition table is not including sda1 at that moment. It's possible that TestDisk written over sda2.

```

Error mounting: mount exited with exit code 13: ntfs_mst_post_read_fixup: magic: 0x454c4946  size: 4096  usa_ofs: 48  usa_count: 2: Invalid argument
Actual VCN (0x3003800020001) of index buffer is different from expected VCN (0x3).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```This is the output when I try to mount sda2 with Menu of Ubuntu.

Edit:

```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
   P HPFS - NTFS             12 223 20 25543 254 63  410157512
Directory /

dr-xr-xr-x     0     0         0  4-Feb-2010 16:01 .
dr-xr-xr-x     0     0         0  4-Feb-2010 16:01 ..
-r--r--r--     0     0        49 11-Oct-2009 17:02 autoexec.bat
dr-xr-xr-x     0     0         0 11-Oct-2009 17:02 PerfLogs
dr-xr-xr-x     0     0         0 11-Oct-2009 17:02 Users

```
This is the output when I list the contents of the sda2 with testdisk. There should be like 15 or more directories and some other files.

---

### Post by oldfred on 2010-12-25
If testdisk cannot see all the files & folder in sda2 it is not looking good. I would try running chkdsk from a windows repair cd to see if that can recover anything.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

chkdsk C: /r  # rerun until no errors

---

### Post by nonicknm on 2010-12-28
Sorry for answering late that much.
 
oldfred I see your point. But even if testdisk shows that much data and i have already checked the sizes of the listed files and total size is not much than 5mb. However, when I use photorec to retrieve my files without caring the file system I am able to retrieve files more than 600mb. I'm using 'more than' because I'm using ubuntu live on a usb stick with 2 gb total size so when it get full photorec just give an error like 'not enough space'. I'll try that chkdsk command when I have time. But I have to ask this question, is that command recover or repair only the boot sector which is sda1 in my case or it can do work on sda2 too?
 
Thanks for your replies, they have been quite helpful :)

---

### Post by bludgard on 2010-12-28
I had the same sort of issue.

Boot from Windows install or repair media.

Click through to open a command prompt.

Type:->   Boot.rec.exe /FixMbr

This will repair the MBR on the first available Windows system partition.

If everything pans out as I hope and you want to either remove/repair/reinstall Ubuntu;

Boot from Ubuntu 10.10 LiveMedia.Select Try Ubuntu.Go to System.Administration.GParted Partition Editor.

You will then have full control of your drive with its various file systems.

Hope this helps.


'Preciate the links,oldfred.Learn somethin' every day.

---

### Post by oldfred on 2010-12-28
Yes you should probably run all the windows repairs on sda2 as that is the main install or C:. The sda1 is a hidden boot/recovery that in windows you do not normally see.

---

