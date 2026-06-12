---
title: "Grub 'Read Error' - AHCI Boot Issue"
date: 2012-09-01
forum: General Help
---

### Post by RyanSharp on 2012-09-01
I've had an issue for the past few weeks, that I've been desperately trying to solve.

I bought a brand new Samsung 64GB SSD, installed Windows 7. Easy peasy so far.
I then installed Ubuntu to run along side it, using my 1TB secondary HDD as /Home and Swap. Installed completely fine.

However, after rebooting after install, GRUB would not load, instead I receive the following error:
[HTML]Loading Operating Systems
Read Error[/HTML]
Though I have to admit, it's possible that it is in fact a Motherboard Read Error, and not from GRUB, but I can't be sure.

Anyway, if I go into BIOS and change the SATA mode to 'IDE', Grub loads fine, however doing so, no OS would boot afterwards. I also require AHCI for my SSD to have the performance boost that I was after when purchasing it.

A workaround I have to perform to boot, is to hit F12 to display alternative Booting options such as Disk, USB, etc, from my BIOS splash. Then I have to choose the CD option and the GRUB screen loads fine under AHCI perfectly fine. **It should be Noted that I don't even have any Disc in my CD-drive when I do this!**

After that, Windows loads up fine from Grub, but I have to load Ubuntu Recovery, and choose the "Boot up from first hard disk" option from their to boot up Ubuntu properly, otherwise choosing the regular Ubuntu option only gives a flashing "_" on a black screen.

I hope this is enough to explain the problem.

I'll now give you the BootInfoScript results:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid fd71c537-3715-44e1-b1fe-07537e22b3dd root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid fd71c537-3715-44e1-b1fe-07537e22b3dd root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sdb3 starts 
                       at sector 200744960. But according to the info from 
                       fdisk, sdb3 starts at sector 2048. According to the 
                       info in the boot sector, sdb3 has 823461887 sectors, 
                       but according to the info from fdisk, it has 
                       1024204799 sectors.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             208,896    48,957,439    48,748,544   7 NTFS / exFAT / HPFS
/dev/sda3          48,959,486   124,067,839    75,108,354   5 Extended
/dev/sda5    *     48,959,488   124,067,839    75,108,352  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1       1,024,208,894 1,953,523,711   929,314,818   5 Extended
/dev/sdb5       1,024,208,896 1,937,897,471   913,688,576  83 Linux
/dev/sdb6       1,937,899,520 1,953,523,711    15,624,192  82 Linux swap / Solaris
/dev/sdb3               2,048 1,024,206,847 1,024,204,800   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   625,141,759   625,139,712   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        A48056DF8056B80E                       ntfs       System Reserved
/dev/sda2        A8C6D6A4C6D671D4                       ntfs       Windows
/dev/sda5        fd71c537-3715-44e1-b1fe-07537e22b3dd   ext4       
/dev/sdb3        6373D03D0A3747A8                       ntfs       Steam
/dev/sdb5        6f5a6eb3-a932-45aa-893e-045b57708270   ext4       
/dev/sdb6        469848c8-867a-41b7-b0e1-b813a43c64af   swap       
/dev/sdc1        725D7B961CF34B1B                       ntfs       backup

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,noatime,nodiratime,discard,errors=remount-ro)
/dev/sdb5        /home                    ext4       (rw)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root fd71c537-3715-44e1-b1fe-07537e22b3dd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root fd71c537-3715-44e1-b1fe-07537e22b3dd
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
  insmod gettext
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root fd71c537-3715-44e1-b1fe-07537e22b3dd
	linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=fd71c537-3715-44e1-b1fe-07537e22b3dd ro   quiet splash acpi=off $vt_handoff
	initrd	/boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root fd71c537-3715-44e1-b1fe-07537e22b3dd
	echo	'Loading Linux 3.2.0-29-generic ...'
	linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=fd71c537-3715-44e1-b1fe-07537e22b3dd ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root fd71c537-3715-44e1-b1fe-07537e22b3dd
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root fd71c537-3715-44e1-b1fe-07537e22b3dd
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root A48056DF8056B80E
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root A8C6D6A4C6D671D4
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=fd71c537-3715-44e1-b1fe-07537e22b3dd /               ext4    noatime,nodiratime,discard,errors=remount-ro 0       1 
# /home was on /dev/sdb5 during installation
UUID=6f5a6eb3-a932-45aa-893e-045b57708270 /home           ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=469848c8-867a-41b7-b0e1-b813a43c64af none            swap    sw              0       0
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  48.112834930 = 51.660763136   boot/grub/core.img                             1
  35.496101379 = 38.113648640   boot/grub/grub.cfg                             1
  26.181640625 = 28.112322560   boot/initrd.img-3.2.0-29-generic               2
  35.479225159 = 38.095527936   boot/vmlinuz-3.2.0-29-generic                  1
  26.181640625 = 28.112322560   initrd.img                                     2
  35.479225159 = 38.095527936   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  63 6f 70 69 61 20 65 20  63 6f 6c 61 41 63 65 64  |copia e colaAced|
00000010  65 72 20 61 20 74 6f 64  6f 20 6f 20 74 65 78 74  |er a todo o text|
00000020  6f 20 66 61 6c 61 64 6f  20 75 74 69 6c 69 7a 61  |o falado utiliza|
00000030  6e 64 6f 20 61 20 63 6f  6e 76 65 72 73 c3 a3 6f  |ndo a convers..o|
00000040  20 64 65 20 74 65 78 74  6f 20 70 61 72 61 20 76  | de texto para v|
00000050  6f 7a 4d 61 6e 69 70 75  6c 61 72 20 61 73 20 64  |ozManipular as d|
00000060  65 66 69 6e 69 c3 a7 c3  b5 65 73 20 71 75 65 20  |efini....es que |
00000070  63 6f 6e 74 72 6f 6c 61  6d 20 6f 20 61 63 65 73  |controlam o aces|
00000080  73 6f 20 64 65 20 57 65  62 73 69 74 65 73 20 61  |so de Websites a|
00000090  20 63 6f 6f 6b 69 65 73  2c 20 4a 61 76 61 53 63  | cookies, JavaSc|
000000a0  72 69 70 74 20 65 20 70  6c 75 67 2d 69 6e 73 4d  |ript e plug-insM|
000000b0  61 6e 69 70 75 6c 61 72  20 61 73 20 64 65 66 69  |anipular as defi|
000000c0  6e 69 c3 a7 c3 b5 65 73  20 72 65 6c 61 63 69 6f  |ni....es relacio|
000000d0  6e 61 64 61 73 20 63 6f  6d 20 70 72 69 76 61 63  |nadas com privac|
000000e0  69 64 61 64 65 41 63 65  64 65 72 20 61 6f 73 20  |idadeAceder aos |
000000f0  73 65 75 73 20 70 65 72  69 66 c3 a9 72 69 63 6f  |seus perif..rico|
00000100  73 20 55 53 42 55 74 69  6c 69 7a 61 72 20 6f 20  |s USBUtilizar o |
00000110  73 65 75 20 6d 69 63 72  6f 66 6f 6e 65 55 74 69  |seu microfoneUti|
00000120  6c 69 7a 61 72 20 61 20  73 75 61 20 63 c3 a2 6d  |lizar a sua c..m|
00000130  61 72 61 55 74 69 6c 69  7a 61 72 20 6f 20 73 65  |araUtilizar o se|
00000140  75 20 6d 69 63 72 6f 66  6f 6e 65 20 65 20 61 20  |u microfone e a |
00000150  63 c3 a2 6d 61 72 61 4e  c3 a3 6f 20 66 6f 69 20  |c..maraN..o foi |
00000160  70 6f 73 73 c3 ad 76 65  6c 20 65 6e 63 6f 6e 74  |poss..vel encont|
00000170  72 61 72 20 6f 20 63 61  6d 69 6e 68 6f 20 61 62  |rar o caminho ab|
00000180  73 6f 6c 75 74 6f 20 70  61 72 61 20 6f 20 64 69  |soluto para o di|
00000190  72 65 63 74 c3 b3 72 69  6f 20 61 20 65 6d 70 61  |rect..rio a empa|
000001a0  63 6f 74 61 72 2e 4f 20  64 69 72 65 63 74 c3 b3  |cotar.O direct..|
000001b0  72 69 6f 20 64 65 20 65  6e 74 72 61 64 61 80 fe  |rio de entrada..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 10 7a 04 00 00  |............z...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt

```

I appreciate anybodies help.
I posted this on AskUbuntu, but received no responses whatsoever after a week. It's not the first time that happened, so I came here.
I've gotten to the point that I feel like bursting out in tears as I spent so much money on a device that I was expecting to allow me to perform my school work better and make my computing experience more pleasant. Instead, I can't do any work without spending enough time to boot the system and my experience has been complete crap as I've spent at least 20 hours trying to fix something I have no knowledge of.

Please, help me here before I tear my hair out.:(

---

### Post by oldfred on 2012-09-01
Some BIOS particularly Intel motherboards want to see the boot flag on a primary partition. That is a Windows requirement to boot. Grub does not use boot flag. 

You do have boot flag on sda5, but just move it back to sda1 where it should be for Windows anyway. If you were to ever reinstall the Windows boot loader the flag would have to be on sda1 for it to boot.

You can move flag with gparted, Disk Utility or command line.

set boot flag on for sda1 (off on others)
sudo sfdisk -A1 /dev/sda
parted /dev/sda set 1 boot on

---

### Post by RyanSharp on 2012-09-01
Thanks for taking the time to help me with this.
I very much appreciate it.

> **oldfred said:**
> Some BIOS particularly Intel motherboards want to see the boot flag on a primary partition. That is a Windows requirement to boot. Grub does not use boot flag. 

You do have boot flag on sda5, but just move it back to sda1 where it should be for Windows anyway. If you were to ever reinstall the Windows boot loader the flag would have to be on sda1 for it to boot.

You can move flag with gparted, Disk Utility or command line.

set boot flag on for sda1 (off on others)
sudo sfdisk -A1 /dev/sda
parted /dev/sda set 1 boot on

Okay, I did as you recommended.
I used GParted and set the Boot flag to SDA1, which is the partition set by Windows as some sort of System Reserved.
However, I'm still having the same problems. Read Error still occurs and still can only access Ubuntu through Recovery.

Anything else?

---

### Post by oldfred on 2012-09-01
When I added my SSD, I just converted to AHCI. But XP does not work with AHCI so I finally shutdown XP (unless I change BIOS back). 

But I understand Windows 7 needs a driver installed before you convert to AHCI, is this error from the Windows boot? It does not look like a grub error. Not sure if there are any other BIOS settings?

Are you booting from the SSD or sda. The grub's in the other MBRs look like they should work but have to change back to sda with config files.

---

### Post by RyanSharp on 2012-09-01
> **oldfred said:**
> When I added my SSD, I just converted to AHCI. But XP does not work with AHCI so I finally shutdown XP (unless I change BIOS back). 

But I understand Windows 7 needs a driver installed before you convert to AHCI, is this error from the Windows boot? It does not look like a grub error. Not sure if there are any other BIOS settings?

Are you booting from the SSD or sda. The grub's in the other MBRs look like they should work but have to change back to sda with config files.

Windows boots up fine once I get Grub booted fine by choosing the boot from CD option in the BIOS (without having any CD inserted).
Windows only hangs on boot up if I change the BIOS to use IDE again, probably because I installed Windows with AHCI enabled. Though this isn't my problem as AHCI is what I need to use anyway, so as such booting up Windows is fine as is, except from the problem of requiring the unusual process just to load GRUB to access Windows.
I don't reckon any other BIOS settings are involved. I can also confirm that my SSD is set to boot first.

SDA is the SSD. Both Windows and Ubuntu are installed on the SSD, I don't know why there are grubs on the other hard drives, as SDB is for /Home, Swap and Steam Games and SDC is just a backup drive.

---

### Post by oldfred on 2012-09-01
Is this a UEFI system? It may be that UEFI is turned on, cannot find the efi partition and reverts to BIOS mode (Which you are in)? Can you turn UEFI off if that is the case?

---

### Post by RyanSharp on 2012-09-01
> **oldfred said:**
> Is this a UEFI system? It may be that UEFI is turned on, cannot find the efi partition and reverts to BIOS mode (Which you are in)? Can you turn UEFI off if that is the case?

It is a UEFI Hybrid motherboard, but only uses it if you have a HDD that is over 2TB, so I always left that option disabled.

Also, I won't be able to do anything further as I believe that my Motherboard just broke my keyboard... >.>

I was just on Ubuntu, when I noticed that the backlight on my keyboard just turned off. It become unresponsive, I thought.
So a reboot later, I realized that the keyboard was broken. After trying it in several USB ports, I tried it in my laptop, and hey, it still doesn't work! I tried my mouse on the same USB port, and what do you know? My mouse stopped working also! Though that started working again after ten minutes, my Keyboard still doesn't.

Everything inside and outside my PC is less than a year old and I spent well over £1000, which to a seventeen year old like is a lot. I'm literally crying right now from frustration.

Just a question, but could the entire grub thing be anything to do with dodgy motherboard controllers? I hope the answer is yes, as I would at least be relieved that all I need to do is replace the motherboard and keyboard. Otherwise, I'll die inside knowing that my entire build is faulty in both hardware and software aspects.

Seriously, can things get any worse?

---

### Post by oldfred on 2012-09-01
You can use UEFI on any size drive. Many boot with small SSD and UEFI.

The requirement for over 2TiB is gpt is then required. And Windows only boots from gpt with UEFI. Otherwise it is totally optional. But error then seems like it is trying to find efi partition, cannot and then defaults to BIOS mode and looks in MBR and that works. But some UEFI do not have settings, most newer ones seem to have a setting on UEFI on or not.

Did you change settings in BIOS/UEFI? Most have a setting to enable USB keyboard & mouse. My keyboard would work in BIOS, not work in grub and then work in either Windows or Ubuntu. It was grub that used BIOS setting and everyone else has their own drivers that by-pass BIOS settings.

I have had mice & keyboard die more often than USB ports on motherboard.

---

### Post by RyanSharp on 2012-09-01
> **oldfred said:**
> You can use UEFI on any size drive. Many boot with small SSD and UEFI.

The requirement for over 2TiB is gpt is then required. And Windows only boots from gpt with UEFI. Otherwise it is totally optional. But error then seems like it is trying to find efi partition, cannot and then defaults to BIOS mode and looks in MBR and that works. But some UEFI do not have settings, most newer ones seem to have a setting on UEFI on or not.

Did you change settings in BIOS/UEFI? Most have a setting to enable USB keyboard & mouse. My keyboard would work in BIOS, not work in grub and then work in either Windows or Ubuntu. It was grub that used BIOS setting and everyone else has their own drivers that by-pass BIOS settings.

I have had mice & keyboard die more often than USB ports on motherboard.

My motherboard is a hybrid BIOS UEFI, but the setting in it was set to 'auto' I just discovered, and not disabled that I previously believed. I'll experiment with that tomorrow. 

I didn't change anything in BIOS regarding USB. The problem occurred with the keyboard while I was in the middle of surfing the web on Ubuntu, so there was about half an hour of time where it was working fine. Also, trying it in my laptop shows that it no longer works. And also the usb ports no longer function properly after it happened. I got the keyboard fr Christmas and it wasn't a cheap one either. 
If I connect my Cyborg RAT mouse, the LED blinks and it shuts down as if it is broken similarly to the keyboard when it first happened, on any USB, but fortunately still works in my laptop, whereas the keyboard doesn't. Also the keyboard doesn't light up at all since it first happened. 
Anyway, that is an issue for a different forum I believe. Sorry.

---

### Post by RyanSharp on 2012-09-02
So I just finished testing the EFI boot options, and they made no difference whatsoever. I still can't boot to GRUB without using the CD option, and I can't yet Boot into Ubuntu from GRUB without going through recovery option.

Also, the mouse is working again on my system, but the keyboard is still useless. I checked BIOS and there was no option about USB other than using it as a booting option or to use whatever is connected by USB to turn the PC on.

Anyway, any ideas about what I can do to fix my OS'? I'd like to solve it before I troubleshoot the keyboard thing elsewhere.

---

### Post by oldfred on 2012-09-02
This runs the same bootinfoscript but adds some info and will help in reinstalling grub2's boot loader to see if that makes any difference.

Run BootInfo to see latest changes and post the link to pastebin it creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by RyanSharp on 2012-09-02
Here is the result:
[http://paste.ubuntu.com/1182050/](http://paste.ubuntu.com/1182050/)

I'll reboot now to see if anything has changed.

EDIT: No change whatsoever from the 'Recommended Repair' option, unfortunately.

---

### Post by oldfred on 2012-09-02
Boot script looks normal to me. I do not see anything obvious, maybe someone else will.

I still think error is from BIOS and grub has no control over that.

---

### Post by RyanSharp on 2012-09-02
Okay, so I trawled through the BIOS settings, and changed one thing that caught my eye... booted up and GRUB loaded fine! >.>

The option was titled "Onboard Serial Port 1" and had the default setting of "3F8/IRQ4", which when I selected, shown various similar settings, plus an "auto". I selected auto, saved, rebooted, and wham, it works!

Please help me make sense of what happened here, and why the default setting halted my boot up.

Also, I still have the problem of Ubuntu not starting without going through Recovery. If I boot Ubuntu as you would, I get an Aubergine screen and nothing more. Any help here? 
I thought it may be a graphics problem, but I have the driver installed.

---

### Post by oldfred on 2012-09-02
In the old days irq's were assigned to certain devices, then there were too many devices for the amount of irq's so they somehow were shared. Perhaps some cannot be? I know irq conflicts were a big issue many years ago, but not recently.

Recovery mode bypasses quiet splash and usually loads nomodeset. Use e on grub menu to see settings on linux line. If nomodeset is working then video driver may be installed but not configured?

What video card/chip is it?

---

### Post by RyanSharp on 2012-09-02
Ro Quiet splash acpi=off $vt_handoff
Is what I get after the Linux line

My GPU is AMD HD Radeon 6850.

---

### Post by oldfred on 2012-09-02
Was the acpi=off to get around the IRQ issue?

I do not know AMD as I have nVidia.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Some have used the redeon settings and some the generic to make systems work. 
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by RyanSharp on 2012-09-02
Hmm... I removed ACPI=off and it booted fine.
I didn't include that personally, so I'm assuming it was included by Boot-repair. Anyway, seems everything is fine now. I just need to edit the Grub config to boot as such from now on.

I'll set this thread to solved tomorrow if everything is still okay.

Before that, can you explain what ACPI is and why it was disabled, or why I should keep it enabled?

Thanks for the help.
I'm absolutely relieved that the big worries have gone.
After this, all I need to do is find that warranty for my keyboard. >.>

---

### Post by oldfred on 2012-09-02
I do not know a lot about ACPI. It has to do with power savings. And is or was not well supported in Linux drivers. My BIOS has some settings on ACPI but I have not changed whatever that default is. And I do not have to change settings in Ubuntu with my system, 6 year  old core duo.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

---

### Post by RyanSharp on 2012-09-03
I can confirm that this has been fixed.

I owe you a lot here, seriously.

---

