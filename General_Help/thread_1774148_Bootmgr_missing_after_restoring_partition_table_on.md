---
title: "Bootmgr missing after restoring partition table on dual boot"
date: 2011-06-02
forum: General Help
---

### Post by Mowbagz_Badpantz on 2011-06-02
Im running ubuntu 10.10 on a dual boot machine together with vista. When I tried to delete a partition in gparted I accidentaly deleted the general partition table so I had to run testdisk on a live cd to restore it. The problem is that once I had done that and rebooted I get the message bootmgr is missing.
I suppose Testdisk deleted or overwrote mz grubloader.
this is my very first post so plz forgive me if I-m doing it wrong...
kthxb

---

### Post by oldfred on 2011-06-03
Welcome to the forums. 

Bootmgr is missing is a windows error. Is you Vista partition still viewable? Does it have these three boot files at the top level?
/bootmgr /Boot/BCD /Windows/System32/winload.exe
It may just be the windows partition boot sector is not configured correctly after the changes.

Post this to see your entire configuration:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Mowbagz_Badpantz on 2011-06-03
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000   7 NTFS / exFAT / HPFS
/dev/sda2           3,074,048   138,242,039   135,167,992   7 NTFS / exFAT / HPFS
/dev/sda3         138,255,453   157,758,292    19,502,840  83 Linux
/dev/sda4         157,758,300   312,592,769   154,834,470   f W95 Extended (LBA)
/dev/sda5         157,758,363   158,706,114       947,752  82 Linux swap / Solaris
/dev/sda6         158,722,048   235,757,559    77,035,512   7 NTFS / exFAT / HPFS
/dev/sda7         235,770,003   309,331,570    73,561,568  83 Linux
/dev/sda8         309,331,638   312,576,685     3,245,048  82 Linux swap / Solaris

/dev/sda4 ends after the last sector of /dev/sda

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3C208ACE208A8E98                       ntfs       WinRE
/dev/sda2        90C68C85C68C6CF2                       ntfs       Vista
/dev/sda3        3a5469d1-f10d-4939-90d0-112e57ca1efe   ext4       
/dev/sda5        2a838eec-0a7a-4403-b3e2-e18f95166b5a   swap       
/dev/sda6        4A868E91868E7D67                       ntfs       Data
/dev/sda7        5e736a97-9387-469b-b99a-e62833ab6d90   ext3       
/dev/sda8        e61f6068-f6d9-4f09-8511-dc2f090470ac   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/Vista             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /media/5e736a97-9387-469b-b99a-e62833ab6d90 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 3a5469d1-f10d-4939-90d0-112e57ca1efe
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
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 3a5469d1-f10d-4939-90d0-112e57ca1efe
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=3a5469d1-f10d-4939-90d0-112e57ca1efe ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 3a5469d1-f10d-4939-90d0-112e57ca1efe
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=3a5469d1-f10d-4939-90d0-112e57ca1efe ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 90c68c85c68c6cf2
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=3a5469d1-f10d-4939-90d0-112e57ca1efe /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2a838eec-0a7a-4403-b3e2-e18f95166b5a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  75.145723820 = 80.687106560   boot/grub/core.img                             1
  75.145750523 = 80.687135232   boot/grub/grub.cfg                             1
  66.721514225 = 71.641680384   boot/initrd.img-2.6.31-14-generic              1
  68.124273777 = 73.147881984   boot/vmlinuz-2.6.31-14-generic                 2
  66.721514225 = 71.641680384   initrd.img                                     1
  68.124273777 = 73.147881984   vmlinuz                                        2

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 5e736a97-9387-469b-b99a-e62833ab6d90
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 5e736a97-9387-469b-b99a-e62833ab6d90
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5e736a97-9387-469b-b99a-e62833ab6d90
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=5e736a97-9387-469b-b99a-e62833ab6d90 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5e736a97-9387-469b-b99a-e62833ab6d90
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=5e736a97-9387-469b-b99a-e62833ab6d90 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5e736a97-9387-469b-b99a-e62833ab6d90
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5e736a97-9387-469b-b99a-e62833ab6d90 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5e736a97-9387-469b-b99a-e62833ab6d90
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5e736a97-9387-469b-b99a-e62833ab6d90 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5e736a97-9387-469b-b99a-e62833ab6d90
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5e736a97-9387-469b-b99a-e62833ab6d90
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 90c68c85c68c6cf2
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

=============================== sda7/etc/fstab: ================================

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
UUID=5e736a97-9387-469b-b99a-e62833ab6d90 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e61f6068-f6d9-4f09-8511-dc2f090470ac none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 135.813649654 = 145.828795904  boot/grub/core.img                             1
 138.474214077 = 148.685555200  boot/grub/grub.cfg                             2
 135.884995937 = 145.905403392  boot/initrd.img-2.6.35-22-generic              6
 138.681226254 = 148.907832832  boot/initrd.img-2.6.35-28-generic             28
 135.873223782 = 145.892763136  boot/vmlinuz-2.6.35-22-generic                 3
 135.880239010 = 145.900295680  boot/vmlinuz-2.6.35-28-generic                 5
 138.681226254 = 148.907832832  initrd.img                                    28
 135.884995937 = 145.905403392  initrd.img.old                                 6
 135.880239010 = 145.900295680  vmlinuz                                        5
 135.873223782 = 145.892763136  vmlinuz.old                                    3


```

---

### Post by Mowbagz_Badpantz on 2011-06-03
Okay, the winload.exe appears to be there. Im not really sure whats going on though with the rest. My ubuntu partition was supposed to be sda5 not sda7. Maybe I made a mistake with testdisk restoring the partition table. Mz intention was to asign more space to ubutnu bz assimilating the unallocated spaces to sda5 ext.3. I know I should have RTFM instead of trying so this is why Im here anyway

---

### Post by oldfred on 2011-06-03
Windows or testdisk seem to make the extended partition too large. Or it is bigger than the drive sda.

> /dev/sda4 ends after the last sector of /dev/sda

First backup partition table to external device
sudo sfdisk -d /dev/sda > parts.txt

Repair broken partition tables (not overlapping issues)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

I think the above is the easiest but the is a manual way:
sfdisk to fix extended beyond end -partition outside the disk!
[http://ubuntuforums.org/showthread.php?t=1012825](http://ubuntuforums.org/showthread.php?t=1012825)

---

### Post by oldfred on 2011-06-03
then you need to install grub2's bootloader to the MBR of sda.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda7 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda7 if not correct:
sudo fdisk -l
#confirm that linux is sda7
sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Mowbagz_Badpantz on 2011-06-04
Wow! Thank you so much! That did the job! Fixparts resized sda4 extension and the commands restored my grub to sda7 which appears to be my new Linux partition after testdisk has messed them up. Would you recommend to change it back to sda5? I'm kind of scared to perform any other partition operation. Thanks again for your help!

PS: 
I just ran 
```
sudo sfdisk -l
```
and got the following output
```
Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+    191-    192-   1536000    7  HPFS/NTFS
/dev/sda2        191+   8605-   8414-  67583996    7  HPFS/NTFS
/dev/sda3       8606+   9819-   1214-   9751420   83  Linux
/dev/sda4       9820+  19456-   9637-  77409162    f  W95 Ext'd (LBA)
/dev/sda5       9820+   9878-     59-    473876   82  Linux swap / Solaris
/dev/sda6       9879+  14675-   4796-  38517756    7  HPFS/NTFS
/dev/sda7      14676+  19254-   4579-  36780784   83  Linux
/dev/sda8      19255+  19456-    202-   1622524   82  Linux swap / Solaris

Disk /dev/sdb: 1023 cylinders, 123 heads, 62 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/17/17 (instead of 1023/123/62).
For this listing I'll assume that geometry.
Units = cylinders of 147968 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1         27+  27013-  26986-   3899456    c  W95 FAT32 (LBA)
		start: (c,h,s) expected (27,15,7) found (1,0,1)
		end: (c,h,s) expected (1023,16,17) found (967,16,17)
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty

```
I believe this still looks kind of messed up although my bootloader seems to work again.
Can you tell me how to bring order into the chaos?

---

### Post by oldfred on 2011-06-04
Reordering partitions can cause all sorts of issues depending on what is using device (/dev/sda1 etc) and what is using UUID. 

I would not change anything.

You do have two swaps. You older install is using the swap in sda5 and the newer is using the swap in sda8.  You could edit one or the other fstab to use the same one and then delete the unused one.

It seems like you may have used an auto install. Once you get beyond basics it is much better to use manual install as then you have total control over partitions - sizes & locations.

---

### Post by Mowbagz_Badpantz on 2011-06-08
Hello oldfred,
I hope it's ok to post again in this thread but you knowing the background might know where my problem comes from:
After fixing my grub I can't boot into windows now telling me that my winload.exe is missing or corrupted
bootscript shows no error:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for (,msdos7)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000   7 NTFS / exFAT / HPFS
/dev/sda2           3,074,048   157,757,439   154,683,392   7 NTFS / exFAT / HPFS
/dev/sda4         157,758,362   312,576,685   154,818,324   f W95 Extended (LBA)
/dev/sda5         157,758,363   158,706,114       947,752  82 Linux swap / Solaris
/dev/sda6         158,722,048   235,757,559    77,035,512  83 Linux
/dev/sda7         235,770,003   309,331,570    73,561,568  83 Linux
/dev/sda8         309,331,638   312,576,685     3,245,048  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3C208ACE208A8E98                       ntfs       WinRE
/dev/sda2        90C68C85C68C6CF2                       ntfs       Vista
/dev/sda5        2a838eec-0a7a-4403-b3e2-e18f95166b5a   swap       
/dev/sda7        5e736a97-9387-469b-b99a-e62833ab6d90   ext3       
/dev/sda8        e61f6068-f6d9-4f09-8511-dc2f090470ac   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/TOSHIBA           udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 5e736a97-9387-469b-b99a-e62833ab6d90
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 5e736a97-9387-469b-b99a-e62833ab6d90
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5e736a97-9387-469b-b99a-e62833ab6d90
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=5e736a97-9387-469b-b99a-e62833ab6d90 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5e736a97-9387-469b-b99a-e62833ab6d90
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=5e736a97-9387-469b-b99a-e62833ab6d90 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5e736a97-9387-469b-b99a-e62833ab6d90
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5e736a97-9387-469b-b99a-e62833ab6d90 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5e736a97-9387-469b-b99a-e62833ab6d90
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=5e736a97-9387-469b-b99a-e62833ab6d90 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5e736a97-9387-469b-b99a-e62833ab6d90
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5e736a97-9387-469b-b99a-e62833ab6d90
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 90c68c85c68c6cf2
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

=============================== sda7/etc/fstab: ================================

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
UUID=5e736a97-9387-469b-b99a-e62833ab6d90 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e61f6068-f6d9-4f09-8511-dc2f090470ac none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 135.900483608 = 145.922033152  boot/grub/core.img                             1
 138.474214077 = 148.685555200  boot/grub/grub.cfg                             2
 135.884995937 = 145.905403392  boot/initrd.img-2.6.35-22-generic              6
 138.681226254 = 148.907832832  boot/initrd.img-2.6.35-28-generic             28
 135.873223782 = 145.892763136  boot/vmlinuz-2.6.35-22-generic                 3
 135.880239010 = 145.900295680  boot/vmlinuz-2.6.35-28-generic                 5
 138.681226254 = 148.907832832  initrd.img                                    28
 135.884995937 = 145.905403392  initrd.img.old                                 6
 135.880239010 = 145.900295680  vmlinuz                                        5
 135.873223782 = 145.892763136  vmlinuz.old                                    3


```
Do you have any suggestions or should I look for help in windwos forums? I'm only scared of blowing up my linux once more.
thanks for everything already!

---

### Post by oldfred on 2011-06-08
I do not understand error message. Did you have more than one windows?

Also grub is calling sda2 a recovery partition, but it has your 
/Windows/System32/winload.exe.

Boot/Recover partitionss often just have:
/bootmgr /Boot/BCD

Since all your windows files are in the partition and the boot script says it is ok, it may be something internal in the sda2 partition boot sector (PBR). But for windows to repair that PBR, you have to have boot flag on sda2. You can use gparted, Disk Utility or command line:

set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda

Then I might try running the fixBoot command from a windows repair command line.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

If sda2 is not your main windows partition where was it?

---

