---
title: "Grub Dual Boot in EFI mode - Windows 7/Xubuntu"
date: 2011-08-11
forum: General Help
---

### Post by ClickHeRe on 2011-08-11
Trying to learn as I'm quite new to doing all of this myself on a new PC that I've built from the ground up for personal development.

Here's the gist of the issue that I've tried to solve for a couple days with information found online but to no avail.

Here's the important information regarding the system
- Motherboard ASUS Sabertooth 990FX - UEFI Enabled
- 128GB SSD for Windows 7 (/dev/sdb)
- 64GB SSD for Xubuntu (/dev/sda)
- 1TB HDD for Data Share between both OS (/dev/sdc)

I've installed Windows 7 on it's own SSD and Xubuntu on it's own SSD, both in UEFI + GPT mode. Both were installed while the other was unplugged as I wanted to be sure not to **** up something (I also flashed the SSD firmware, etc. which recommends to only have the SSD + Media plugged in). I can boot from the motherboard menu to either one successfully (Xubuntu being the default).

The issue I'm trying to resolve is find the correct menu item to add to /etc/grub.d/40_custom so that Windows 7 appears in the menu (easy) but also boots successfully!!!

I found some information here: 
[https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT](https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT)

But that doesn't work. In fact it leads to a blank black screen where nothing happens forever (but it's better than before where I would only get an error about not loading an EFI file).

Os-prober also can't see Windows either.

Thanks in advance for the help.

----

Here's my bootscript dump

> 
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    467387 of the same hard drive for core.img, but core.img can not be found 
    at this location.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 528315 of the same hard drive for 
                       core.img. core.img is at this location and looks for 
                       (,gpt2)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdc1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   125,045,423   125,045,423  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34       195,346       195,313 EFI System partition
/dev/sda2         195,347     8,195,347     8,000,001 Data partition (Windows/Linux)
/dev/sda3       8,195,348    48,195,348    40,000,001 Data partition (Windows/Linux)
/dev/sda4      48,195,349    78,195,349    30,000,001 Data partition (Windows/Linux)
/dev/sda5      78,195,350    94,195,350    16,000,001 Data partition (Windows/Linux)
/dev/sda6      94,195,351    96,195,351     2,000,001 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 128.0 GB, 128035676160 bytes
256 heads, 63 sectors/track, 15505 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sdb1 ends after the last sector of /dev/sdb

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048       206,847       204,800 EFI System partition
/dev/sdb2         206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sdb3         468,992   250,068,991   249,600,000 Data partition (Windows/Linux)

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sdc1 ends after the last sector of /dev/sdc

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdc1              34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sdc2         264,192    21,235,711    20,971,520 Data partition (Windows/Linux)
/dev/sdc3      21,235,712 1,908,672,511 1,887,436,800 Data partition (Windows/Linux)
/dev/sdc4   1,908,672,512 1,953,521,663    44,849,152 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        0366-715C                              vfat       
/dev/sda2        293173a4-19a0-4fbd-9a83-d808ed2316eb   ext4       
/dev/sda3        069a90b5-f643-4254-8394-41057bac19b1   ext4       
/dev/sda4        893e5f8f-a176-4990-8e12-10fcf3e9aa4a   ext4       
/dev/sda5        61fcf11a-5c26-4db8-b10b-9d3ad6d81ab7   ext4       
/dev/sda6        b558501a-7dcf-412b-a079-20c6cfbe2439   ext4       
/dev/sdb1        D217-21A4                              vfat       
/dev/sdb3        88822A3E822A315C                       ntfs       WinMain
/dev/sdc2        EE3CE9363CE8FA8B                       ntfs       WinData
/dev/sdc3        727253047252CC8B                       ntfs       Media
/dev/sdc4        480E5D4C0E5D33E2                       ntfs       Data

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot/efi                vfat       (rw,noatime)
/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /usr                     ext4       (rw,noatime,discard,commit=0)
/dev/sda4        /usr/local               ext4       (rw,noatime,discard,commit=0)
/dev/sda5        /home                    ext4       (rw,noatime,discard,commit=0)
/dev/sda6        /var                     ext4       (rw,noatime,discard,commit=0)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt3)'
search --no-floppy --fs-uuid --set=root 069a90b5-f643-4254-8394-41057bac19b1
if loadfont /share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt2)'
search --no-floppy --fs-uuid --set=root 293173a4-19a0-4fbd-9a83-d808ed2316eb
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_gpt
	insmod ext2
	set root='(/dev/sda,gpt2)'
	search --no-floppy --fs-uuid --set=root 293173a4-19a0-4fbd-9a83-d808ed2316eb
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=293173a4-19a0-4fbd-9a83-d808ed2316eb ro   quiet splash elevator=noop vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_gpt
	insmod ext2
	set root='(/dev/sda,gpt2)'
	search --no-floppy --fs-uuid --set=root 293173a4-19a0-4fbd-9a83-d808ed2316eb
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=293173a4-19a0-4fbd-9a83-d808ed2316eb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_gpt
	insmod ext2
	set root='(/dev/sda,gpt2)'
	search --no-floppy --fs-uuid --set=root 293173a4-19a0-4fbd-9a83-d808ed2316eb
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=293173a4-19a0-4fbd-9a83-d808ed2316eb ro   quiet splash elevator=noop vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_gpt
	insmod ext2
	set root='(/dev/sda,gpt2)'
	search --no-floppy --fs-uuid --set=root 293173a4-19a0-4fbd-9a83-d808ed2316eb
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=293173a4-19a0-4fbd-9a83-d808ed2316eb ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows 7" {
    search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
    chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=293173a4-19a0-4fbd-9a83-d808ed2316eb /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot/efi       vfat    defaults,noatime        0       1
# /home was on /dev/sda5 during installation
UUID=61fcf11a-5c26-4db8-b10b-9d3ad6d81ab7 /home           ext4    defaults,noatime,discard        0       2
# /usr was on /dev/sda3 during installation
UUID=069a90b5-f643-4254-8394-41057bac19b1 /usr            ext4    defaults,noatime,discard        0       2
# /usr/local was on /dev/sda4 during installation
UUID=893e5f8f-a176-4990-8e12-10fcf3e9aa4a /usr/local      ext4    defaults,noatime,discard        0       2
# /var was on /dev/sda6 during installation
UUID=b558501a-7dcf-412b-a079-20c6cfbe2439 /var            ext4    defaults,noatime,discard        0       2


tmpfs /tmp      tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/log  tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/tmp  tmpfs defaults,noatime,mode=1777 0 0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.589265347 = 0.632718848    boot/grub/grub.cfg                             1
   0.601411343 = 0.645760512    boot/initrd.img-2.6.38-10-generic              2
   0.483510494 = 0.519165440    boot/initrd.img-2.6.38-8-generic               2
   0.491899014 = 0.528172544    boot/vmlinuz-2.6.38-10-generic                 2
   0.473302364 = 0.508204544    boot/vmlinuz-2.6.38-8-generic                  1
   0.601411343 = 0.645760512    initrd.img                                     2
   0.483510494 = 0.519165440    initrd.img.old                                 2
   0.491899014 = 0.528172544    vmlinuz                                        2
   0.473302364 = 0.508204544    vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 a4 21 17 d2 4e  4f 20 4e 41 4d 45 20 20  |..).!..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error


---

### Post by pqwoerituytrueiwoq on 2011-08-11
if i read that right 
you have both OSes installed on there own drive
when you tell win7 to boot via grub it fails (i am assuming ubuntu boots)
MS is probably looking on the wrong ssd/hdd for it's boot loader

---

### Post by ClickHeRe on 2011-08-12
Xubuntu boots fine as it's the default path in the BIOS (Windows is the second) and it shows me the menu.

Yes both OSes are installed on separate drives.

Could it be that this code only searches the current drive where GRUB lives (/dev/sda) and I should change this to search (/dev/sdb) where Windows lives which I have no clue how to do?

menuentry "Windows x86_64 UEFI-GPT" {
search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

---

### Post by Ozymandias_117 on 2011-08-12
If this helps you at all, this is my menu entry for Windows 7. It looks like you're setting the root to a specific file which I assume is where the problem is.

```
menuentry "Windows 7 (on /dev/sdc2)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(hd2,msdos2)'
        search --no-floppy --fs-uuid --set=root 79CE3D955CA57BDA
        chainloader +1
}
```

The 79CE3D955CA57BDA is the UUID of the partition

---

### Post by YesWeCan on 2011-08-12
> **ClickHeRe said:**
> Xubuntu boots fine as it's the default path in the BIOS (Windows is the second) and it shows me the menu.

Yes both OSes are installed on separate drives.

Could it be that this code only searches the current drive where GRUB lives (/dev/sda) and I should change this to search (/dev/sdb) where Windows lives which I have no clue how to do?

menuentry "Windows x86_64 UEFI-GPT" {
search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

The  efi partition it wants is sdb1 I assume. Can you add a uuid for sdb1 to the search line?

---

### Post by ClickHeRe on 2011-08-12
> **Ozymandias_117 said:**
> If this helps you at all, this is my menu entry for Windows 7. It looks like you're setting the root to a specific file which I assume is where the problem is.

```
menuentry "Windows 7 (on /dev/sdc2)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(hd2,msdos2)'
        search --no-floppy --fs-uuid --set=root 79CE3D955CA57BDA
        chainloader +1
}
```

The 79CE3D955CA57BDA is the UUID of the partition


In your config, is msdos2 the windows fat boot partition like my /dev/sdb1 above or the WinMain one (/dev/sdb3)?

---

### Post by YesWeCan on 2011-08-12
I don't know much about UEFI but I have the impression is that it moves the OS selection menu to the bios so you don't need to select other OSs using the Grub menu. Is this impression wrong?

---

### Post by ClickHeRe on 2011-08-12
I have found more sources of information and I think I'll find the final solution with experimentation tonight

- Found how to go to the command line from the menu
- Found how to get GRUB to output debug information while trying stuff which should help for errors and seeing what the hell is going on
- Found information regarding windows boot and EFI mode

The simplistic command I tried above will not work for obvious reasons I found in GRUB documentation.

When I get the solution I'll document each command and the reason they are used.

---

### Post by Avidanborisov on 2011-08-12
> **ClickHeRe said:**
> I have found more sources of information and I think I'll find the final solution with experimentation tonight

- Found how to go to the command line from the menu
- Found how to get GRUB to output debug information while trying stuff which should help for errors and seeing what the hell is going on
- Found information regarding windows boot and EFI mode

The simplistic command I tried above will not work for obvious reasons I found in GRUB documentation.

When I get the solution I'll document each command and the reason they are used.

I also had problems with older version grub. You can use this to install the latest version: (It is a script I wrote, just follow the instructions the script gives)

```
wget http://my-shell-scripts.googlecode.com/files/compile_grub2_uefi.sh
chmod +x compile_grub2_uefi.sh
./compile_grub2_uefi.sh
```

Also, just a thought, you can put Windows boot loader as the second boot option in the firmware and create a menu entry in grub that exits grub. That way, windows bootloader will be loaded after grub exits.

---

### Post by srs5694 on 2011-08-12
First, the GRUB entry offered by Ozymondias_117 won't work; it's a BIOS GRUB entry, and Windows on a UEFI system boots in an entirely different way.

My suggestion for what to do is to install [rEFIt](http://refit.sourceforge.net/) and use it to select the OS to boot. An important caveat, though, is that the most common rEFIt binaries are mixed-mode 32-/64-bit binaries for Macs, and these don't seem to work on most UEFI PCs. Ubuntu has a refit package in its repositories that includes a pure 64-bit binary that works on every UEFI-based system on which I've tested (about four, including virtual machines). The procedure would be this:


[list=1]
[*]Boot into Ubuntu.
[*]Install the refit package ("sudo apt-get install refit" or use Synaptic or some other tool of your choice).
[*]Verify that your ESP is mounted at /boot/efi. It should have an efi or EFI subdirectory with an ubuntu subdirectory, so you should see /boot/efi/EFI/ubutu or /boot/efi/efi/ubuntu on your filesystem.
[*]Type "sudo cp -r /usr/lib64/refit/refit /boot/efi/EFI". This copies most of the rEFIt files to a new subdirectory (/boot/efi/EFI/refit) on the ESP.
[*]Type "sudo cp /usr/lib64/refit/x64/refit.efi /boot/efi/EFI/refit". This replaces the 32-/64-bit rEFIt binary with a pure 64-bit binary.
[*]Add rEFIt to your firmware's list of boot loaders. This can be done with tools in the firmware (consult your manual) or by using the efibootmgr program in Linux. I don't recall the precise syntax for the latter, though.
[*]Reboot and select rEFIt from the firmware's boot menu. You should see an option to boot Windows or Linux (although one or both may be mis-labelled). If the graphical display is messed up, you can edit the refit.conf configuration file on the ESP to uncomment the "textonly" line. This will switch from the graphical mode (which is often glitchy) to the text-only mode (which is less pretty but less likely to be glitchy).
[*]If rEFIt enabled you to select the OS, use your firmware or efibootmgr to make it the default boot loader.
[/list]

---

### Post by ClickHeRe on 2011-08-12
> **srs5694 said:**
> First, the GRUB entry offered by Ozymondias_117 won't work; it's a BIOS GRUB entry, and Windows on a UEFI system boots in an entirely different way.

My suggestion for what to do is to install [rEFIt](http://refit.sourceforge.net/) and use it to select the OS to boot. An important caveat, though, is that the most common rEFIt binaries are mixed-mode 32-/64-bit binaries for Macs, and these don't seem to work on most UEFI PCs. Ubuntu has a refit package in its repositories that includes a pure 64-bit binary that works on every UEFI-based system on which I've tested (about four, including virtual machines). The procedure would be this:


[list=1]
[*]Boot into Ubuntu.
[*]Install the refit package ("sudo apt-get install refit" or use Synaptic or some other tool of your choice).
[*]Verify that your ESP is mounted at /boot/efi. It should have an efi or EFI subdirectory with an ubuntu subdirectory, so you should see /boot/efi/EFI/ubutu or /boot/efi/efi/ubuntu on your filesystem.
[*]Type "sudo cp -r /usr/lib64/refit/refit /boot/efi/EFI". This copies most of the rEFIt files to a new subdirectory (/boot/efi/EFI/refit) on the ESP.
[*]Type "sudo cp /usr/lib64/refit/x64/refit.efi /boot/efi/EFI/refit". This replaces the 32-/64-bit rEFIt binary with a pure 64-bit binary.
[*]Add rEFIt to your firmware's list of boot loaders. This can be done with tools in the firmware (consult your manual) or by using the efibootmgr program in Linux. I don't recall the precise syntax for the latter, though.
[*]Reboot and select rEFIt from the firmware's boot menu. You should see an option to boot Windows or Linux (although one or both may be mis-labelled). If the graphical display is messed up, you can edit the refit.conf configuration file on the ESP to uncomment the "textonly" line. This will switch from the graphical mode (which is often glitchy) to the text-only mode (which is less pretty but less likely to be glitchy).
[*]If rEFIt enabled you to select the OS, use your firmware or efibootmgr to make it the default boot loader.
[/list]

Thanks for the reply and I saw this answer everywhere in similar issues. I do want to resolve this with GRUB as I'm pretty sure this is doable and I'm not ready to start installing other stuff just because no one understands the issue or can't figure it out (my nature and I'm in no rush to find this as I can still use the system)

I'm aware that the answer given is a BIOS mode menu entry.

Like I said before, I know have the tools to try this manually on the command line and see what's going on and will figure this out eventually.

I'll report my findings whether good or bad.

---

