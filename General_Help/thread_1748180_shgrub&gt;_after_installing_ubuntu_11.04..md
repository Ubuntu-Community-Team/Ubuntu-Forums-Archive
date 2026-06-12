---
title: "sh:grub&gt; after installing ubuntu 11.04."
date: 2011-05-03
forum: General Help
---

### Post by BlasterXL on 2011-05-03
Hello there, I got a problem after installing Ubuntu 11.04. (Just from the update manager). I Guess it went wrong after I selected to update Grub. When I start my computer, the only thing is see is: 

*sh:grub>*

So that is the whole problem, I googled alot, but I'm stuck and I'm pretty noob. So I want to repair my grub menu to start Or Windows Or Ubuntu again, for now, I can't start anything. Maybe someone could help.

Things I googled and tried,


*sudo fdisk -lu* **gives me these results**:

```

[I]Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6325b1f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1953521663   976759808    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd52e5cfc


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1         1686825  1920747464   959530320    f  W95 Ext'd (LBA)
/dev/sdb2      1920747465  1953520064    16386300   83  Linux
/dev/sdb5   *     1686888  1833771554   916042333+   7  HPFS/NTFS
/dev/sdb6      1876954338  1918835729    20940696   83  Linux
/dev/sdb7      1918835793  1920747464      955836   82  Linux swap / Solaris
/dev/sdb8      1833771618  1875058604    20643493+  83  Linux
/dev/sdb9      1875058668  1876954274      947803+  82  Linux swap / Solaris[/I]

```

**When I try this:**
```
[I]sudo grub
grub> find /grub.stage1[/I]
```
It gets me an error: *Error15: File not found.*

**Or: **
```
*find /boot/grub/stage1*
```
Now nothing happens.


**When I type this:**
```
*gksudo gedit grub.lst*
```
It opens an empty file.


**And when I try this:**
```
*grub-install -v* 
```
It says: grub-install (GNU GRUB 0.97)



I'm really stuck. Maybe someone can help. Big thanks of course.
I can still boot Ubuntu from CD-rom, All my files are still on the disk. (Thank god). But I want to be able to boot again :)

*Sorry for my bad english :)

---

### Post by Rubi1200 on 2011-05-03
Hi,

please do the following so we can get a better overview of what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by BlasterXL on 2011-05-03
Thank you very much for the quick answering.

I did like you say, here is the output:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=288be4e4-ffab-4913-b079-b853a28ae12d)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sdb9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6325b1f2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd52e5cfc

Partition  Boot         Start           End          Size  Id System

/dev/sdb1           1,686,825 1,920,747,464 1,919,060,640   f W95 Ext d (LBA)
/dev/sdb5    *      1,686,888 1,833,771,554 1,832,084,667   7 HPFS/NTFS
/dev/sdb6       1,876,954,338 1,918,835,729    41,881,392  83 Linux
/dev/sdb7       1,918,835,793 1,920,747,464     1,911,672  82 Linux swap / Solaris
/dev/sdb8       1,833,771,618 1,875,058,604    41,286,987  83 Linux
/dev/sdb9       1,875,058,668 1,876,954,274     1,895,607  82 Linux swap / Solaris
/dev/sdb2       1,920,747,465 1,953,520,064    32,772,600  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        80C2F69090FA0800                       ntfs                                     
/dev/sdb2        58237e36-a7e0-45c7-b0ae-e56a8c176040   ext4                                     
/dev/sdb5        01C9EC69648C5750                       ntfs       Windows7                      
/dev/sdb6        bcccf90c-32dd-4836-81c3-b1fd17629129   ext4                                     
/dev/sdb7        0a4efef1-86eb-4d85-a581-52d3c982c1e9   swap                                     
/dev/sdb8        288be4e4-ffab-4913-b079-b853a28ae12d   ext4                                     
/dev/sdb9        8d892113-3c26-44d5-959d-36e137ecdd40   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf
```

I see alot of these errors: *unknown filesystem type 'ext4'.* 
So I was thinking, I just started Ubuntu from CD-rom, but it's an older version; *8.04*, maybe this does not recognize the EXT4 file system? I'm already downing 11.04 manually, let me know if I might need it. (I'll burn it  on Cd-rom anyway).

---

### Post by BlasterXL on 2011-05-03
Ok, now I also tried with Ubuntu 11.04, booted from CD-rom.
Here are the (more detailed) results:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=288be4e4-ffab-4913-b079-b853a28ae12d)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1           1,686,825 1,920,747,464 1,919,060,640   f W95 Ext d (LBA)
/dev/sdb5    *      1,686,888 1,833,771,554 1,832,084,667   7 HPFS/NTFS
/dev/sdb6       1,876,954,338 1,918,835,729    41,881,392  83 Linux
/dev/sdb7       1,918,835,793 1,920,747,464     1,911,672  82 Linux swap / Solaris
/dev/sdb8       1,833,771,618 1,875,058,604    41,286,987  83 Linux
/dev/sdb9       1,875,058,668 1,876,954,274     1,895,607  82 Linux swap / Solaris
/dev/sdb2       1,920,747,465 1,953,520,064    32,772,600  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        80C2F69090FA0800                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        58237e36-a7e0-45c7-b0ae-e56a8c176040   ext4                                     
/dev/sdb5        01C9EC69648C5750                       ntfs       Windows7                      
/dev/sdb6        bcccf90c-32dd-4836-81c3-b1fd17629129   ext4                                     
/dev/sdb7        0a4efef1-86eb-4d85-a581-52d3c982c1e9   swap                                     
/dev/sdb8        288be4e4-ffab-4913-b079-b853a28ae12d   ext4                                     
/dev/sdb9        8d892113-3c26-44d5-959d-36e137ecdd40   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=bcccf90c-32dd-4836-81c3-b1fd17629129 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=0a4efef1-86eb-4d85-a581-52d3c982c1e9 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=========================== sdb8/boot/grub/grub.cfg: ===========================

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
true
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos8)'
search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
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
menuentry 'Ubuntu, met Linux 2.6.38-9-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
	linux	/boot/vmlinuz-2.6.38-9-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro vga=769  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-9-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.38-9-generic-pae (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
	echo	'Loading Linux 2.6.38-9-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-9-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro single vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-9-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, met Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro vga=769  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.35-28-generic-pae (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro single vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro vga=769  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.35-27-generic-pae (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
	echo	'Loading Linux 2.6.35-27-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro single vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro vga=769  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.35-24-generic-pae (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro single vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.32-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
	linux	/boot/vmlinuz-2.6.32-27-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro vga=769  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.32-27-generic-pae (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
	echo	'Loading Linux 2.6.32-27-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-27-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro single vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.31-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro vga=769  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.31-21-generic-pae (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
	echo	'Loading Linux 2.6.31-21-generic-pae ...'
	linux	/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro single vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos8)'
	search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 80C2F69090FA0800
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

=============================== sdb8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

# Entry for /dev/sda1 :
UUID=80C2F69090FA0800 /media/80C2F69090FA0800 ntfs-3g users 0 0
# Entry for /dev/sdb5 :
UUID=01C9EC69648C5750 /media/Windows7 ntfs-3g users 0 0
# Entry for /dev/sdb6 :
UUID=bcccf90c-32dd-4836-81c3-b1fd17629129 /media/bcccf90c-32dd-4836-81c3-b1fd17629129 ext4 defaults 0 0
# Entry for /dev/sdb7 :
UUID=0a4efef1-86eb-4d85-a581-52d3c982c1e9 swap swap sw 0 0
# Entry for /dev/sdb8 :
UUID=288be4e4-ffab-4913-b079-b853a28ae12d / ext4 defaults 0 1
# Entry for /dev/sdb9 :
UUID=8d892113-3c26-44d5-959d-36e137ecdd40 swap swap sw 0 0

=================== sdb8: Location of files loaded by Grub: ===================


 939.1GB: boot/grub/core.img
 942.9GB: boot/grub/grub.cfg
 944.5GB: boot/initrd.img-2.6.31-21-generic-pae
 946.4GB: boot/initrd.img-2.6.32-27-generic-pae
 949.7GB: boot/initrd.img-2.6.35-24-generic-pae
 950.0GB: boot/initrd.img-2.6.35-27-generic-pae
 949.2GB: boot/initrd.img-2.6.35-28-generic-pae
 954.9GB: boot/initrd.img-2.6.38-9-generic-pae
 943.0GB: boot/vmlinuz-2.6.31-21-generic-pae
 947.5GB: boot/vmlinuz-2.6.32-27-generic-pae
 945.1GB: boot/vmlinuz-2.6.35-24-generic-pae
 945.2GB: boot/vmlinuz-2.6.35-27-generic-pae
 946.4GB: boot/vmlinuz-2.6.35-28-generic-pae
 944.5GB: boot/vmlinuz-2.6.38-9-generic-pae
 954.9GB: initrd.img
 949.2GB: initrd.img.old
 944.5GB: vmlinuz
 946.4GB: vmlinuz.old

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=58237e36-a7e0-45c7-b0ae-e56a8c176040 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf


```

I'm pretty impressed by this small program (Boot info script), it makes a lot of things visible.
It's acually the first time I see Ubuntu 11.04 (booted from cd-rom), some people don't like unity, but my first impressions are good. Hopefully I can get Compiz work again after all this. 
Waiting for further instructions. :)

---

### Post by rsteve on 2011-05-03
I have the same problem of not being able to boot except with USB pen drive.  Here is my script:
 Boot Info Script 0.55    dated February 15th, 2010                    

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2syn.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
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

/dev/sda1    *             63    16,798,319    16,798,257   c W95 FAT32 (LBA)
/dev/sda2          16,798,320   261,938,558   245,140,239   7 HPFS/NTFS
/dev/sda3         261,939,198   488,396,799   226,457,602   5 Extended
/dev/sda5         261,939,200   482,254,847   220,315,648  83 Linux
/dev/sda6         482,256,896   488,396,799     6,139,904  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
31 heads, 48 sectors/track, 5263 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          1,072     7,831,551     7,830,480   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4270-1BAA                              vfat       HP_RECOVERY                   
/dev/sda2        8620F02C20F024B9                       ntfs       HP_PAVILION                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b   ext4                                     
/dev/sda6        42df0869-809d-4350-a0b5-b3861b71c2c6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6FF7-243E                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 4270-1baa
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 8620F02C20F024B9
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=42df0869-809d-4350-a0b5-b3861b71c2c6 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 149.2GB: boot/grub/core.img
 143.5GB: boot/grub/grub.cfg
 137.4GB: boot/initrd.img-2.6.35-28-generic
 137.4GB: boot/initrd.img-2.6.38-8-generic
 149.3GB: boot/vmlinuz-2.6.35-28-generic
 145.7GB: boot/vmlinuz-2.6.38-8-generic
 137.4GB: initrd.img
 137.4GB: initrd.img.old
 145.7GB: vmlinuz
 149.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  33 36 da d0 bd 07 87 85  91 cd 9d c7 38 ca 89 0e  |36..........8...|
00000010  72 7d 2b aa 42 e8 c4 5c  c7 c7 43 ea 7f 0a ef a3  |r}+.B..\..C.....|
00000020  4d 58 e7 9c af a9 24 c8  f6 e4 ed 62 af e9 57 2d  |MX....$....b..W-|
00000030  b5 69 21 8b 60 da 40 07  ef 9c 63 3d 4d 6d ec d2  |.i!.`.@...c=Mm..|
00000040  d4 4a 6d 2b 15 2d af 95  e2 48 dc 93 85 c2 f7 a9  |.Jm+.-...H......|
00000050  23 9d 97 93 2e 14 74 06  a9 5a d6 15 ec 89 c1 69  |#.....t..Z.....i|
00000060  66 0a a4 94 ea 87 3d 7f  1a b5 71 b9 90 80 03 2e  |f.....=...q.....|
00000070  7a e6 ae 9e 84 39 5c a7  3a c6 80 6d 18 27 91 c5  |z....9\.:..m.'..|
00000080  65 a9 20 b2 a0 c6 7a 63  b5 69 be e4 a5 71 04 de  |e. ...zc.i...q..|
00000090  6a 91 26 e5 00 e0 8c ff  00 4a af 3d d9 8e 36 08  |j.&......J.=..6.|
000000a0  fc 74 1e d4 e2 9b 61 27  65 62 b4 53 79 b2 91 b1  |.t....a'eb.Sy...|
000000b0  91 b1 d0 f5 15 65 d6 48  d3 25 b0 3a 73 dc f6 ab  |.....e.H.%.:s...|
000000c0  b1 09 d8 82 e4 a4 32 12  bf 2a 10 09 1e fd ea e4  |......2..*......|
000000d0  36 e6 21 bc 7c aa 7a 8a  b6 f4 14 5f 36 c2 5c 2e  |6.!.|.z...._6.\.|
000000e0  e0 ec 43 17 63 f2 9c e3  68 f4 f7 a7 2b 34 58 7c  |..C.c...h...+4X||
000000f0  95 24 75 cd 26 c6 d9 62  da d0 5c db b1 23 cb ea  |.$u.&..b..\..#..|
00000100  71 e9 54 b4 dd 23 ec ef  e7 dc 3a 09 08 e1 81 ed  |q.T..#....:.....|
00000110  da b8 b1 0d b9 24 b6 2e  12 b1 62 f7 54 90 b8 8a  |.....$....b.T...|
00000120  15 ca f5 dd 59 b7 76 17  13 5a 12 d2 16 04 f3 83  |....Y.v..Z......|
00000130  d3 de b0 75 65 29 72 44  da ca 1a b3 38 f8 4a da  |...ue)rD....8.J.|
00000140  79 0c af 23 c8 38 06 22  df 29 1e e2 ac 26 9b f6  |y..#.8.".)...&..|
00000150  24 95 51 15 57 7e 77 0f  f3 d2 ba 21 1d 7d e3 09  |$.Q.W~w....!.}..|
00000160  4b 99 bb 11 b0 32 ed 2a  47 27 a9 ac 7d 46 da 3b  |K....2.*G'..}F.;|
00000170  9d e0 8d c8 57 81 e9 f8  d7 4b 8d ee 89 6f 96 c3  |....W....K...o..|
00000180  13 40 b2 85 51 cd bc 7b  b6 83 8c 64 53 a5 b6 b7  |.@..Q..{...dS...|
00000190  42 0a 41 1c 64 74 da 80  57 13 c1 ae 6b a3 5f 6d  |B.A.dt..W...k._m|
000001a0  ee 94 c2 2f 92 c1 ba 0e  de 99 ae 3e 6b 79 d6 64  |.../.......>ky.d|
000001b0  32 0f 31 63 1b 23 e3 3b  97 af 27 fa d1 8a 00 fe  |2.1c.#.;..'.....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c0 21 0d 00 fe  |............!...|
000001d0  ff ff 05 fe ff ff 85 c1  21 0d 7d b6 5d 00 00 00  |........!.}.]...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 26 00  |.X.SYSLINUX...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 30 04 00 00  |........?...0...|
00000020  d0 7b 77 00 d1 1d 00 00  00 00 00 00 02 00 00 00  |.{w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 3e 24 f7 6f 4e  4f 20 4e 41 4d 45 20 20  |..)>$.oNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 40 a2 0e 00  66 ba 00 00 00 00 bb 00  |}.f.@...f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by Rubi1200 on 2011-05-04
> **BlasterXL said:**
> Ok, now I also tried with Ubuntu 11.04, booted from CD-rom.
Here are the (more detailed) results:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=288be4e4-ffab-4913-b079-b853a28ae12d)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1           1,686,825 1,920,747,464 1,919,060,640   f W95 Ext d (LBA)
/dev/sdb5    *      1,686,888 1,833,771,554 1,832,084,667   7 HPFS/NTFS
/dev/sdb6       1,876,954,338 1,918,835,729    41,881,392  83 Linux
/dev/sdb7       1,918,835,793 1,920,747,464     1,911,672  82 Linux swap / Solaris
/dev/sdb8       1,833,771,618 1,875,058,604    41,286,987  83 Linux
/dev/sdb9       1,875,058,668 1,876,954,274     1,895,607  82 Linux swap / Solaris
/dev/sdb2       1,920,747,465 1,953,520,064    32,772,600  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        80C2F69090FA0800                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        58237e36-a7e0-45c7-b0ae-e56a8c176040   ext4                                     
/dev/sdb5        01C9EC69648C5750                       ntfs       Windows7                      
/dev/sdb6        bcccf90c-32dd-4836-81c3-b1fd17629129   ext4                                     
/dev/sdb7        0a4efef1-86eb-4d85-a581-52d3c982c1e9   swap                                     
/dev/sdb8        288be4e4-ffab-4913-b079-b853a28ae12d   ext4                                     
/dev/sdb9        8d892113-3c26-44d5-959d-36e137ecdd40   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=bcccf90c-32dd-4836-81c3-b1fd17629129 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=0a4efef1-86eb-4d85-a581-52d3c982c1e9 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=========================== sdb8/boot/grub/grub.cfg: ===========================

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
true
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos8)'
search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
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
menuentry 'Ubuntu, met Linux 2.6.38-9-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos8)'
    search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
    linux    /boot/vmlinuz-2.6.38-9-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro vga=769  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-9-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.38-9-generic-pae (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos8)'
    search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
    echo    'Loading Linux 2.6.38-9-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-9-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro single vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-9-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, met Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos8)'
    search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro vga=769  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.35-28-generic-pae (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos8)'
    search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro single vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos8)'
    search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro vga=769  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.35-27-generic-pae (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos8)'
    search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
    echo    'Loading Linux 2.6.35-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-27-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro single vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos8)'
    search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro vga=769  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.35-24-generic-pae (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos8)'
    search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
    echo    'Loading Linux 2.6.35-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro single vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.32-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos8)'
    search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro vga=769  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.32-27-generic-pae (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos8)'
    search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
    echo    'Loading Linux 2.6.32-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro single vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.31-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos8)'
    search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
    linux    /boot/vmlinuz-2.6.31-21-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro vga=769  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.31-21-generic-pae
}
menuentry 'Ubuntu, met Linux 2.6.31-21-generic-pae (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos8)'
    search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
    echo    'Loading Linux 2.6.31-21-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-21-generic-pae root=UUID=288be4e4-ffab-4913-b079-b853a28ae12d ro single vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos8)'
    search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos8)'
    search --no-floppy --fs-uuid --set=root 288be4e4-ffab-4913-b079-b853a28ae12d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 80C2F69090FA0800
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

=============================== sdb8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

# Entry for /dev/sda1 :
UUID=80C2F69090FA0800 /media/80C2F69090FA0800 ntfs-3g users 0 0
# Entry for /dev/sdb5 :
UUID=01C9EC69648C5750 /media/Windows7 ntfs-3g users 0 0
# Entry for /dev/sdb6 :
UUID=bcccf90c-32dd-4836-81c3-b1fd17629129 /media/bcccf90c-32dd-4836-81c3-b1fd17629129 ext4 defaults 0 0
# Entry for /dev/sdb7 :
UUID=0a4efef1-86eb-4d85-a581-52d3c982c1e9 swap swap sw 0 0
# Entry for /dev/sdb8 :
UUID=288be4e4-ffab-4913-b079-b853a28ae12d / ext4 defaults 0 1
# Entry for /dev/sdb9 :
UUID=8d892113-3c26-44d5-959d-36e137ecdd40 swap swap sw 0 0

=================== sdb8: Location of files loaded by Grub: ===================


 939.1GB: boot/grub/core.img
 942.9GB: boot/grub/grub.cfg
 944.5GB: boot/initrd.img-2.6.31-21-generic-pae
 946.4GB: boot/initrd.img-2.6.32-27-generic-pae
 949.7GB: boot/initrd.img-2.6.35-24-generic-pae
 950.0GB: boot/initrd.img-2.6.35-27-generic-pae
 949.2GB: boot/initrd.img-2.6.35-28-generic-pae
 954.9GB: boot/initrd.img-2.6.38-9-generic-pae
 943.0GB: boot/vmlinuz-2.6.31-21-generic-pae
 947.5GB: boot/vmlinuz-2.6.32-27-generic-pae
 945.1GB: boot/vmlinuz-2.6.35-24-generic-pae
 945.2GB: boot/vmlinuz-2.6.35-27-generic-pae
 946.4GB: boot/vmlinuz-2.6.35-28-generic-pae
 944.5GB: boot/vmlinuz-2.6.38-9-generic-pae
 954.9GB: initrd.img
 949.2GB: initrd.img.old
 944.5GB: vmlinuz
 946.4GB: vmlinuz.old

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=58237e36-a7e0-45c7-b0ae-e56a8c176040 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf


```I'm pretty impressed by this small program (Boot info script), it makes a lot of things visible.
It's acually the first time I see Ubuntu 11.04 (booted from cd-rom), some people don't like unity, but my first impressions are good. Hopefully I can get Compiz work again after all this. 
Waiting for further instructions. :)
I am confused :confused: You seem to have 2 Ubuntu installs and 2 swap partitions plus another Linux partition on sdb2.

Which partition have you been trying to boot? And, how did you end up in this situation. 

You need to first find out where your files are and save them before we try anything else.

---

### Post by Rubi1200 on 2011-05-04
> **rsteve said:**
> I have the same problem of not being able to boot except with USB pen drive.  Here is my script:
 Boot Info Script 0.55    dated February 15th, 2010                    

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2syn.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
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

/dev/sda1    *             63    16,798,319    16,798,257   c W95 FAT32 (LBA)
/dev/sda2          16,798,320   261,938,558   245,140,239   7 HPFS/NTFS
/dev/sda3         261,939,198   488,396,799   226,457,602   5 Extended
/dev/sda5         261,939,200   482,254,847   220,315,648  83 Linux
/dev/sda6         482,256,896   488,396,799     6,139,904  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
31 heads, 48 sectors/track, 5263 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          1,072     7,831,551     7,830,480   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4270-1BAA                              vfat       HP_RECOVERY                   
/dev/sda2        8620F02C20F024B9                       ntfs       HP_PAVILION                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b   ext4                                     
/dev/sda6        42df0869-809d-4350-a0b5-b3861b71c2c6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6FF7-243E                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 4270-1baa
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 8620F02C20F024B9
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=3db86e4e-3fdb-4ccd-878d-0b16a6cb8b2b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=42df0869-809d-4350-a0b5-b3861b71c2c6 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 149.2GB: boot/grub/core.img
 143.5GB: boot/grub/grub.cfg
 137.4GB: boot/initrd.img-2.6.35-28-generic
 137.4GB: boot/initrd.img-2.6.38-8-generic
 149.3GB: boot/vmlinuz-2.6.35-28-generic
 145.7GB: boot/vmlinuz-2.6.38-8-generic
 137.4GB: initrd.img
 137.4GB: initrd.img.old
 145.7GB: vmlinuz
 149.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  33 36 da d0 bd 07 87 85  91 cd 9d c7 38 ca 89 0e  |36..........8...|
00000010  72 7d 2b aa 42 e8 c4 5c  c7 c7 43 ea 7f 0a ef a3  |r}+.B..\..C.....|
00000020  4d 58 e7 9c af a9 24 c8  f6 e4 ed 62 af e9 57 2d  |MX....$....b..W-|
00000030  b5 69 21 8b 60 da 40 07  ef 9c 63 3d 4d 6d ec d2  |.i!.`.@...c=Mm..|
00000040  d4 4a 6d 2b 15 2d af 95  e2 48 dc 93 85 c2 f7 a9  |.Jm+.-...H......|
00000050  23 9d 97 93 2e 14 74 06  a9 5a d6 15 ec 89 c1 69  |#.....t..Z.....i|
00000060  66 0a a4 94 ea 87 3d 7f  1a b5 71 b9 90 80 03 2e  |f.....=...q.....|
00000070  7a e6 ae 9e 84 39 5c a7  3a c6 80 6d 18 27 91 c5  |z....9\.:..m.'..|
00000080  65 a9 20 b2 a0 c6 7a 63  b5 69 be e4 a5 71 04 de  |e. ...zc.i...q..|
00000090  6a 91 26 e5 00 e0 8c ff  00 4a af 3d d9 8e 36 08  |j.&......J.=..6.|
000000a0  fc 74 1e d4 e2 9b 61 27  65 62 b4 53 79 b2 91 b1  |.t....a'eb.Sy...|
000000b0  91 b1 d0 f5 15 65 d6 48  d3 25 b0 3a 73 dc f6 ab  |.....e.H.%.:s...|
000000c0  b1 09 d8 82 e4 a4 32 12  bf 2a 10 09 1e fd ea e4  |......2..*......|
000000d0  36 e6 21 bc 7c aa 7a 8a  b6 f4 14 5f 36 c2 5c 2e  |6.!.|.z...._6.\.|
000000e0  e0 ec 43 17 63 f2 9c e3  68 f4 f7 a7 2b 34 58 7c  |..C.c...h...+4X||
000000f0  95 24 75 cd 26 c6 d9 62  da d0 5c db b1 23 cb ea  |.$u.&..b..\..#..|
00000100  71 e9 54 b4 dd 23 ec ef  e7 dc 3a 09 08 e1 81 ed  |q.T..#....:.....|
00000110  da b8 b1 0d b9 24 b6 2e  12 b1 62 f7 54 90 b8 8a  |.....$....b.T...|
00000120  15 ca f5 dd 59 b7 76 17  13 5a 12 d2 16 04 f3 83  |....Y.v..Z......|
00000130  d3 de b0 75 65 29 72 44  da ca 1a b3 38 f8 4a da  |...ue)rD....8.J.|
00000140  79 0c af 23 c8 38 06 22  df 29 1e e2 ac 26 9b f6  |y..#.8.".)...&..|
00000150  24 95 51 15 57 7e 77 0f  f3 d2 ba 21 1d 7d e3 09  |$.Q.W~w....!.}..|
00000160  4b 99 bb 11 b0 32 ed 2a  47 27 a9 ac 7d 46 da 3b  |K....2.*G'..}F.;|
00000170  9d e0 8d c8 57 81 e9 f8  d7 4b 8d ee 89 6f 96 c3  |....W....K...o..|
00000180  13 40 b2 85 51 cd bc 7b  b6 83 8c 64 53 a5 b6 b7  |.@..Q..{...dS...|
00000190  42 0a 41 1c 64 74 da 80  57 13 c1 ae 6b a3 5f 6d  |B.A.dt..W...k._m|
000001a0  ee 94 c2 2f 92 c1 ba 0e  de 99 ae 3e 6b 79 d6 64  |.../.......>ky.d|
000001b0  32 0f 31 63 1b 23 e3 3b  97 af 27 fa d1 8a 00 fe  |2.1c.#.;..'.....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c0 21 0d 00 fe  |............!...|
000001d0  ff ff 05 fe ff ff 85 c1  21 0d 7d b6 5d 00 00 00  |........!.}.]...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 26 00  |.X.SYSLINUX...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 30 04 00 00  |........?...0...|
00000020  d0 7b 77 00 d1 1d 00 00  00 00 00 00 02 00 00 00  |.{w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 3e 24 f7 6f 4e  4f 20 4e 41 4d 45 20 20  |..)>$.oNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 40 a2 0e 00  66 ba 00 00 00 00 bb 00  |}.f.@...f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```
Hi and welcome to the forums rsteve :-)

You really ought to start your own thread as your issue is not quite the same.

In any event, you need to reinstall GRUB from the LiveCD.

Use these instructions and make sure GRUB is installed to the MBR of sda:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

In other words, mount sda5 and install to sda.

Don't forget to run the update-grub command back in Ubuntu.

---

### Post by BlasterXL on 2011-05-07
I made a backup of all the important files. I just want to start Windows 7 so I can make a backup of all my music files (fl-studio/ reason). After that Ill reinstall everything, its a mess indeed, don't ask how :) .. Maybe its a Raid1 configuration? I tried booting from both HDD, changed in the bios, but in both situations I got: *sh:grub>*

---

### Post by josephku on 2011-05-07
Hello.  I found my self in a similar situation as you tonight.  Basically, grub.cfg was corrupt.  I was also stuck at the grub> prompt.  To fix it I did something like this:

grub> linux (hd2,2)/boot/vmlinuz root=/dev/sda5
grub> initrd (hd2,2)/initrd.img
grub> boot

Maybe this could help you. While typing the above commands, pressing a TAB key displayed possible command completions.  From your output I guess your 11.04 installation is on the logical drive of an extended partition.  In any case try the TAB key to help complete the commands and find the vmlinuz and initrd.img files as indicated in my example and you may just get 11.04 booted.  Once you are up in 11.04, use the update-grub command in a terminal to regenerate your grub.cfg file (if it was corrupt like mine). I am unsure what "(hdx,y)" you should be using.  The TAB key should help. Good luck.

---

### Post by BlasterXL on 2011-05-07
Ok, I got everything fixed now. What I did was to simple.
I just installed Ubuntu 11.04 again with the Ubuntu Cd-rom, deleted all the partitions *except* the windows (ntfs) partitions.
Then I created a new EXT4 partition and Swap partition and installed Ubuntu again. Grub menu is restored! I can start Windows7 and Ubuntu again! I hope this will help someone else to. Thanks for all the help again.

---

