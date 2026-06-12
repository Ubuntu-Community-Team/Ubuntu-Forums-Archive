---
title: "2 Linux swap partitions and a few Dell Utility partitions"
date: 2011-09-18
forum: General Help
---

### Post by CheshireKat on 2011-09-18
I wasn't sure where to put this; I basically need help organizing my partitions and such for my Ubuntu installations. I hope someone can help me or refer me to something to read?

Okay, about a month ago I had installed a distro of Ubuntu 10.4 (UberStudent) on my Dell Inspiron 1100 30GB 526MB RAM laptop in a partition next to Windows XP, leaving about 20GB for Windows. Then I decided to wipe out Windows entirely and created a new partition over it. Then I installed an Ubuntu 10.4-based OS called Bodhi Linux on the new partition. Now I would like to install Xubuntu over the UberStudent partition, but when I got through the installer and saw all my partitions, I noticed I had way more partitions than I setup. I have two Linux Swap partitions; I'm not sure if that's normal since I have two Linux OS'? There's a FAT16 partition (/sda1) which I'm guessing is my Live USB that I'm running Xubuntu off of, even though the size is incorrect as far as I know. /sda2 (ext3) is 5.6GB. 256MB is used; I've no idea what's on that partition and I can't access it. I didn't even know it existed until now. Then there's /sda4 (ext2) of 6GB; 105MB is used. Again, I don't know what's on it. /sda7 is 11.2GB and 6342MB is used; I believe this is my Bodhi partition (with that much used up, it should be; I installed several programs and stuff). /sda8 is a swap partition of 544.2MB and 0MB is used. /sda5 (ext4) is 6.3GB with 2490MB used. This probably is my UberStudent partition. And finally, I have /sda6 as another swap of 337MB with 0MB used.

So basically what I want to know is, do I need both swap partitions? [s]And how can I figure out what the extra partitions are being used for? It'd be nice if I could combine those extra partitions that somehow were created to enlarge my OS's partition space. I don't know how they got there or what's on them.[/s]
Actually, just as I was writing that I remembered that in Bodhi Linux there are...I think 3 "Dell Utility" drives listed under "Places." So now I'm wondering if Dell created those extra partitions and if so, what for and can I delete them?

I'm sorry if this is unclear :???: I'll try to clarify more if needed.


EDIT: hmm...I think this could've gone in the Dell Support forum...?

---

### Post by coffeecat on 2011-09-18
HI, I'll be logging off in a minute, but I thought I'd start the ball rolling by asking for some more information so that others can help you while it's night here where I am. If not, I'll look in on this thread in the morning.

First thing - about your edit. Don't worry about the forum. It's fine here. The Dell forum was originally intended for those with Dell systems with pre-installed Ubuntu. I know a lot of Dell owners who've installed their own systems use that forum, but yours doesn't sound like a specific Dell problem.

Next - yes, you can have only one swap partition shared between two or more Linux installations. We can sort that out when we see your exact layout.

Yes, it is a bit unclear! :) The easiest way to get all the information we need about your system is for you to run the boot script here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot script as described there and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. Then we'll be able to see exactly what's what and whether you really do have three separate Dell Utility partitions. I doubt it, but let's see.

---

### Post by foureyesboy on 2011-09-18
> **CheshireKat said:**
> 

So basically what I want to know is, do I need both swap partitions? 

As for the above question, no, you don't need two swap partitions (you only boot into one distro at a time) though it's no harm at all (just taking up your disk space).  But you need to get in one of the distro and manually change the setting [s]int[/s] in /etc/fstab to point the swap partition to the same swap as with the other distro.

---

### Post by CheshireKat on 2011-09-18
Alright. I have that script on my flashdrive already from another issue I had, so I'll get in Bodhi and run that. 
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file /sda_mbr.bak looks at 
                       sector 1 of the same hard drive for core.img, but 
                       core.img can not be found at this location.
    Operating System:  Windows 95
    Boot files:        /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......Sf.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 845056 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262   6 FAT16
/dev/sda2    *         80,325    11,032,575    10,952,251  83 Linux
/dev/sda3          22,747,134    58,603,519    35,856,386   5 Extended
/dev/sda5    *     45,709,312    57,942,015    12,232,704  83 Linux
/dev/sda6          57,944,064    58,603,519       659,456  82 Linux swap / Solaris
/dev/sda7          22,747,136    44,640,255    21,893,120  83 Linux
/dev/sda8          44,642,304    45,705,215     1,062,912  82 Linux swap / Solaris
/dev/sda4          11,032,576    22,746,661    11,714,086  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.2 GB, 16231956480 bytes
255 heads, 63 sectors/track, 1973 cylinders, total 31703040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    31,696,244    31,696,182   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D3-041D                              vfat       DellUtility
/dev/sda2        91402ca0-c7bc-4396-adf8-937cdbd384e9   ext3       
/dev/sda4        d3fc596c-3de7-47f6-83e4-c28cd06f54e7   ext2       
/dev/sda5        86183267-42ed-446d-88aa-a09e634e8b58   ext4       
/dev/sda6        aa5d44de-5c19-4499-b3e8-94afd6c04326   swap       
/dev/sda7        d48904b0-0247-4771-8fa2-6dc11478098b   ext4       
/dev/sda8        59b8d020-0259-4a4d-9da3-80d72b561b2a   swap       
/dev/sdb1        E8AD-290C                              vfat       FLASH

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/sda1              vfat       (rw)
/dev/sda2        /media/sda2              ext3       (rw)
/dev/sda4        /media/sda4              ext2       (rw)
/dev/sda5        /media/sda5              ext4       (rw)
/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/FLASH         vfat       (rw,nosuid,nodev,uhelper=hal,uid=1000)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             initrd.gz                                      1

=========================== sda5/boot/grub/grub.cfg: ===========================


```

---

### Post by coffeecat on 2011-09-19
I'll post what I can, but most of the RESULTS.txt output is missing. I think something went wrong with your copy and paste! If you look at the end of what you posted, it's trying to tell us about the grub.cfg file on sda5, but got terminated. :wink: There should be grub.cfg and /etc/fstab files for both sda5 and sda7, plus a few other things.

Anyway, the output agrees with what you posted before - more-or-less - but I'll post what I've got from the script in a more readable form. The GB and MB sizes I've given are base 10 ones, not base 2 - which would be GiB and MiB. 

sda1 - your Dell Utility partition. Only 41MB. You only have one! There is some grub code in this partition which shouldn't be there. I've not seen that exact message before, so I can't quite work out what it's telling us.

sda2 - ext3 - 5.6GB. We can come back to how to access it later.

sda3 - your extended partition containing sda5 through to sda8.

sda5 - ext4 - 6.3GB - Contains an OS "Ubuntu 10.04.1 LTS".

sda6 - swap - 338MB - We can't tell which installation this belongs to without the /etc/fstab files.

sda7 - ext4 - 11,2GB - Contains an OS "Ubuntu 10.04.3 LTS".

sda8 - swap - 544MB - See comment for sda6.

sda4 - primary partition, ext2 - 6GB - See comment for sda2.

I can't tell which of sda5 or sda7 is Bodhi, but I'm sure you're right that it's sda7. We should be able to be certain if you post the missing bits of RESULTS.txt. If Bodhi is sda7, what is sda5? It's not clear from your OP.

First comment I'd make is that I wouldn't necessarily bother deleting one of the swap partitions and arranging things so that both OSs use the one - they are both quite small. Nevertheless, you're quite tight for space on 30GB and it doesn't help that you have two partitions totalling  nearly 12GB that you don't know how to access. Accessing them is straightforward - you just need to deal with permissions. I can tell you how to do that, but in the meantime post back with the missing script output and give us an idea of what you are trying to achieve. Perhaps a fundamental re-organisation of your hard drive would be best.

---

### Post by CheshireKat on 2011-09-19
Okay, ran again and copied whole thing:
```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file /sda_mbr.bak looks at 
                       sector 1 of the same hard drive for core.img, but 
                       core.img can not be found at this location.
    Operating System:  Windows 95
    Boot files:        /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......Sf.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 845056 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262   6 FAT16
/dev/sda2    *         80,325    11,032,575    10,952,251  83 Linux
/dev/sda3          22,747,134    58,603,519    35,856,386   5 Extended
/dev/sda5    *     45,709,312    57,942,015    12,232,704  83 Linux
/dev/sda6          57,944,064    58,603,519       659,456  82 Linux swap / Solaris
/dev/sda7          22,747,136    44,640,255    21,893,120  83 Linux
/dev/sda8          44,642,304    45,705,215     1,062,912  82 Linux swap / Solaris
/dev/sda4          11,032,576    22,746,661    11,714,086  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.2 GB, 16231956480 bytes
255 heads, 63 sectors/track, 1973 cylinders, total 31703040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    31,696,244    31,696,182   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D3-041D                              vfat       DellUtility
/dev/sda2        91402ca0-c7bc-4396-adf8-937cdbd384e9   ext3       
/dev/sda4        d3fc596c-3de7-47f6-83e4-c28cd06f54e7   ext2       
/dev/sda5        86183267-42ed-446d-88aa-a09e634e8b58   ext4       
/dev/sda6        aa5d44de-5c19-4499-b3e8-94afd6c04326   swap       
/dev/sda7        d48904b0-0247-4771-8fa2-6dc11478098b   ext4       
/dev/sda8        59b8d020-0259-4a4d-9da3-80d72b561b2a   swap       
/dev/sdb1        E8AD-290C                              vfat       FLASH

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/sda1              vfat       (rw)
/dev/sda2        /media/sda2              ext3       (rw)
/dev/sda4        /media/sda4              ext2       (rw)
/dev/sda5        /media/sda5              ext4       (rw)
/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/FLASH         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /media/Plop Boot Manager 5.0.13 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             initrd.gz                                      1

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 86183267-42ed-446d-88aa-a09e634e8b58
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
search --no-floppy --fs-uuid --set 86183267-42ed-446d-88aa-a09e634e8b58
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 86183267-42ed-446d-88aa-a09e634e8b58
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=86183267-42ed-446d-88aa-a09e634e8b58 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 86183267-42ed-446d-88aa-a09e634e8b58
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=86183267-42ed-446d-88aa-a09e634e8b58 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 86183267-42ed-446d-88aa-a09e634e8b58
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 86183267-42ed-446d-88aa-a09e634e8b58
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

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
UUID=86183267-42ed-446d-88aa-a09e634e8b58 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=aa5d44de-5c19-4499-b3e8-94afd6c04326 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  21.947502136 = 23.565950976   boot/grub/core.img                             1
  21.976802826 = 23.597412352   boot/grub/grub.cfg                             1
  23.305809021 = 25.024421888   boot/initrd.img-2.6.32-24-generic              2
  23.064407349 = 24.765218816   boot/vmlinuz-2.6.32-24-generic                 1
  23.305809021 = 25.024421888   initrd.img                                     2
  23.064407349 = 24.765218816   vmlinuz                                        1

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set d48904b0-0247-4771-8fa2-6dc11478098b
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set d48904b0-0247-4771-8fa2-6dc11478098b
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
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set d48904b0-0247-4771-8fa2-6dc11478098b
insmod png
if background_image /usr/share/backgrounds/grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Bodhi Linux, with Linux 2.6.39-2-generic' --class bodhi --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set d48904b0-0247-4771-8fa2-6dc11478098b
	linux	/boot/vmlinuz-2.6.39-2-generic root=UUID=d48904b0-0247-4771-8fa2-6dc11478098b ro   splash quiet
	initrd	/boot/initrd.img-2.6.39-2-generic
}
menuentry 'Bodhi Linux, with Linux 2.6.39-2-generic (recovery mode)' --class bodhi --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set d48904b0-0247-4771-8fa2-6dc11478098b
	echo	'Loading Linux 2.6.39-2-generic ...'
	linux	/boot/vmlinuz-2.6.39-2-generic root=UUID=d48904b0-0247-4771-8fa2-6dc11478098b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.39-2-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set d48904b0-0247-4771-8fa2-6dc11478098b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set d48904b0-0247-4771-8fa2-6dc11478098b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 86183267-42ed-446d-88aa-a09e634e8b58
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=86183267-42ed-446d-88aa-a09e634e8b58 ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 86183267-42ed-446d-88aa-a09e634e8b58
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=86183267-42ed-446d-88aa-a09e634e8b58 ro single
	initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
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
# / was on /dev/sda7 during installation
UUID=d48904b0-0247-4771-8fa2-6dc11478098b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=59b8d020-0259-4a4d-9da3-80d72b561b2a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  13.027305603 = 13.987962880   boot/grub/core.img                             1
  17.588802338 = 18.885832704   boot/grub/grub.cfg                             2
  14.136802673 = 15.179276288   boot/initrd.img-2.6.39-2-generic               2
  11.389648438 = 12.229541888   boot/vmlinuz-2.6.39-2-generic                  2
  14.136802673 = 15.179276288   initrd.img                                     2
  11.389648438 = 12.229541888   vmlinuz                                        2

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 46 90 44 65 6c 6c 20  34 2e 31 00 02 04 01 00  |.F.Dell 4.1.....|
00000010  02 00 02 00 00 f8 4f 00  3f 00 ff 00 3f 00 00 00  |......O.?...?...|
00000020  86 39 01 00 80 00 29 1d  04 d3 07 44 65 6c 6c 55  |.9....)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 00 00  |tilityFAT16   ..|
00000040  00 00 00 00 00 00 00 00  fa b8 00 00 8e d0 bc fc  |................|
00000050  7b fb fc 8e d8 ff 0e 13  04 8b 0e 13 04 c1 e1 06  |{...............|
00000060  8e c1 b9 00 01 33 f6 33  ff f3 66 a5 c7 06 72 04  |.....3.3..f...r.|
00000070  45 44 8e c0 bd 00 7c e8  21 01 0f 82 bb 00 66 0f  |ED....|.!.....f.|
00000080  b7 86 16 00 66 d1 e0 66  0f b7 9e 0e 00 66 03 c3  |....f..f.....f..|
00000090  66 03 86 1c 00 66 89 86  3e 00 8b 86 11 00 c1 e8  |f....f..>.......|
000000a0  04 89 86 46 00 bb 00 05  e8 aa 00 0f 82 8a 00 ba  |...F............|
000000b0  10 00 b9 0b 00 be ec 7d  8b fb f3 a6 74 16 83 c3  |.......}....t...|
000000c0  20 4a 75 ee 66 ff 86 3e  00 ff 8e 46 00 75 d6 be  | Ju.f..>...F.u..|
000000d0  d9 7d eb 6d 66 0f b7 86  11 00 66 ba 20 00 00 00  |.}.mf.....f. ...|
000000e0  66 f7 e2 66 0f b7 8e 0b  00 66 03 c1 66 48 66 f7  |f..f.....f..fHf.|
000000f0  f1 66 01 86 3e 00 66 8b  86 3e 00 66 89 46 fc 66  |.f..>.f..>.f.F.f|
00000100  0f b7 47 1a 8b f8 2d 02  00 66 0f b6 9e 0d 00 66  |..G...-..f.....f|
00000110  f7 e3 66 01 86 3e 00 bb  00 07 c7 86 46 00 04 00  |..f..>......F...|
00000120  e8 32 00 72 14 81 c3 00  02 66 ff 86 3e 00 ff 8e  |.2.r.....f..>...|
00000130  46 00 75 ec ea 00 02 70  00 be cc 7d eb 03 be d9  |F.u....p...}....|
00000140  7d e8 02 00 eb fe ac 3c  00 74 09 b4 0e bb 07 00  |}......<.t......|
00000150  cd 10 eb f2 c3 66 8b 86  3e 00 66 33 d2 66 0f b7  |.....f..>.f3.f..|
00000160  8e 18 00 66 f7 f1 66 42  88 96 45 00 66 33 d2 66  |...f..fB..E.f3.f|
00000170  0f b7 8e 1a 00 66 f7 f1  88 96 44 00 89 86 42 00  |.....f....D...B.|
00000180  b8 01 02 8b 8e 42 00 c0  e5 06 0a ae 45 00 86 e9  |.....B......E...|
00000190  8a b6 44 00 8a 96 24 00  cd 13 c3 80 3e c2 07 06  |..D...$.....>...|
000001a0  74 29 b8 01 02 bb 00 06  b9 01 00 b6 00 8a 96 24  |t).............$|
000001b0  00 cd 13 72 16 c6 06 c2  07 06 b8 01 03 bb 00 06  |...r............|
000001c0  b9 01 00 b6 00 8a 96 24  00 cd 13 c3 44 69 73 6b  |.......$....Disk|
000001d0  20 65 72 72 6f 72 0d 0a  00 4d 69 73 73 69 6e 67  | error...Missing|
000001e0  20 27 69 6f 2e 73 79 73  27 0d 0a 00 49 4f 20 20  | 'io.sys'...IO  |
000001f0  20 20 20 20 53 59 53 00  00 00 00 00 00 01 55 aa  |    SYS.......U.|
00000200

```


The Dell Utility can be booted, but I'm not sure if that has anything to do with the GRUB on that partition.

In Bodhi Linux, three Dell Utility partitions show up (I'm writing from Bodhi now). One (/sda5) is my other Ubuntu-based OS, UberStudent (this is the partition I'd like to wipe out and use for Xubuntu), and the other two (/sda4 & /sda2) simply have a folder named "lost+found". The actual Dell Utility partition doesn't show up, but I don't need it anyway. It seems as though the other partitions were automatically named Dell Utility on their own.

---

### Post by CheshireKat on 2011-09-19
Okay, ran again and copied whole thing:
```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file /sda_mbr.bak looks at 
                       sector 1 of the same hard drive for core.img, but 
                       core.img can not be found at this location.
    Operating System:  Windows 95
    Boot files:        /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......Sf.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 845056 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262   6 FAT16
/dev/sda2    *         80,325    11,032,575    10,952,251  83 Linux
/dev/sda3          22,747,134    58,603,519    35,856,386   5 Extended
/dev/sda5    *     45,709,312    57,942,015    12,232,704  83 Linux
/dev/sda6          57,944,064    58,603,519       659,456  82 Linux swap / Solaris
/dev/sda7          22,747,136    44,640,255    21,893,120  83 Linux
/dev/sda8          44,642,304    45,705,215     1,062,912  82 Linux swap / Solaris
/dev/sda4          11,032,576    22,746,661    11,714,086  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.2 GB, 16231956480 bytes
255 heads, 63 sectors/track, 1973 cylinders, total 31703040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    31,696,244    31,696,182   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D3-041D                              vfat       DellUtility
/dev/sda2        91402ca0-c7bc-4396-adf8-937cdbd384e9   ext3       
/dev/sda4        d3fc596c-3de7-47f6-83e4-c28cd06f54e7   ext2       
/dev/sda5        86183267-42ed-446d-88aa-a09e634e8b58   ext4       
/dev/sda6        aa5d44de-5c19-4499-b3e8-94afd6c04326   swap       
/dev/sda7        d48904b0-0247-4771-8fa2-6dc11478098b   ext4       
/dev/sda8        59b8d020-0259-4a4d-9da3-80d72b561b2a   swap       
/dev/sdb1        E8AD-290C                              vfat       FLASH

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/sda1              vfat       (rw)
/dev/sda2        /media/sda2              ext3       (rw)
/dev/sda4        /media/sda4              ext2       (rw)
/dev/sda5        /media/sda5              ext4       (rw)
/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/FLASH         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /media/Plop Boot Manager 5.0.13 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             initrd.gz                                      1

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 86183267-42ed-446d-88aa-a09e634e8b58
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
search --no-floppy --fs-uuid --set 86183267-42ed-446d-88aa-a09e634e8b58
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 86183267-42ed-446d-88aa-a09e634e8b58
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=86183267-42ed-446d-88aa-a09e634e8b58 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 86183267-42ed-446d-88aa-a09e634e8b58
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=86183267-42ed-446d-88aa-a09e634e8b58 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 86183267-42ed-446d-88aa-a09e634e8b58
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 86183267-42ed-446d-88aa-a09e634e8b58
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

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
UUID=86183267-42ed-446d-88aa-a09e634e8b58 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=aa5d44de-5c19-4499-b3e8-94afd6c04326 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  21.947502136 = 23.565950976   boot/grub/core.img                             1
  21.976802826 = 23.597412352   boot/grub/grub.cfg                             1
  23.305809021 = 25.024421888   boot/initrd.img-2.6.32-24-generic              2
  23.064407349 = 24.765218816   boot/vmlinuz-2.6.32-24-generic                 1
  23.305809021 = 25.024421888   initrd.img                                     2
  23.064407349 = 24.765218816   vmlinuz                                        1

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set d48904b0-0247-4771-8fa2-6dc11478098b
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set d48904b0-0247-4771-8fa2-6dc11478098b
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
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set d48904b0-0247-4771-8fa2-6dc11478098b
insmod png
if background_image /usr/share/backgrounds/grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Bodhi Linux, with Linux 2.6.39-2-generic' --class bodhi --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set d48904b0-0247-4771-8fa2-6dc11478098b
	linux	/boot/vmlinuz-2.6.39-2-generic root=UUID=d48904b0-0247-4771-8fa2-6dc11478098b ro   splash quiet
	initrd	/boot/initrd.img-2.6.39-2-generic
}
menuentry 'Bodhi Linux, with Linux 2.6.39-2-generic (recovery mode)' --class bodhi --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set d48904b0-0247-4771-8fa2-6dc11478098b
	echo	'Loading Linux 2.6.39-2-generic ...'
	linux	/boot/vmlinuz-2.6.39-2-generic root=UUID=d48904b0-0247-4771-8fa2-6dc11478098b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.39-2-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set d48904b0-0247-4771-8fa2-6dc11478098b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set d48904b0-0247-4771-8fa2-6dc11478098b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 86183267-42ed-446d-88aa-a09e634e8b58
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=86183267-42ed-446d-88aa-a09e634e8b58 ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 86183267-42ed-446d-88aa-a09e634e8b58
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=86183267-42ed-446d-88aa-a09e634e8b58 ro single
	initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
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
# / was on /dev/sda7 during installation
UUID=d48904b0-0247-4771-8fa2-6dc11478098b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=59b8d020-0259-4a4d-9da3-80d72b561b2a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  13.027305603 = 13.987962880   boot/grub/core.img                             1
  17.588802338 = 18.885832704   boot/grub/grub.cfg                             2
  14.136802673 = 15.179276288   boot/initrd.img-2.6.39-2-generic               2
  11.389648438 = 12.229541888   boot/vmlinuz-2.6.39-2-generic                  2
  14.136802673 = 15.179276288   initrd.img                                     2
  11.389648438 = 12.229541888   vmlinuz                                        2

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 46 90 44 65 6c 6c 20  34 2e 31 00 02 04 01 00  |.F.Dell 4.1.....|
00000010  02 00 02 00 00 f8 4f 00  3f 00 ff 00 3f 00 00 00  |......O.?...?...|
00000020  86 39 01 00 80 00 29 1d  04 d3 07 44 65 6c 6c 55  |.9....)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 00 00  |tilityFAT16   ..|
00000040  00 00 00 00 00 00 00 00  fa b8 00 00 8e d0 bc fc  |................|
00000050  7b fb fc 8e d8 ff 0e 13  04 8b 0e 13 04 c1 e1 06  |{...............|
00000060  8e c1 b9 00 01 33 f6 33  ff f3 66 a5 c7 06 72 04  |.....3.3..f...r.|
00000070  45 44 8e c0 bd 00 7c e8  21 01 0f 82 bb 00 66 0f  |ED....|.!.....f.|
00000080  b7 86 16 00 66 d1 e0 66  0f b7 9e 0e 00 66 03 c3  |....f..f.....f..|
00000090  66 03 86 1c 00 66 89 86  3e 00 8b 86 11 00 c1 e8  |f....f..>.......|
000000a0  04 89 86 46 00 bb 00 05  e8 aa 00 0f 82 8a 00 ba  |...F............|
000000b0  10 00 b9 0b 00 be ec 7d  8b fb f3 a6 74 16 83 c3  |.......}....t...|
000000c0  20 4a 75 ee 66 ff 86 3e  00 ff 8e 46 00 75 d6 be  | Ju.f..>...F.u..|
000000d0  d9 7d eb 6d 66 0f b7 86  11 00 66 ba 20 00 00 00  |.}.mf.....f. ...|
000000e0  66 f7 e2 66 0f b7 8e 0b  00 66 03 c1 66 48 66 f7  |f..f.....f..fHf.|
000000f0  f1 66 01 86 3e 00 66 8b  86 3e 00 66 89 46 fc 66  |.f..>.f..>.f.F.f|
00000100  0f b7 47 1a 8b f8 2d 02  00 66 0f b6 9e 0d 00 66  |..G...-..f.....f|
00000110  f7 e3 66 01 86 3e 00 bb  00 07 c7 86 46 00 04 00  |..f..>......F...|
00000120  e8 32 00 72 14 81 c3 00  02 66 ff 86 3e 00 ff 8e  |.2.r.....f..>...|
00000130  46 00 75 ec ea 00 02 70  00 be cc 7d eb 03 be d9  |F.u....p...}....|
00000140  7d e8 02 00 eb fe ac 3c  00 74 09 b4 0e bb 07 00  |}......<.t......|
00000150  cd 10 eb f2 c3 66 8b 86  3e 00 66 33 d2 66 0f b7  |.....f..>.f3.f..|
00000160  8e 18 00 66 f7 f1 66 42  88 96 45 00 66 33 d2 66  |...f..fB..E.f3.f|
00000170  0f b7 8e 1a 00 66 f7 f1  88 96 44 00 89 86 42 00  |.....f....D...B.|
00000180  b8 01 02 8b 8e 42 00 c0  e5 06 0a ae 45 00 86 e9  |.....B......E...|
00000190  8a b6 44 00 8a 96 24 00  cd 13 c3 80 3e c2 07 06  |..D...$.....>...|
000001a0  74 29 b8 01 02 bb 00 06  b9 01 00 b6 00 8a 96 24  |t).............$|
000001b0  00 cd 13 72 16 c6 06 c2  07 06 b8 01 03 bb 00 06  |...r............|
000001c0  b9 01 00 b6 00 8a 96 24  00 cd 13 c3 44 69 73 6b  |.......$....Disk|
000001d0  20 65 72 72 6f 72 0d 0a  00 4d 69 73 73 69 6e 67  | error...Missing|
000001e0  20 27 69 6f 2e 73 79 73  27 0d 0a 00 49 4f 20 20  | 'io.sys'...IO  |
000001f0  20 20 20 20 53 59 53 00  00 00 00 00 00 01 55 aa  |    SYS.......U.|
00000200

```


The Dell Utility can be booted, but I'm not sure if that has anything to do with the GRUB on that partition.

In Bodhi Linux, three Dell Utility partitions show up (I'm writing from Bodhi now). One (/sda5) is my other Ubuntu-based OS, UberStudent (this is the partition I'd like to wipe out and use for Xubuntu), and the other two (/sda4 & /sda2) simply have a folder named "lost+found". The actual Dell Utility partition doesn't show up, but I don't need it anyway. It seems as though the other partitions were automatically named Dell Utility on their own.

---

### Post by coffeecat on 2011-09-19
> **CheshireKat said:**
> It seems as though the other partitions were automatically named Dell Utility on their own.

Actually, no. Have a look at this from your output:

```
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D3-041D                              vfat       DellUtility
/dev/sda2        91402ca0-c7bc-4396-adf8-937cdbd384e9   ext3       
/dev/sda4        d3fc596c-3de7-47f6-83e4-c28cd06f54e7   ext2       
/dev/sda5        86183267-42ed-446d-88aa-a09e634e8b58   ext4       
/dev/sda6        aa5d44de-5c19-4499-b3e8-94afd6c04326   swap       
/dev/sda7        d48904b0-0247-4771-8fa2-6dc11478098b   ext4       
/dev/sda8        59b8d020-0259-4a4d-9da3-80d72b561b2a   swap       
/dev/sdb1        E8AD-290C                              vfat       FLASH


```

Only your sda1 partition and your flash drive (sdb1) have labels. I would think that Dell Utility appearing three times in Bodhi is a glitch. I don't have any experience of Bodhi Linux, so I can't comment further.

How about this? Your sda2 (primary) and sda5 and sda6 (logical) partitions add up to approx 12GB - a good size for a Linux installation. You can't combine the space as it stands at the moment because the primary is outside the extended. What you could do is to delete sda2 and then enlarge the extended (sda3) backwards to take over the space vacated by sda2. Then delete sda5 and sda6, and create a new ext4 logical partition in the 12GB space as your proposed Xubuntu root partition. Xubuntu could share the sda8 swap. Doing this, however, would renumber sda7 and sda8. This wouldn't matter in Ubuntu, because Ubuntu uses UUIDs in /etc/fstab and grub configurations. I don't know what Bodhi Lunux uses - you would need to check this.

---

### Post by CheshireKat on 2011-09-19
Bodhi Linux uses Ubuntu 10.4 as its base, so if Ubuntu will be fine with it, then Bodhi should as well I would think (and hope). Okay, I'll give your suggestions a try when I have time (probably tomorrow when I don't have schoolwork). Thanks!

Just out of curiosity, any ideas on how those two other partitions were created or their supposed purpose? I guess it doesn't matter so much as long as it doesn't cause serious/major issues, but I know I didn't create them, so...I think it's kinda weird.

---

### Post by coffeecat on 2011-09-20
> **CheshireKat said:**
> Bodhi Linux uses Ubuntu 10.4 as its base, so if Ubuntu will be fine with it, then Bodhi should as well I would think (and hope).

If you're referring to the Dell partition appearing thrice, then this may be something to do with the desktop that Bodhi is using, enlightenment. The functionality of displaying partitions in the file manager (if that's where you're seeing this tripling) is built into the desktop GUI libraries. But intriguing. I've been meaning to give Bodhi Linux a spin myself - I could see what it makes of my menagerie of partitions! :) 

> **CheshireKat said:**
>  Okay, I'll give your suggestions a try when I have time (probably tomorrow when I don't have schoolwork). Thanks!

Good luck with that. Usual caution about backing your data up before manipulating partitions. Also, you'll need to use Gparted in a live CD. In Gparted, you'll need to right-click on each of the swap partitions and choose "swapoff" otherwise the extended partition will be locked and you won't be able to resize it.

> **CheshireKat said:**
> Just out of curiosity, any ideas on how those two other partitions were created or their supposed purpose? I guess it doesn't matter so much as long as it doesn't cause serious/major issues, but I know I didn't create them, so...I think it's kinda weird.

No idea on that. Interesting that one of them is the non-journalled ext2.

---

