---
title: "Dual booting problem"
date: 2010-07-28
forum: General Help
---

### Post by tmfs on 2010-07-28
Hey,

I installed Ubuntu 10.04 on my HP Pavilion dm4t using a USB stick. Unfortunately, that seems to have somehow corrupted my Windows 7 boot loader - whenever I select Windows from the boot options, it asks me to insert the Windows DVD to recover the installation.

I've two problems - 

1) Is there a way to fix Windows without uninstalling Ubuntu and without removing the option to dual-boot? If there is then how should I go about it?

2) I don't actually have a Windows 7 disk with me (the lappy didn't come with one). I do have a recovery partition though. Will that be sufficient to fix Windows or do I absolutely need a disk?

Thanks

---

### Post by oldfred on 2010-07-29
If you can boot recovery partition you can repair it with that. You can install a simple windows boot loader from Ubuntu and then boot the recovery, then reinstall grub2 from the liveCD. But to see exactly what the problem is:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Restore basic windows boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by tmfs on 2010-07-29
Here's the output from Boot Info Script


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

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
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda4 has 
                       467513343 sectors, but according to the info from 
                       fdisk, it has 506542127 sectors.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             411,646   470,226,943   469,815,298   5 Extended
/dev/sda5             411,648   391,034,879   390,623,232  83 Linux
/dev/sda6         391,036,928   449,628,159    58,591,232  83 Linux
/dev/sda7         449,630,208   470,226,943    20,596,736  82 Linux swap / Solaris
/dev/sda4         470,228,992   976,771,119   506,542,128  42 SFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 1,953,519,615 1,953,517,568   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        36AC6518AC64D441                       ntfs       SYSTEM                        
/dev/sda3: PTTYPE="dos" 
/dev/sda4        C40EE3F70EE3E082                       ntfs       New Volume                    
/dev/sda5        3b4b117e-afe6-44dc-a574-45bbb9c306fc   ext4                                     
/dev/sda6        00f084d1-4499-477a-b23a-c3e96570f7cb   ext4                                     
/dev/sda7        4f7a803d-1f40-4eec-8ea7-ecca1b6ed4e8   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        C86C303C6C302818                       ntfs       Elements                      
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /home                    ext4       (rw)
/dev/sdc1        /media/Elements          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 00f084d1-4499-477a-b23a-c3e96570f7cb
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 00f084d1-4499-477a-b23a-c3e96570f7cb
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 00f084d1-4499-477a-b23a-c3e96570f7cb
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=00f084d1-4499-477a-b23a-c3e96570f7cb ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 00f084d1-4499-477a-b23a-c3e96570f7cb
	echo	'Loading Linux 2.6.32-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=00f084d1-4499-477a-b23a-c3e96570f7cb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 00f084d1-4499-477a-b23a-c3e96570f7cb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 00f084d1-4499-477a-b23a-c3e96570f7cb
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 36ac6518ac64d441
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=00f084d1-4499-477a-b23a-c3e96570f7cb /               ext4    errors=remount-ro 0       1
/dev/sda5       /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=4f7a803d-1f40-4eec-8ea7-ecca1b6ed4e8 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 221.8GB: boot/grub/core.img
 228.2GB: boot/grub/grub.cfg
 221.8GB: boot/initrd.img-2.6.32-24-generic-pae
 221.8GB: boot/vmlinuz-2.6.32-24-generic-pae
 221.8GB: initrd.img
 221.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by oldfred on 2010-07-29
Your partitions are identified as sfs which is some sort of proprietary windows.

I do not see your windows install. Your boot partition is sda2 and you have a sfs/NTFS partition sda4 but you converted sda3 to the extended partition to install Ubuntu. Was sda3 your windows install?

You normally see the windows partition with this directory & executable.

/Windows/System32/winload.exe

Do you have those directories & file somewhere else?

---

### Post by tmfs on 2010-07-29
> **oldfred said:**
> Your partitions are identified as sfs which is some sort of proprietary windows.

I do not see your windows install. Your boot partition is sda2 and you have a sfs/NTFS partition sda4 but you converted sda3 to the extended partition to install Ubuntu. Was sda3 your windows install?

You normally see the windows partition with this directory & executable.

/Windows/System32/winload.exe

Do you have those directories & file somewhere else?

I don't have those directories anywhere. I remember shrinking my Windows 7 partition to create space for linux using the Windows disk utility. 
After that the Ubuntu installer wasn't recognizing the free space as usable so I formatted it as NTFS and then installed Windows there. It is possible I guess that I accidentally overwrote my Windows partition though I doubt it. 
Will I still be able to do a Windows installation through the recovery partition?

---

### Post by oldfred on 2010-07-29
If you moved your install to sda4, It may still be workable but is not now bootable. You could try repairing it and see if windows will add the boot files to it.
It looks like you still have sda2 as a boot and usually that includes a recovery partition  that may do repairs. Often windows only wants to repair a windows partition with the boot flag but that is your sda2 boot partition. 

Your reinstall from the recovery usually is not a repair but a total erase of your drive and reinstall to "like" new. All changes you have done since your bought it will be erased. Check your documentation on what your recovery does.

---

