---
title: "Help with Grub2"
date: 2011-06-27
forum: General Help
---

### Post by strange_cathect on 2011-06-27
I've been having some difficulty with Grub2 lately and would like someone with more experience to view the output from my boot script to tell me if all is well. 

I've read that you shouldn't install Grub2 to a partition; instead, it should be placed in the MBR of the hard drive where you keep /.

I'm a little confused about what I'm seeing here. Can anyone look over this and tell me if I screwed up on the install? Thanks.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for (,msdos3)/boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda3 and looks at sector 38030352 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 3 for (,msdos3)/boot/grub.
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1         910,146,510   976,768,064    66,621,555  82 Linux swap / Solaris
/dev/sda2         133,548,345   910,146,509   776,598,165  83 Linux
/dev/sda3    *          2,048   133,548,344   133,546,297  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               6,144   153,788,415   153,782,272  83 Linux
/dev/sdb2         153,788,416   625,141,759   471,353,344  83 Linux
```

---

### Post by Quackers on 2011-06-27
You've chopped off about 80% of the boot script output :-)
What I can see looks ok, if sdb1 is a second Linux root partition.

The MBR of the hard drive is the first sector of the drive. This is not where "/" is kept. That is in your root partition.

What grub problems are you experiencing?

---

### Post by strange_cathect on 2011-06-27
{edit}

---

### Post by strange_cathect on 2011-06-27
Hi.

/dev/sdb is just an extra hard drive that has backup data. I don't know why /sdb has grub installed there. Should I try to remove this?

I have had problems with grub ever since the upgrade that gave me Grub2. Basically, every time I try to do an upgrade to a new version of Ubuntu Grub breaks and I have to reinstall.

Should I try to remove the grub that is on my second drive (sdb)? 

Here is the rest of my boot script, if it is helpful.

                ```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for (,msdos3)/boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda3 and looks at sector 38030352 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 3 for (,msdos3)/boot/grub.
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1         910,146,510   976,768,064    66,621,555  82 Linux swap / Solaris
/dev/sda2         133,548,345   910,146,509   776,598,165  83 Linux
/dev/sda3    *          2,048   133,548,344   133,546,297  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               6,144   153,788,415   153,782,272  83 Linux
/dev/sdb2         153,788,416   625,141,759   471,353,344  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        916aa027-e796-45a9-a358-e4fe5c866c8d   swap       
/dev/sda2        841868a3-a027-4f40-9d14-c68fb3d5cf80   ext3       
/dev/sda3        9c88acfc-7f2e-4740-b4be-fc449adcd1c3   ext4       
/dev/sdb1        e8803af6-4c7f-4766-ba6e-be711320494d   ext3       Backup
/dev/sdb2        69d704f4-72fd-49d5-8902-33132c9960a1   ext3       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /home                    ext3       (rw,commit=0)
/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb2        /Backup                  ext3       (rw,commit=0)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 9c88acfc-7f2e-4740-b4be-fc449adcd1c3
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 9c88acfc-7f2e-4740-b4be-fc449adcd1c3
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
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9c88acfc-7f2e-4740-b4be-fc449adcd1c3
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=9c88acfc-7f2e-4740-b4be-fc449adcd1c3 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9c88acfc-7f2e-4740-b4be-fc449adcd1c3
	echo	'Loading Linux 2.6.35-30-generic ...'
	linux	/boot/vmlinuz-2.6.35-30-generic root=UUID=9c88acfc-7f2e-4740-b4be-fc449adcd1c3 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9c88acfc-7f2e-4740-b4be-fc449adcd1c3
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=9c88acfc-7f2e-4740-b4be-fc449adcd1c3 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9c88acfc-7f2e-4740-b4be-fc449adcd1c3
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=9c88acfc-7f2e-4740-b4be-fc449adcd1c3 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9c88acfc-7f2e-4740-b4be-fc449adcd1c3
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=9c88acfc-7f2e-4740-b4be-fc449adcd1c3 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9c88acfc-7f2e-4740-b4be-fc449adcd1c3
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=9c88acfc-7f2e-4740-b4be-fc449adcd1c3 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9c88acfc-7f2e-4740-b4be-fc449adcd1c3
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=9c88acfc-7f2e-4740-b4be-fc449adcd1c3 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9c88acfc-7f2e-4740-b4be-fc449adcd1c3
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=9c88acfc-7f2e-4740-b4be-fc449adcd1c3 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9c88acfc-7f2e-4740-b4be-fc449adcd1c3
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=9c88acfc-7f2e-4740-b4be-fc449adcd1c3 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9c88acfc-7f2e-4740-b4be-fc449adcd1c3
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=9c88acfc-7f2e-4740-b4be-fc449adcd1c3 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9c88acfc-7f2e-4740-b4be-fc449adcd1c3
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=9c88acfc-7f2e-4740-b4be-fc449adcd1c3 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9c88acfc-7f2e-4740-b4be-fc449adcd1c3
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=9c88acfc-7f2e-4740-b4be-fc449adcd1c3 ro single  splash quiet vga=795
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9c88acfc-7f2e-4740-b4be-fc449adcd1c3
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=9c88acfc-7f2e-4740-b4be-fc449adcd1c3 ro  splash quiet vga=795  quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9c88acfc-7f2e-4740-b4be-fc449adcd1c3
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=9c88acfc-7f2e-4740-b4be-fc449adcd1c3 ro single  splash quiet vga=795
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9c88acfc-7f2e-4740-b4be-fc449adcd1c3
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 9c88acfc-7f2e-4740-b4be-fc449adcd1c3
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=9c88acfc-7f2e-4740-b4be-fc449adcd1c3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=841868a3-a027-4f40-9d14-c68fb3d5cf80 /home           ext3    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=916aa027-e796-45a9-a358-e4fe5c866c8d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

UUID=69d704f4-72fd-49d5-8902-33132c9960a1 /Backup ext3 defaults 0 0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  18.134307861 = 19.471564800   boot/grub/core.img                             1
  62.144039154 = 66.726653952   boot/grub/grub.cfg                             2
   2.445510864 = 2.625847296    boot/initrd.img-2.6.35-22-generic              2
   3.156448364 = 3.389210624    boot/initrd.img-2.6.35-23-generic              1
   3.195514679 = 3.431157760    boot/initrd.img-2.6.35-24-generic              2
   3.211139679 = 3.447934976    boot/initrd.img-2.6.35-25-generic              1
   3.226772308 = 3.464720384    boot/initrd.img-2.6.35-27-generic              1
   3.445522308 = 3.699601408    boot/initrd.img-2.6.35-28-generic              2
   3.250213623 = 3.489890304    boot/initrd.img-2.6.35-30-generic              2
  18.138305664 = 19.475857408   boot/vmlinuz-2.6.35-22-generic                 1
  18.153171539 = 19.491819520   boot/vmlinuz-2.6.35-23-generic                 1
  18.157173157 = 19.496116224   boot/vmlinuz-2.6.35-24-generic                 1
  18.254978180 = 19.601133568   boot/vmlinuz-2.6.35-25-generic                 1
  18.258979797 = 19.605430272   boot/vmlinuz-2.6.35-27-generic                 1
  18.132854462 = 19.470004224   boot/vmlinuz-2.6.35-28-generic                 1
  18.262985229 = 19.609731072   boot/vmlinuz-2.6.35-30-generic                 1
   3.250213623 = 3.489890304    initrd.img                                     2
   3.226772308 = 3.464720384    initrd.img.old                                 1
  18.262985229 = 19.609731072   vmlinuz                                        1
  18.258979797 = 19.605430272   vmlinuz.old                                    1

```

---

### Post by drs305 on 2011-06-27
Other than G2 was once installed to a partition (sda3), the files currently look ok. That was done at some point by selecting a partition (sda3) on which to install Grub2, rather than the drive (sda). For most users, installing onto a specific partition is not a good idea.

You might want to install G2 to the sdb bootloader just so if you should ever boot that drive first it still points to your real installation on sda3. It currently would fail. I'd run the command on sda as well afterward just to make sure.

From your normally-running Ubuntu:
```
sudo grub-install /dev/sdb
sudo grub-install /dev/sda
sudo update-grub
```

---

### Post by strange_cathect on 2011-06-28
Thanks for your help.

You say that Grub was *once* installed to sda3 and that I should install Grub to the MBR of sdb, as well as sda. I'm just curious as to how you determined this. From looking at the boot info it seems to suggest that I already do have Grub on the MBR of both sda and sdb as well as sda3 partition.

Am I missing something?

---

### Post by drs305 on 2011-06-28
> **strange_cathect said:**
> Thanks for your help.

You say that Grub was *once* installed to sda3 and that I should install Grub to the MBR of sdb, as well as sda. I'm just curious as to how you determined this. From looking at the boot info it seems to suggest that I already do have Grub on the MBR of both sda and sdb as well as sda3 partition.

Am I missing something?

Here is what I looked at:
> [noparse]
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 1 of the same hard drive for core.img. core.img is at this location and looks in[/noparse] **partition 3** for (,msdos3)/boot/grub.

This shows G2 is installed on the sda MBR and correctly points to your Ubuntu installation on sda3
> [noparse]
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 1 of the same hard drive for core.img. core.img is at this location and looks in[/noparse] **partition 1** for /boot/grub.

The sdb MBR also has Grub2 information on it, but it points to partition 1. The boot info script has a few quirks which I won't get into here, but the script identifies that the sdb MBR points to 'partition 1'. There is no Ubuntu installation on either sda1 or sdb1, so the MBR is pointing to an incorrect location.

Therefore, installing G2 to the sdb MBR by running the commands previously cited will update it to look at the correct partition (sda3). Running the command again on the sda MBR is just a precaution and isn't really required, as it is already correct. I have a practice of always running the command on the controlling MBR last to ensure it has the latest information. Which MBR is used is actually based on the BIOS boot order.

> [noparse]
sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda3 and looks at sector 38030352 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 3 for (,msdos3)/boot/grub.[/noparse]


This shows G2 is also installed on the sda3 PBR. It's not being used, and it's a bit of a pain to zero it out, so I rarely provide instructions on how to clear it out as the 'risks' are greater than the 'benefit' of removing it.

---

### Post by strange_cathect on 2011-06-28
I see. Thanks for the explanation. And for your help. I executed those commands with no issues.

---

