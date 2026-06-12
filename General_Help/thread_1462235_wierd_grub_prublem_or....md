---
title: "wierd grub prublem? or...?"
date: 2010-04-25
forum: General Help
---

### Post by salvichronic on 2010-04-25
Hello all,

This is my first post on these forums, I have been running ubuntu karmic since it's release and ive had no problems and if I did I was able to find the solution. I currently have a HP desktop model a6403w dual booting with Vista.

My problem is that at the grub menu when the system boots up with ubuntu it does not seem to load, when I boot into vista it also tries to load but then it freezes, and i am also unable to login into ubuntu recovery. I originally though that the Hard Drive was crapping out until my Dell MINI 10 was having the same issues dual booting with ubuntu/xp. I noticed today if i let the system just sit when starting up either OS it would reboot to grub and if I select the OS agian it would boot in no problems.

Can anyone help me with this issue? or point me in the right direction? also, I have never touched the grub config since i installed ubuntu(except to add an image). Thank you all in advance for the replies.

---

### Post by oldfred on 2010-04-25
Welcome to the forums.

I have seen one or two others with similar issues but not a solution.

Lets see if anything looks wrong.
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

Problems that are intermittent are difficult to resolve and computers are always consistent. I just saw where one user solved his problem by removing a CD as the system was running fsck on it. I had issues once with USB key plugged in, without everything was fine.

---

### Post by salvichronic on 2010-04-25
Thank you very much for the reply oldfred! :)


Here is what results.txt shows..

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda7 starts at sector 224620893.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    80,084,024    80,083,962   7 HPFS/NTFS
/dev/sda2          80,084,025   119,154,104    39,070,080  83 Linux
/dev/sda3         957,247,200   976,767,119    19,519,920   7 HPFS/NTFS
/dev/sda4         119,154,105   957,233,024   838,078,920   5 Extended
/dev/sda5         119,154,168   216,813,239    97,659,072  83 Linux
/dev/sda6         216,813,303   224,620,829     7,807,527  82 Linux swap / Solaris
/dev/sda7         224,620,893   957,233,024   732,612,132   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        064C09094C08F569                       ntfs       HP                            
/dev/sda2        ee59a199-a005-43c1-a4dd-d3786929ec58   ext4                                     
/dev/sda3        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE                 
/dev/sda5        d26c8e10-bdd5-40b3-8db2-1cc63c3d7c0c   ext4                                     
/dev/sda6        32a3a501-e7d2-4c87-8411-7f93ba9d47a4   swap                                     
/dev/sda7        1661-4614                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /home                    ext4       (rw)


=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set ee59a199-a005-43c1-a4dd-d3786929ec58
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,2)
search --no-floppy --fs-uuid --set ee59a199-a005-43c1-a4dd-d3786929ec58
insmod tga
if background_image /boot/grub/Windbuchencom.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set ee59a199-a005-43c1-a4dd-d3786929ec58
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=ee59a199-a005-43c1-a4dd-d3786929ec58 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set ee59a199-a005-43c1-a4dd-d3786929ec58
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=ee59a199-a005-43c1-a4dd-d3786929ec58 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set ee59a199-a005-43c1-a4dd-d3786929ec58
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=ee59a199-a005-43c1-a4dd-d3786929ec58 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set ee59a199-a005-43c1-a4dd-d3786929ec58
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=ee59a199-a005-43c1-a4dd-d3786929ec58 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set ee59a199-a005-43c1-a4dd-d3786929ec58
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=ee59a199-a005-43c1-a4dd-d3786929ec58 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set ee59a199-a005-43c1-a4dd-d3786929ec58
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=ee59a199-a005-43c1-a4dd-d3786929ec58 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set ee59a199-a005-43c1-a4dd-d3786929ec58
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=ee59a199-a005-43c1-a4dd-d3786929ec58 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set ee59a199-a005-43c1-a4dd-d3786929ec58
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=ee59a199-a005-43c1-a4dd-d3786929ec58 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set ee59a199-a005-43c1-a4dd-d3786929ec58
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ee59a199-a005-43c1-a4dd-d3786929ec58 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set ee59a199-a005-43c1-a4dd-d3786929ec58
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ee59a199-a005-43c1-a4dd-d3786929ec58 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 064c09094c08f569
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 949ca48c9ca46a86
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=ee59a199-a005-43c1-a4dd-d3786929ec58 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=d26c8e10-bdd5-40b3-8db2-1cc63c3d7c0c /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=32a3a501-e7d2-4c87-8411-7f93ba9d47a4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  44.0GB: boot/grub/core.img
  44.4GB: boot/grub/grub.cfg
  44.0GB: boot/initrd.img-2.6.31-14-generic
  44.1GB: boot/initrd.img-2.6.31-16-generic
  45.8GB: boot/initrd.img-2.6.31-17-generic
  46.1GB: boot/initrd.img-2.6.31-19-generic
  45.3GB: boot/initrd.img-2.6.31-20-generic
  43.1GB: boot/vmlinuz-2.6.31-14-generic
  41.7GB: boot/vmlinuz-2.6.31-16-generic
  45.0GB: boot/vmlinuz-2.6.31-17-generic
  43.6GB: boot/vmlinuz-2.6.31-19-generic
  45.4GB: boot/vmlinuz-2.6.31-20-generic
  45.3GB: initrd.img
  46.1GB: initrd.img.old
  45.4GB: vmlinuz
  43.6GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo0/sda7: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```

---

### Post by oldfred on 2010-04-25
You have sda1 set at boot but it is missing one major file. And maybe other files in the System32 directory?
 /Windows/System32/winload.exe

It looks like grub found the factory image file and is trying to load it.

Was partition sda2 a windows file system before? Win7 separates the boot files you have in sda1 as a boot partition and puts winload in the main win partition. I am not sure that is part of the normal fixes it runs.

I would try the repairs to see if it will add winload back.
Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

---

### Post by salvichronic on 2010-04-27
The HD was originally split into two partitions the first partition was where the main OS was located and the second is HP recovery disk/drive. I left the second partition alone and I partitioned the first by shrinking it for free space to install ubuntu. 
 
I was able to boot into vista to manually search for winload.exe was in the System32 directory but i unfortunatly forgot to run chkdsk. So, at the moment that recovery drive does not want to boot so I am unable to go into recovery and I have no physical recovery disk. The PC doesn't want to boot into anything anymore :(
 
So it looks like I am at a loss lol, unfortuanly I need windows for two programs, which sucks....

---

### Post by oldfred on 2010-04-27
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by salvichronic on 2010-05-03
Sorry for the late response, so I followed the steps on my laptop and every works great and I havn't had any problems for a couple of days now. As for the Desktop nothing I did seem to work, but i'm assuming that the problems it gave me were symptoms of a potential mobo/cpu failure. Which is what happened and I took apart the tower to verify this. Also, oldfred I would like to thank you for you guidance and patience. :)

---

