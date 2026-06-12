---
title: "Can I boot Win7 without the Windows bootloader?"
date: 2010-12-13
forum: General Help
---

### Post by Zeikcied on 2010-12-13
Okay, so I got a new HP computer last week and I installed Kubuntu.  When I was setting up the hard drive, I noticed that it had three partitions already on it.  One seemed to be a boot partition at the start, another was the Windows Restore partition at the end of the drive, and the space in the middle was taken up by Windows 7.

I deleted the Restore, as I don't plan to make use of Windows 7, and if it breaks then it's not going to matter much.  But I formatted the existing boot partition for use as /boot and Grub.  I totally forgot that Grub needs the Windows boot loader to load Windows.  I remembered this the second time I rebooted my computer and noticed that the Grub menu didn't show up.

So is it at all possible to boot to Windows 7, since I deleted the Windows boot loader and the recovery partition?  Or do I now have a chunk of worthless data on my hard drive?

---

### Post by Rubi1200 on 2010-12-14
Hi,
just to correct you on a couple of things:
> Grub needs the Windows boot loader to load Windows
Not true; GRUB needs to be installed in such a way as to allow it to handle the booting process (MBR, partition, or /boot). It does not *need* the Windows bootloader as it will quite happily probe and add other operating systems to its menu.

> I formatted the existing boot partition for use as /boot and Grub
To be honest, there is no real need for a separate /boot partition. If you had asked here first we could have helped you install GRUB in a way that would have avoided your current situation.

> do I now have a chunk of worthless data on my hard drive? 	
Hopefully not! Unlikely, considering what you have described.

Solution:
boot the computer with a LiveCD, choosing to try Ubuntu not install.

Run the boot info script linked at the bottom of my post.

Get the results back here and we will help you get this sorted out.

By the way, even though you say not to care if Windows gets messed up, I think it was a bit foolhardy to delete the recovery partition without making a backup CD first. You could have done this from within Windows. After all, you never know...

---

### Post by oldfred on 2010-12-14
Reading ahead a little, but we need boot script to confirm it.

You may want to have a windows repair CD handy.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Zeikcied on 2010-12-16
> **Rubi1200 said:**
> Hi,
just to correct you on a couple of things:

Not true; GRUB needs to be installed in such a way as to allow it to handle the booting process (MBR, partition, or /boot). It does not *need* the Windows bootloader as it will quite happily probe and add other operating systems to its menu.


To be honest, there is no real need for a separate /boot partition. If you had asked here first we could have helped you install GRUB in a way that would have avoided your current situation.


Hopefully not! Unlikely, considering what you have described.

Solution:
boot the computer with a LiveCD, choosing to try Ubuntu not install.

Run the boot info script linked at the bottom of my post.

Get the results back here and we will help you get this sorted out.

By the way, even though you say not to care if Windows gets messed up, I think it was a bit foolhardy to delete the recovery partition without making a backup CD first. You could have done this from within Windows. After all, you never know...

I haven't tried the boot info script yet.  When I do, I'll be sure to post the results.

But I thought Grub needed the Windows bootloader.  I thought that when Grub boots to Windows that it just passed things along to the Windows bootloader (I think it's called chain-loading).  At least that's how it used to do it.

I know you don't need to put /boot on its own partition.  This is the first time I've done that.  I just figured I'd do it because the partition was already there.

I removed the recovery partition because I honestly don't need Windows for anything.  I only asked this question because I've never really tried Windows 7 (or even Vista) so I was curious how it looks and feels.  I only really keep Windows on the systems in case I need something for Wine, and even that's becoming less and less important.

---

### Post by oldfred on 2010-12-16
Grub chainloads to the code in the partition boot sector. Windows boot loader in the MBR just jumps to the partition boot sector, so grub just bypasses the MBR portion of windows booting process.

The boot/recovery partition is windows boot partition and has to have just windows code. If you installed grub to it you have damaged it and it will need repair. We need boot script to tell what has been done.

On desktops you should not normally create a separate /boot. It is more difficult to repair and is unnecessary unless you have a very old system with BIOS limits or a server type install with RAID, LVM or are planning to encrypt the entire root partition.

If you want to know more about windows booting and dual booting. It has a lot of info but just reviewing pictures explains a lot.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Zeikcied on 2010-12-17
This does seem like a lot of fuss just to satisfy a curiosity about how Windows 7 actually performs, but here's the results of the Boot Info Script.  I did end up editing the fstab file so my other partitions would auto-mount, thus the little comments I inserted.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800  83 Linux
/dev/sda2             206,848    97,863,097    97,656,250   7 HPFS/NTFS
/dev/sda3          97,863,680   127,160,319    29,296,640  83 Linux
/dev/sda4         127,162,366 1,953,523,711 1,826,361,346   5 Extended
/dev/sda5         127,162,368   517,785,599   390,623,232  83 Linux
/dev/sda6         517,787,648 1,494,347,775   976,560,128  83 Linux
/dev/sda7       1,494,349,824 1,689,659,391   195,309,568  83 Linux
/dev/sda8       1,689,661,440 1,943,758,847   254,097,408  83 Linux
/dev/sda9       1,943,760,896 1,953,523,711     9,762,816  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6a45a801-57d2-4435-ab35-0f7683246103   ext3                                     
/dev/sda2        048C5D278C5D1490                       ntfs       OS                            
/dev/sda3        673f059e-1085-45b2-9015-12f8f2819e37   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        4b297d13-bd29-458e-980e-266d063be162   ext4                                     
/dev/sda6        70a401a4-ffff-4b7d-9c9d-82896d296891   ext4                                     
/dev/sda7        ffed0205-07db-4334-ab33-d64cfc8361d2   ext4                                     
/dev/sda8        dc29ac79-2db9-41bc-80a1-4e548518d6b0   ext4                                     
/dev/sda9        bc02643b-e191-4e46-9a2d-a885ed0905ec   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sda1/grub/grub.cfg: =============================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 673f059e-1085-45b2-9015-12f8f2819e37
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6a45a801-57d2-4435-ab35-0f7683246103
	linux	/vmlinuz-2.6.35-23-generic root=UUID=673f059e-1085-45b2-9015-12f8f2819e37 ro   quiet splash
	initrd	/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6a45a801-57d2-4435-ab35-0f7683246103
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/vmlinuz-2.6.35-23-generic root=UUID=673f059e-1085-45b2-9015-12f8f2819e37 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6a45a801-57d2-4435-ab35-0f7683246103
	linux	/vmlinuz-2.6.35-22-generic root=UUID=673f059e-1085-45b2-9015-12f8f2819e37 ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6a45a801-57d2-4435-ab35-0f7683246103
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=673f059e-1085-45b2-9015-12f8f2819e37 ro single 
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6a45a801-57d2-4435-ab35-0f7683246103
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6a45a801-57d2-4435-ab35-0f7683246103
	linux16	/memtest86+.bin console=ttyS0,115200n8
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

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: initrd.img-2.6.35-23-generic
    .0GB: vmlinuz-2.6.35-22-generic
    .0GB: vmlinuz-2.6.35-23-generic

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext3    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=4b297d13-bd29-458e-980e-266d063be162 /home           ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=bc02643b-e191-4e46-9a2d-a885ed0905ec none            swap    sw              0       0
#formerly sda3
/dev/sda6	/media/sda6	ext4	rw,nosuid,nodev,uhelper=hal	0	2
#formerly hda1
/dev/sda7	/media/sda7	ext4	rw,nosuid,nodev,uhelper=hal	0	2
#formerly sdb3
/dev/sda8	/media/sda8	ext4	rw,nosuid,nodev,uhelper=hal	0	2
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by oldfred on 2010-12-17
Windows boot partition also had these two windows files. But you should be able to repair your windows install in sda2. Windows creates a separate 100MB boot/recovery partition for those who want to encrypt the main partition and for future use with gpt partitions.

 /bootmgr /Boot/BCD

For windows to see the main install as bootable you will have to move the boot flag to sda2 from sda1. You can use gparted or disk utility to move it.

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

After you repair windows, reboot to Ubuntu. If you ran fixMBR you will have to reinstall grub2 first.
Run this and it should find your windows install and let you boot it.

sudo update-grub

---

### Post by Zeikcied on 2011-02-10
I finally got around to using the recovery disc.  (K3B has never worked for me, so after it seemingly ruined two CD-RW discs, I had to use cdrecord from a terminal.)

I did all the steps you listed (including the boot flag), other than the /fixmbr step.  Then I booted to my Kubuntu install and ran the update-grub command.  It didn't find Windows.  So I ran the recovery disc again and ran the /fixmbr step and then fumbled around trying to reinstall Grub with my Kubuntu 10.10 LiveCD.  Grub got reinstalled, and I booted to Kubuntu to run update-grub, and it still doesn't see Windows.

When I first ran the recovery disc, it didn't list the Win7 install on the dialog after selecting the language.  But it still properly detected C:, as the command prompt had the proper partition label.  The second time I ran the recovery disc, it listed the install.  So the first round of steps at least did something.  But Grub still doesn't see Windows when I run the update command.

---

### Post by oldfred on 2011-02-10
If you did the fixMBR, did you boot windows to be sure it worked? It should have then totally repaired windows. Grub will only find correctly configured/working windows to boot.

If repairs have not worked rerun boot script to see what has changed.

---

