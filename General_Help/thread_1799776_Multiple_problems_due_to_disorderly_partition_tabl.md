---
title: "Multiple problems due to disorderly partition table"
date: 2011-07-08
forum: General Help
---

### Post by najdorfchess on 2011-07-08
Hi all. I'm using a Dell Inspiron 15R laptop with 4 GB RAM. I dual boot ubuntu 11.04 64-bit with Windows 7 64-bit OS. The mistake I did is deleting the 15GB dell recovery disk since I thought its a waste of disk space, which could be employed usefully. Due to that [COLOR="Red"]grub2 wasn't detecting windows partition[/COLOR] no matter what I do. Here is the info of my partition table:

```
najdorf@mynatty:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x01df2c72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400   de  Dell Utility
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        1926       10066    65386520    7  HPFS/NTFS
/dev/sda3              13       60802   488281145    f  W95 Ext'd (LBA)
/dev/sda5              14        1925    15358140    7  HPFS/NTFS
/dev/sda6           10066       52969   344617984    7  HPFS/NTFS
/dev/sda7           55580       55704      999424   82  Linux swap / Solaris
/dev/sda8           55705       60802    40942592   83  Linux

[COLOR="Red"]Partition table entries are not in disk order[/COLOR]

```


As you can see from above the boot is in sda2 which is my windows 7 partition (C drive). sda5 is the dell recovery partition which I deleted out of greed. And sda6 is another ntfs partition for keeping my data(movies, games etc..)

My mbr is also as per windows 7 boot and the partition table is written according to windows compatible mode. Due to this [COLOR="Red"]Gparted doesnt detect my partition table[/COLOR] at all. See the screenshot of it below


[[img]http://www.freeimagehosting.net/uploads/09f6bff241.png[/img]](http://www.freeimagehosting.net/)



Another effect is that im [COLOR="Red"]unable to log into ubuntu when my windows os is hibernated[/COLOR]. Also the boot menu never displays the kernel version of ubuntu. Today the current stable release is 2.6.39.2 but my system hasn't been updated to it yet. Infact my [COLOR="Red"]update manager doesn't even show it as an update[/COLOR]. My current kernel version is displayed below. 

```
najdorf@mynatty:~$ uname -r
2.6.38-8-generic
```


Someone kindly tell me if I can fix this entire problem. I really don't want to clean my disk and reinstall the Operating systems. 
Feel free to ask me any question/ additional info. Thanks in advance!  :)

---

### Post by jocko on 2011-07-08
> **najdorfchess said:**
> Today the current stable release is 2.6.39.2 but my system hasn't been updated to it yet. Infact my update manager doesn't even show it as an update. My current kernel version is displayed below. 

```
najdorf@mynatty:~$ uname -r
2.6.38-8-generic
```Someone kindly tell me if I can fix this entire problem. I really don't want to clean my disk and reinstall the Operating systems. 
Feel free to ask me any question/ additional info. Thanks in advance!  :)
Can't help you with the real problem, but:

The current stable release from kernel.org is 2.6.39.2 as you say, but the kernel in natty is still and will *always* be 2.6.38.
Ubuntu *has never* and *will never* introduce a new version of the kernel to the standard repos of an already released Ubuntu version.
All the kernel updates you get from the update manager are just patches to the same kernel version, never new versions.
If you want a newer kernel, either install it from some unsupported source (ppa or compile it yourself) or wait for the next ubuntu version (Oneiric ocelot, which will have a 3.0.x series kernel).

---

### Post by najdorfchess on 2011-07-08
> **jocko said:**
> Can't help you with the real problem, but:

The current stable release from kernel.org is 2.6.39.2 as you say, but the kernel in natty is still and will *always* be 2.6.38.
Ubuntu *has never* and *will never* introduce a new version of the kernel to the standard repos of an already released Ubuntu version.
All the kernel updates you get from the update manager are just patches to the same kernel version, never new versions.
If you want a newer kernel, either install it from some unsupported source (ppa or compile it yourself) or wait for the next ubuntu version (Oneiric ocelot, which will have a 3.0.x series kernel).

Oh this is interesting and new to me. Does ubuntu not update its kernel in its previous versions. I have used ubuntu 8.x and 9.x and i remember updating the kernel on so many occasions and having a huge list of options on my boot menu. Are u sure about this? Or is it a new policy introduced recently for natty?

---

### Post by Quackers on 2011-07-08
Gparted doesn't recognise your partition table because something is wrong with it.
sda1 is a Dell Utility partition.
Although you say that sda2 is your Windows 7 partition it appears to be only 4GB in size. That's not much for Win 7.
The space taken by sda3 (your extended partition) includes the sda2 partition's start/end cylinders. This can not be correct. sda2 is a primary partition and cannot be inside an extended partition.

We'd better find out what is where.
Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example
```
 cd Downloads/boot_info_script060
```

if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by srs5694 on 2011-07-08
> **najdorfchess said:**
> Hi all. I'm using a Dell Inspiron 15R laptop with 4 GB RAM. I dual boot ubuntu 11.04 64-bit with Windows 7 64-bit OS. The mistake I did is deleting the 15GB dell recovery disk since I thought its a waste of disk space, which could be employed usefully. Due to that [COLOR=Red]grub2 wasn't detecting windows partition[/COLOR] no matter what I do. Here is the info of my partition table:

Deleting the recovery partition could not cause the problems you describe, unless you deleted the wrong partition. (It could be your software didn't do what you thought it did, though; see below....) Quackers has correctly identified at least one of your problems, but see more below....

> ```
najdorf@mynatty:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x01df2c72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400   de  Dell Utility
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        1926       10066    65386520    7  HPFS/NTFS
/dev/sda3              13       60802   488281145    f  W95 Ext'd (LBA)
/dev/sda5              14        1925    15358140    7  HPFS/NTFS
/dev/sda6           10066       52969   344617984    7  HPFS/NTFS
/dev/sda7           55580       55704      999424   82  Linux swap / Solaris
/dev/sda8           55705       60802    40942592   83  Linux

[COLOR=Red]Partition table entries are not in disk order[/COLOR]

```

You've highlighted the "partition table entries are not in disk order" message. Don't worry about this; it's perfectly legal, although it can be confusing. Quackers said that your /dev/sda2 is 4GB in size, but I get about 62 GiB for /dev/sda2. Obviously one of us has made an arithmetic error. I've double-checked mine, but with these big numbers, it's easy to miss a mistake....

> As you can see from above the boot is in sda2 which is my windows 7 partition (C drive). sda5 is the dell recovery partition which I deleted out of greed. And sda6 is another ntfs partition for keeping my data(movies, games etc..)

If the partition appears in the partition table you did not delete it. Perhaps you deleted it from your boot loader configuration, but that doesn't delete it from the disk and it doesn't save any disk space. Given the nature of the problem, I suspect whatever unnamed utility you used for this task didn't delete the partition, but instead reassigned it from being a primary partition to being a logical partition.

FWIW, it *is* safe to delete these ~15 or ~20 GB recovery partitions; *however*, doing so means that you'll be unable to restore or repair Windows without a Windows installation or recovery disc for the same version of Windows you've got. There's normally a tool in Windows you can use to burn recovery discs that will enable you to restore the computer to a pristine state. I recommend you use this tool prior to deleting the partition. You can also download (supposedly MS-approved) standard installation discs from [here,](http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/) or use a retail disc if you've bought one for another computer. Whatever you decide to do, though, it's something you should deal with later.

As Quackers says, your partition table is illegal because /dev/sda2 (a primary partition) resides within your extended partition. Extended partitions contain logical partitions; primary partitions may not reside within them. Unfortunately, GParted flakes out when it sees this type of configuration and shows the entire disk as being blank. My hunch is that the tool you used to "delete" /dev/sda5 converted it from primary to logical and expanded the extended partition to cover this partition, in the process creating the overlap with /dev/sda2, as well.

Obtaining the Boot Info Script output, as Quackers suggests, will clarify some details of your boot configuration and will show the partition table more precisely; however, the partition table problem is already clear. There are a number of possible ways to fix it, but the simplest is to use my [FixParts](http://www.rodsbooks.com/fixparts/) program to convert /dev/sda5 from logical back to primary, as it presumably began. Be sure to back up your partition table, as described on the FixParts Web page, before you do this, and be sure that all six your current primary and logical partitions appear as either "primary" or "logical" in the display -- none should be listed as "omitted" or missing (except for the extended partition, which FixParts does not show). If FixParts shows something strange, don't try random things with it; post back showing its output to get more advice.

> My mbr is also as per windows 7 boot and the partition table is written according to windows compatible mode. Due to this [COLOR=Red]Gparted doesnt detect my partition table[/COLOR] at all. See the screenshot of it below

As above, the cause of GParted showing a blank disk is your illegal partition table. This has nothing to do with a "windows compatible mode."

---

### Post by najdorfchess on 2011-07-08
@Quackers

I have pasted the result after running the boot info script. 

It's a long file. So have put it in code mode.


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2    *     30,926,848   161,699,887   130,773,040   7 NTFS / exFAT / HPFS
/dev/sda3             208,782   976,771,071   976,562,290   f W95 Extended (LBA)
/dev/sda5             208,845    30,925,124    30,716,280   7 NTFS / exFAT / HPFS
/dev/sda6         161,703,936   850,939,903   689,235,968   7 NTFS / exFAT / HPFS
/dev/sda7         892,884,992   894,883,839     1,998,848  82 Linux swap / Solaris
/dev/sda8         894,885,888   976,771,071    81,885,184  83 Linux

/dev/sda2 overlaps with /dev/sda3

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3030-3030                              vfat       DELLUTILITY
/dev/sda2        AC7C4EC27C4E86D4                       ntfs       OS
/dev/sda5        01CC287586523180                       ntfs       
/dev/sda6        94285D60285D4282                       ntfs       
/dev/sda7        e72f5392-aeaa-4d4c-b05c-71524c681e22   swap       
/dev/sda8        604031f4-600a-49a1-a1c2-25a709fcada2   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /media/sda2              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/sda5              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/sda6              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=0)


=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=========================== sda8/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 604031f4-600a-49a1-a1c2-25a709fcada2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root 604031f4-600a-49a1-a1c2-25a709fcada2
set locale_dir=($root)/boot/grub/locale
set lang=en_IN
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 604031f4-600a-49a1-a1c2-25a709fcada2
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=604031f4-600a-49a1-a1c2-25a709fcada2 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 604031f4-600a-49a1-a1c2-25a709fcada2
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=604031f4-600a-49a1-a1c2-25a709fcada2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 604031f4-600a-49a1-a1c2-25a709fcada2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root 604031f4-600a-49a1-a1c2-25a709fcada2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid           0  0  
# / was on /dev/sda7 during installation
UUID=604031f4-600a-49a1-a1c2-25a709fcada2  /            ext4  errors=remount-ro             0  1  
# swap was on /dev/sda6 during installation
UUID=e72f5392-aeaa-4d4c-b05c-71524c681e22  none         swap  sw                            0  0  
/dev/sda2                                  /media/sda2  ntfs  nls=iso8859-1,umask=000,user  0  0  
/dev/sda5                                  /media/sda5  ntfs  nls=iso8859-1,umask=000,user  0  0  
/dev/sda6                                  /media/sda6  ntfs  nls=iso8859-1,umask=000,user  0  0  
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 434.853477478 = 466.920366080  boot/grub/core.img                             1
 429.056716919 = 460.696141824  boot/grub/grub.cfg                             1
 428.578907013 = 460.183097344  boot/initrd.img-2.6.38-8-generic               2
 434.955833435 = 467.030269952  boot/vmlinuz-2.6.38-8-generic                  1
 428.578907013 = 460.183097344  initrd.img                                     2
 434.955833435 = 467.030269952  vmlinuz                                        1

```


I rechecked it and sda2 is the C drive, which is the windows system partition. It is about 62.5 GB in total size. 
Thank you.

---

### Post by najdorfchess on 2011-07-08
@src5694

Thank you so much for the informative reply. I just ran the script and have posted above. I think what u say is right. I did try changing the 15GB recovery partition into logical partition using EASEUS partition master software in windows 7 which i think put in my windows primary partition (C drive) within the new logical partition, (since I guess their starting sectors have to be in ascending order. I'm not sure if this is the reason). Moreover since the sda2 partition is extended grub isn't able to find it everytime i try to restore it (using 100 different methods!! Seriously! ;-)

Kindly go through the result file and I will try to use Fixparts to rearrange my partition table. Let me know if I'm missing anything here, and suggestions & comments. Thanks!

---

### Post by srs5694 on 2011-07-08
The Boot Info Script results add detail and precision, but don't change my recommendations as presented in my earlier post: Use FixParts to convert /dev/sda5 from a logical partition to a primary partition.

The order of partitions in terms of the sectors they use does *not* have to match the order in which they appear in the partition table, so that's not an error or a cause for concern. Such disordered partitions can be confusing, but they are *not* an error.

I do note that your MBR contains the Windows boot loader. That's fine *if* you've got GRUB installed in a primary Linux partition that's marked as active (which is not the case for you) or if the Windows BCD boot loader is chainloading to GRUB (which may be the case -- you've got GRUB's core.img file copied onto your Windows partition, so it could be it's being referenced in this way). No matter what, I recommend you fix the partition table error and then deal with any boot problems, if you find you're having problems booting at that point.

---

### Post by jocko on 2011-07-08
> **najdorfchess said:**
> Oh this is interesting and new to me. Does ubuntu not update its kernel in its previous versions. I have used ubuntu 8.x and 9.x and i remember updating the kernel on so many occasions and having a huge list of options on my boot menu. Are u sure about this? Or is it a new policy introduced recently for natty?
This has always been ubuntu's policy. After the final release of an ubuntu version, the packages in the repos are never updated from newer upstream source code (with one or a few exceptions). Updates that you get from the repos are just patches to the same version of the source code as the original release of the ubuntu version had.
Natty had a 2.6.38 kernel when it was released, and even if you get some updated kernels now and then, they will still be 2.6.38 kernels. Same with (almost) all other packages.

The only exception to this rule that I know of is firefox, which was updated from a beta version in 8.04, and now canonical have loosened the policy a little bit to allow even updates to new major versions of firefox (natty had firefox 4 when it was released, but has been updated to firefox 5.0 later).

---

### Post by oldfred on 2011-07-08
The grub install in windows will prevent it from booting. Windows is not case sensitive so a /boot & /Boot are exactly the same and in windows you cannot have two identical folders in the same folder. Delete /boot that has grub files, but be careful not to delete Boot that has the BCD as that is an essential part of windows.

>     Boot files:        /bootmgr /[COLOR=Red]Boot[/COLOR]/BCD /Windows/System32/winload.exe 
                       [COLOR=Red]/boot[/COLOR]/grub/core.img[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

### Post by najdorfchess on 2011-07-09
Thank you everyone for ur kind responses. I installed fixparts 0.7.1 and ran it through to convert sda5 partition into a primary partition. But I was unable to do so since fixparts didn't list it under *CAN BE PRIMARY* column. When I tried it, operation failed and it aborted. So I quit out without any changes. What can I do now? See below 

```
root@mynatty:/home/najdorf# fixparts /dev/sda
FixParts 0.7.1

Loading MBR data from /dev/sda

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 976773168 sectors (465.8 GiB)
MBR disk identifier: 0x01DF2C72
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1                  2048       206847   primary     Y        Y      0xDE
   2      *       30926848    161699887   logical     Y               0x07
   5                208845     30925124   logical     Y               0x07
   6             161703936    850939903   primary     Y        Y      0x07
   7             892884992    894883839   omitted                     0x82
   8             894885888    976771071   primary              Y      0x83

MBR command (? for help): r
Partition to set as primary: 5
Specified change is not legal! Aborting change!

```

---

### Post by najdorfchess on 2011-07-09
> **jocko said:**
> This has always been ubuntu's policy. After the final release of an ubuntu version, the packages in the repos are never updated from newer upstream source code (with one or a few exceptions). Updates that you get from the repos are just patches to the same version of the source code as the original release of the ubuntu version had.
Natty had a 2.6.38 kernel when it was released, and even if you get some updated kernels now and then, they will still be 2.6.38 kernels. Same with (almost) all other packages. 

Oh I didn't know this at all. But I vaguely remember updating kernel versions in one of the earlier distros of ubuntu. But like you say, the policy might have been the same from earlier on. And regarding firefox, yes I'm very happy to see liberation of policy and firefox 5 hit ubuntu repos as soon it was on mozilla's site  :)
Anyways, thanks a lot for ur info!

---

### Post by najdorfchess on 2011-07-09
> **srs5694 said:**
> The Boot Info Script results add detail and precision, but don't change my recommendations as presented in my earlier post: Use FixParts to convert /dev/sda5 from a logical partition to a primary partition.


I have converted sda5 from a logical partition into a primary partition using EASEUS partition master in Windows 7. I was unable to do this using Fixparts as I had described in my previous post. Now [COLOR="Red"]I'm able to see my partition table in GParted[/COLOR]. Screenshot of that is shown below

[[img]http://www.freeimagehosting.net/uploads/7b15f45f68.png[/img]](http://www.freeimagehosting.net/)


As you can see from the table, the Dell recovery partition which I converted from logical to primary has been renamed as sda2. Earlier it was sda5. Subsequently other partition's names have also been changed. These include:

sda3 = C drive for windows 7 (which is my boot partition)
sda4 = Which contains all the other partitions within, including the linux partitions. Incidentally this partition is now an extended parition (and I dunno why).
sda5 = My D drive in win7 (has most of my data)
sda6 = linux swap
sda7 = ext4 partition of ubuntu 11.04

There are small unallocated spaces between the main partitions and the extended partition, and also right at the end of the table. Any reason why this is there? 

Also I ran the bootinfo script again whose result file I have pasted below inside CODE tag. 


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2             208,845    30,925,124    30,716,280   7 NTFS / exFAT / HPFS
/dev/sda3    *     30,926,848   161,699,887   130,773,040   7 NTFS / exFAT / HPFS
/dev/sda4         161,703,934   976,771,071   815,067,138   f W95 Extended (LBA)
/dev/sda5         161,703,936   892,880,895   731,176,960   7 NTFS / exFAT / HPFS
/dev/sda6         892,884,992   894,883,839     1,998,848  82 Linux swap / Solaris
/dev/sda7         894,885,888   976,771,071    81,885,184  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3030-3030                              vfat       DELLUTILITY
/dev/sda2        01CC287586523180                       ntfs       
/dev/sda3        AC7C4EC27C4E86D4                       ntfs       OS
/dev/sda5        94285D60285D4282                       ntfs       
/dev/sda6        e72f5392-aeaa-4d4c-b05c-71524c681e22   swap       
/dev/sda7        604031f4-600a-49a1-a1c2-25a709fcada2   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/sda1              vfat       (rw)
/dev/sda2        /media/sda2              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/sda3              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/sda5              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 604031f4-600a-49a1-a1c2-25a709fcada2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 604031f4-600a-49a1-a1c2-25a709fcada2
set locale_dir=($root)/boot/grub/locale
set lang=en_IN
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 604031f4-600a-49a1-a1c2-25a709fcada2
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=604031f4-600a-49a1-a1c2-25a709fcada2 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 604031f4-600a-49a1-a1c2-25a709fcada2
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=604031f4-600a-49a1-a1c2-25a709fcada2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 604031f4-600a-49a1-a1c2-25a709fcada2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos7)'
	search --no-floppy --fs-uuid --set=root 604031f4-600a-49a1-a1c2-25a709fcada2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
proc                                       /proc        proc  nodev,noexec,nosuid                 0  0  
# / was on /dev/sda7 during installation
UUID=604031f4-600a-49a1-a1c2-25a709fcada2  /            ext4  errors=remount-ro                   0  1  
# swap was on /dev/sda6 during installation
UUID=e72f5392-aeaa-4d4c-b05c-71524c681e22  none         swap  sw                                  0  0  
/dev/sda2                                  /media/sda2  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sda5                                  /media/sda5  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sda6                                  /media/sda6  ntfs  nls=iso8859-1,umask=000,user        0  0  
/dev/sda1                                  /media/sda1  vfat  defaults                            0  0  
/dev/sda3                                  /media/sda3  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 434.853477478 = 466.920366080  boot/grub/core.img                             1
 430.310668945 = 462.042562560  boot/grub/grub.cfg                             1
 428.578907013 = 460.183097344  boot/initrd.img-2.6.38-8-generic               2
 434.955833435 = 467.030269952  boot/vmlinuz-2.6.38-8-generic                  1
 428.578907013 = 460.183097344  initrd.img                                     2
 434.955833435 = 467.030269952  vmlinuz                                        1

```


However I do [COLOR="Red"]get an error[/COLOR] while booting up the system that it's [COLOR="Red"]unable to mount sda6 partition[/COLOR] which happens to be my swap partition (atleast with the new partition numbers assigned). 

I initially thought the error is due to mismatch with PySDM software Storage manager that I use to automount the drives. But this error is shown even after I uninstalled the software. Also when I noted in the system monitor there is absolutely no usage of the swap space which might have got to do with the system unable to detect the partition. Help me out here. Thanks in advance!

---

### Post by Quackers on 2011-07-09
What is booting? Anything?

You have /boot/grub/core.img in sda3 with your Windows boot files. That shouldn't be there. As it may interfere with Windows booting you should remove that boot folder but BE CAREFUL that you don't remove Windows' boot file (which includes BCD). Only remove the boot folder that includes grub and inside that folder will be core.img

At the moment the only bootloader installed to the mbr of the drive is the Windows bootloader.
To get Ubuntu to boot you need to have grub installed to the mbr of the drive.
You can delete the above file from the Ubuntu live cd desktop (via the Places menu) and you can also install grub to the mbr of the drive from that environment too, with the following commands. Please copy/paste them into the terminal, one line at a time, pressing enter after each line.
```
sudo mount /dev/sda7 /mnt  
sudo grub-install --root-directory=/mnt /dev/sda
```
This should report "Finished.No errors".
If it does please reboot and Ubuntu should boot directly.
If so, open a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is run to see if the Windows Loader is picked up.
If so, reboot and you should see a grub menu giving you the choice of which OS to boot. Try both in turn.

---

### Post by najdorfchess on 2011-07-09
I already did this and I'm able to boot into both Windows 7 and Ubuntu normally. But the only problem seems to be with mounting sda6 partition during system boot. I get the following message 

[COLOR=Blue][I]An error occurred while mounting /media/sda6
Press S to skip mounting or M for manual recovery
[/I][/COLOR]

It is the swap partition and when I observe in the system monitor there seems to be no usage of swap. But the system detects 976MB of swap space though. So I don't know. Should I delete the /media/sda6 directory? Or is the problem due to the partition being shown as omitted by fixparts? Any suggestions how I could fix this? Thank you guys in advance :)

---

### Post by oldfred on 2011-07-09
It is not swap it is having trouble mounting but the renumbered NTFS partitions from your fstab:

> /dev/sda2                                  /media/sda2  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
/dev/sda5                                  /media/sda5  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
[COLOR=Red]/dev/sda6[/COLOR]                                  /media/sda6  ntfs  nls=iso8859-1,umask=000,user        0  0  
/dev/sda1                                  /media/sda1  vfat  defaults                            0  0  
/dev/sda3                                  /media/sda3  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
Not sure if any other the others match or not as I did not check them.

---

### Post by Quackers on 2011-07-09
> **najdorfchess said:**
> I already did this and I'm able to boot into both Windows 7 and Ubuntu normally. But the only problem seems to be with mounting sda6 partition during system boot.

Then you must have posted an old results.txt file, as Windows is still in the mbr of the drive according to your last one.
As long as things are booting that's good :-)

With regard to oldfred's last comments you can comment out the line in /etc/fstab by typing a  #  at the start of the particular line. Then you can see if the error message disappears when booting.

---

### Post by srs5694 on 2011-07-09
My comments (mostly just to reiterate what others have said):


[list]
[*]FixParts could have done the conversion, but it set up some initial default changes that would have to have been undone. Specifically, you would have to have used "l" to change 6, 7, and 8 into logicals; then used "r" to change 2 and 5 into primaries. The "Can Be Logical" and "Can Be Primary" columns refer to the changes you can make *at that moment*; they change as you change primary/logical assignments. Clearly the algorithms FixParts uses to determine the defaults aren't optimized for the specific problem you had. Of course, this is all moot since you managed to do the job with another tool. I mention it only in case somebody reads this in the future and could benefit from the information.
[*]My suspicion is that the Windows BCD boot loader is being used to chainload GRUB. If so, removing core.img from the Windows partition could render Linux unbootable. If both Windows and Linux are booting correctly, I'd leave that detail alone and I would *not* re-install GRUB to the MBR. "If it ain't broke, don't fix it."
[*]As oldfred says, you need to update your /etc/fstab file to reflect the new partition identities. The most robust way to do this is to replace the "/dev/sda6" and similar entries with UUID values, which you can obtain by typing "sudo blkid". If you swap in one device filename to replace another, you could have to change them again in the future.
[*]Don't worry about those small unallocated spaces between partitions. They're puny, so the risks to your filesystems if you should attempt to resize them to recover the space are far greater than any benefit you could gain from the extra space. They probably exist because of small resizing operations done in all the juggling in at least two disk utilities.
[/list]

---

### Post by najdorfchess on 2011-07-09
> **Quackers said:**
> 
With regard to oldfred's last comments you can comment out the line in /etc/fstab by typing a  #  at the start of the particular line. Then you can see if the error message disappears when booting.

Yes I forget such a thing exists. Thanks a lot  :) 
Edited fstab and took out that line. It worked. Thanks a lot guys. 

Strangely enough, I have a new peculiar problem. My clock on Windows 7 gets reset to GMT time every time I startup. This weird problem occurs when I had booted ubuntu the last time and booting into windows. If had I booted windows 7 previously and restart back into windows, the clock remains correct. Sounds very awkward but this is the problem. 

Anyways the error in my partition table is resolved and boot problem is solved. Thank you guys once again  :)

Can I mark this thread as Solved?

---

### Post by najdorfchess on 2011-07-09
> **srs5694 said:**
> My comments (mostly just to reiterate what others have said):


[list]
[*]My suspicion is that the Windows BCD boot loader is being used to chainload GRUB. If so, removing core.img from the Windows partition could render Linux unbootable. If both Windows and Linux are booting correctly, I'd leave that detail alone and I would *not* re-install GRUB to the MBR. "If it ain't broke, don't fix it."
[*]As oldfred says, you need to update your /etc/fstab file to reflect the new partition identities. The most robust way to do this is to replace the "/dev/sda6" and similar entries with UUID values, which you can obtain by typing "sudo blkid". If you swap in one device filename to replace another, you could have to change them again in the future.
[*]Don't worry about those small unallocated spaces between partitions. They're puny, so the risks to your filesystems if you should attempt to resize them to recover the space are far greater than any benefit you could gain from the extra space. They probably exist because of small resizing operations done in all the juggling in at least two disk utilities.
[/list]


Thanks for summarizing. Yes I did use partition master in windows 7 to solve my problem as I had initially used the same tool earlier. So even though Fixparts was unable to convert it back into primary, I was able to get the job done. But it's a very useful tool to have anyway. BTW, can u kindly gimme places where I can learn more about these stuffs? I mean like which file to look for when u have a particular problem, like he pointed out at /etc/fstab immediately after reading about my problem. I know it's a very generic question but any posts in ubuntuforum that could help me go into little more depth of filesystem, various config files, and how config files work in ubuntu OS in general. It would be great if u can provide me with links. Thanks :)

---

### Post by oldfred on 2011-07-09
It depends a lot on what your interests are. I used google to find solutions to the things I broke in Ubuntu and took a while to realize most of the good answers were from posts here. Then one day lurking in new posts I saw something I knew the answer to and replied.

Of course 6 months later I found I wanted to remember exactly how to solve something, looked in google and found the answer except it was not quite right. Some poster name oldfred left out one step. Oops. Now I keep notes and keep updating them so they get better over time, I  hope.

---

### Post by Quackers on 2011-07-09
And the rest is history :-)

Happy to see that you got things working najdorfchess! :-)

---

### Post by srs5694 on 2011-07-09
> **najdorfchess said:**
> Strangely enough, I have a new peculiar problem. My clock on Windows 7 gets reset to GMT time every time I startup. This weird problem occurs when I had booted ubuntu the last time and booting into windows. If had I booted windows 7 previously and restart back into windows, the clock remains correct. Sounds very awkward but this is the problem. 

My own preferred solution to this problem is to tell Windows that the hardware clock is in GMT. This can be done as described [here,](http://weblogs.asp.net/dfindley/archive/2006/06/20/Set-hardware-clock-to-UTC-on-Windows-_2800_or-how-to-make-the-clock-work-on-a-Mac-Book-Pro_2900_.aspx) among other places. I like this solution rather than telling Linux to use local time because with the hardware clock in GMT there's less likely to be problems because two OSes try to change the clock when daylight saving time changes roll around.

As to what files to look at or other resources for finding solutions to problems, I'm afraid that's a very broad question. There are lots of configuration files in /etc, but some problems require dealing with other files; and even in /etc, there are lots of files that affect various different subsystems. To begin getting a handle on it, I recommend reading an introductory Linux book or reading some introductory Linux administration Web sites. If you don't do this and just solve problems as they occur you'll gradually build up the knowledge of what's important, though.

---

### Post by najdorfchess on 2011-07-09
> **oldfred said:**
> It depends a lot on what your interests are. I used google to find solutions to the things I broke in Ubuntu and took a while to realize most of the good answers were from posts here. Then one day lurking in new posts I saw something I knew the answer to and replied.

Of course 6 months later I found I wanted to remember exactly how to solve something, looked in google and found the answer except it was not quite right. Some poster name oldfred left out one step. Oops. Now I keep notes and keep updating them so they get better over time, I  hope.

Haha good one.. But you guys are amazing. This is one single forum with so much to learn about the best operating system in the world :) I mean for someone starting his Master's in Computer Science this is gold. I'll put my effort to learn and help others as well! Hats off! (Respect) :cool:

My interest is in knowing how the OS works. I mean knowing how the filesystem is like, how linux is built as an OS (the fundu of its architecture), what are the major configuration files (atleast all the critical ones) to look for while troubleshooting a problem. I can work with the OS, use help online and solve certain issues here and there, my level is certainly more than a beginner. But by no means I can say I'm an expert.  All I would need is articles or posts in forums like these to help me get started on this. I think this way of learning is better than reading a book. But if you guys can suggest a book, then it's great as well. 

P.S. Most of my learning on linux is by usage and through CBT Nugget on Red Hat. I dunno if you guys have heard of it, but I think it's famous.

---

### Post by najdorfchess on 2011-07-09
> **Quackers said:**
> And the rest is history :-)

Happy to see that you got things working najdorfchess! :-)

Thanks a lot :)

---

### Post by najdorfchess on 2011-07-10
> **srs5694 said:**
> My own preferred solution to this problem is to tell Windows that the hardware clock is in GMT. This can be done as described [here,](http://weblogs.asp.net/dfindley/archive/2006/06/20/Set-hardware-clock-to-UTC-on-Windows-_2800_or-how-to-make-the-clock-work-on-a-Mac-Book-Pro_2900_.aspx) among other places. I like this solution rather than telling Linux to use local time because with the hardware clock in GMT there's less likely to be problems because two OSes try to change the clock when daylight saving time changes roll around.

As to what files to look at or other resources for finding solutions to problems, I'm afraid that's a very broad question. There are lots of configuration files in /etc, but some problems require dealing with other files; and even in /etc, there are lots of files that affect various different subsystems. To begin getting a handle on it, I recommend reading an introductory Linux book or reading some introductory Linux administration Web sites. If you don't do this and just solve problems as they occur you'll gradually build up the knowledge of what's important, though.

Yes this did help. I run the reg script in windows and the time got reset to +5:30 to what my current time is. The same thing happened in Ubuntu as well, but when I reset the clock in linux, it got resetted in windows 7 as well. The clock time is fine on subsequent reboots in both the OSes. Thank you for this. 

And regarding the learning part, do u recommend any specific book/ material, which you think is quite solid?

---

### Post by najdorfchess on 2011-07-10
And if someone can help me with the eclipse default compiler problem. See link [http://ubuntuforums.org/showthread.php?t=1799253](http://ubuntuforums.org/showthread.php?t=1799253)
Thanks

---

### Post by kanishkdudeja on 2011-07-10
> **najdorfchess said:**
> And if someone can help me with the eclipse default compiler problem. See link [http://ubuntuforums.org/showthread.php?t=1799253](http://ubuntuforums.org/showthread.php?t=1799253)
Thanks

Ive replied to it..Check it.

---

### Post by oldfred on 2011-07-10
I am still a book person and when starting with Ubuntu bought Ubuntu Unleashed 6.06. I am still using it and have many notes in the margins and pages stuck into locations to provide for some of the major changes. 

History:
[http://www.netneurotic.de/mac/unix/images/UNIX.png](http://www.netneurotic.de/mac/unix/images/UNIX.png)
[http://en.wikipedia.org/wiki/File%3AUnix_history-simple.svg](http://en.wikipedia.org/wiki/File%3AUnix_history-simple.svg)

Ubuntu Documentation:
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[https://help.ubuntu.com/11.04/index.html](https://help.ubuntu.com/11.04/index.html)

Explaination of file structure
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)

Checking on bugs gives a lot of insight to the inner workings of the system.
bug reports info on how to do:
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)
Check bugs
[https://bugs.launchpad.net/ubuntu/+source/grub2](https://bugs.launchpad.net/ubuntu/+source/grub2)

System configuration files are in /etc and user configuration files are in /home in hidden files & folders with the . prefix.

---

### Post by srs5694 on 2011-07-10
> **najdorfchess said:**
> And regarding the learning part, do u recommend any specific book/ material, which you think is quite solid?

At the risk of tooting my own horn, there's my *Linux+ Complete Study Guide* (ISBN 978-0-470-88845-2), which is more-or-less the same book as my *LPIC-1 Study Guide* (ISBN 978-0-470-40483-6), both from Sybex. These are textbooks for people studying for the Linux+ or LPIC-1 certifications, but of course the information they contain is relevant for anybody wanting to learn Linux. These titles are heavy on command line methods of administration, though. If you want something with more of a GUI emphasis, something else would work better, but I have no specific recommendations on that score.

One thing you might try is going to a book store with a good selection of Linux books and peruse the Linux titles. See if you can find answers some questions, such as how to create an /etc/fstab entry or how to fix X if it doesn't start up, in each of the books. Pick whichever book seems to present the answers you can best understand.

---

### Post by najdorfchess on 2011-07-10
> **oldfred said:**
> I am still a book person and when starting with Ubuntu bought Ubuntu Unleashed 6.06. I am still using it and have many notes in the margins and pages stuck into locations to provide for some of the major changes. 

History:
[http://www.netneurotic.de/mac/unix/images/UNIX.png](http://www.netneurotic.de/mac/unix/images/UNIX.png)
[http://en.wikipedia.org/wiki/File%3AUnix_history-simple.svg](http://en.wikipedia.org/wiki/File%3AUnix_history-simple.svg)

Ubuntu Documentation:
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[https://help.ubuntu.com/11.04/index.html](https://help.ubuntu.com/11.04/index.html)

Explaination of file structure
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)

Checking on bugs gives a lot of insight to the inner workings of the system.
bug reports info on how to do:
[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)
Check bugs
[https://bugs.launchpad.net/ubuntu/+source/grub2](https://bugs.launchpad.net/ubuntu/+source/grub2)

System configuration files are in /etc and user configuration files are in /home in hidden files & folders with the . prefix.

This is very nice. I'm bookmarking this page straightaway! Thanks a lot

---

### Post by najdorfchess on 2011-07-10
> **srs5694 said:**
> At the risk of tooting my own horn, there's my *Linux+ Complete Study Guide* (ISBN 978-0-470-88845-2), which is more-or-less the same book as my *LPIC-1 Study Guide* (ISBN 978-0-470-40483-6), both from Sybex. These are textbooks for people studying for the Linux+ or LPIC-1 certifications, but of course the information they contain is relevant for anybody wanting to learn Linux. These titles are heavy on command line methods of administration, though. If you want something with more of a GUI emphasis, something else would work better, but I have no specific recommendations on that score. 

That's a nice suggestion. It would be appropriate to read these books, since I wanna know deep about the OS. And I love command line inputs. No way I would need a GUI for every aspect in my system ;) Thank you  :)

---

### Post by najdorfchess on 2011-07-12
I have an error while mounting my hard disk partitions. I get the following error (see screenshot). It shows the error while I try to mount one of the partitions.

I think I need the root access to mount my partitions. But im able to mount pen drives and external hard disks. I have copy pasted my /etc/fstab file below under code tag. Tell me what should I change to be able to mount my hard disk partitions.

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid                           0  0  
# / was on /dev/sda7 during installation
UUID=604031f4-600a-49a1-a1c2-25a709fcada2  /            ext4  errors=remount-ro                             0  1  
# swap was on /dev/sda6 during installation
UUID=e72f5392-aeaa-4d4c-b05c-71524c681e22  none         swap  sw                                            0  0  
/dev/sda2                                  /media/sda2  ntfs  nls=iso8859-1,ro,users,noauto,umask=000,user  0  0  
/dev/sda5                                  /media/sda5  ntfs  nls=iso8859-1,ro,users,noauto,umask=000,user  0  0  
#/dev/sda6                                 /media/sda6  ntfs  nls=iso8859-1,umask=000,user                  0  0  
/dev/sda1                                  /media/sda1  vfat  noauto,user                                   0  0  
/dev/sda3                                  /media/sda3  ntfs  nls=iso8859-1,users,noauto,umask=000,user     0  0  

```

---

### Post by oldfred on 2011-07-12
Looks like it cannot mount sda5 either. Comment it out. You may need to run chkdsk on all the NTFS & FAT partitions. Run it until there are no errors.

---

### Post by najdorfchess on 2011-07-15
This doesnt seem to work and I don't get any error in my disks. I think the problem has gotta do with privileges and I'm not able to mount the NTFS drives as the user. However I'm able to mount them as the root user. So what I did is to run the mount of these partitions during boot, so that they are auto mounted. I'm able to edit files and run applications, in those drives. The only small problem being that I cant unmount them unless im root, which isn't a big deal anyway.

---

### Post by najdorfchess on 2011-07-23
Hi all. This thread has been marked SOLVED and my primary problem has been solved. I would like to know if it is possible to expand the size of ext4 ubuntu partition (sda7). I would like to do that by shrinking sda5 and extending the sda7 volume with the resulting free space. Any suggestions?

---

### Post by oldfred on 2011-07-23
You cannot easily do that unless they are adjacent on the drive. You have swap inbetween.

You could delete swap and recreate that at the end of the extended partition and move sda7 left. That will give it a new UUID and you will have to edit fstab to get swap working again.

I do not like move partitions around a lot. I will expand to the right to increase size but moving left requires all the data to be copied & verified. If a large partition it can take very long and any interruption/powerfailure etc can cause total loss.

Another possibility is creating a new partition for /home and moving all your /home into that new partition. I tend to prefer smaller system partitions for both windows & Linux and having data separate.

Several essentially identical ways to move /home.
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

