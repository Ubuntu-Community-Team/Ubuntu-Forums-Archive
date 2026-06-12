---
title: "Major (for me) Dual Booting Problems"
date: 2011-09-14
forum: General Help
---

### Post by sublimnalxx on 2011-09-14
My computer came with pre-installed Vista OS and I thought it would be a good idea to install Ubuntu into it ( I have yet to see any good come from this :(). 

The way I have it set up is I've got (2) hard drives; (1) 750GB Seagate HD, and (1) 160GB Western Digital HD. The Vista runs off of the Seagate and Ubuntu from The Western Digital. During Ubuntu installation i chose to install side by side, I didn't enter any settings manually or anything like that. After Installation I saw that i had the option to run Vista or Ubuntu. The Ubuntu option worked fine, but the Vista option takes me to a black screen with a white cursor at the top left corner blinking indefinitely.

Note: I'm able to use Ubuntu.

If anyone would be so kind as to give me a hand here, it would be greatly appreciated. I want this nightmare to end already! I just wanted to enjoy Ubuntu. (Clean Vista Install is not an option) Thank you in advance.

---

### Post by oldfred on 2011-09-15
Welcome to the forums.

If you installed to a separate drive, you should have no issues if you cleanly installed the entire system and the grub2 boot loader to the MBR of the second drive.

To see what is where.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by garvinrick4 on 2011-09-15
Do you need help running the boot_info_script.sh ? Will be easy to diagnose your problem
and get you running properly if you could run it and post it to this thread, if you need help
just hollar?

---

### Post by sublimnalxx on 2011-09-15
Well, the way I explained I have it installed is the way I installed it right before I came to post. I've been trying to fix it by reading about the issue other people were having and have been trying so for the last 3 days, but I guess I ended up mixing things up. Looking back now, I must have installed / re-installed Ubuntu at least 6 more times, sometimes reformatting the drive, and sometimes putting the boot file in my Windows HD, etc. Anyway, here are the results:

```

                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/nvidia_cbecdiba and 
    looks at sector 1 of the same hard drive for core.img. core.img is at this 
    location and looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

nvidia_cbecdiba1: ______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /wubildr /ubuntu/winboot/wubildr 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

nvidia_cbecdiba1/Wubi: _________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: unknown filesystem type ''

nvidia_cbecdiba2: ______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63 1,441,207,214 1,441,207,152   7 NTFS / exFAT / HPFS
/dev/sda2       1,441,207,215 1,465,144,064    23,936,850   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   304,193,535   304,191,488  83 Linux
/dev/sdb2         304,195,582   312,580,095     8,384,514   5 Extended
/dev/sdb5         304,195,584   312,580,095     8,384,512  82 Linux swap / Solaris


Drive: nvidia_cbecdiba _____________________________________________________________________

Disk /dev/mapper/nvidia_cbecdiba: 750.2 GB, 750156316672 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/nvidia_cbecdiba1   *             63 1,441,207,214 1,441,207,152   7 NTFS / exFAT / HPFS
/dev/mapper/nvidia_cbecdiba2      1,441,207,215 1,465,144,064    23,936,850   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        BEE40923E408E00F                       ntfs       HP
/dev/sda2        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE
/dev/sdb1        e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b   ext4       
/dev/sdb5        f1349434-9d94-4a4a-afe9-34d15f143fdf   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b
    linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b
    echo    'Loading Linux 2.6.38-11-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  96.135013580 = 103.224184832  boot/grub/core.img                             1
 142.133003235 = 152.614150144  boot/grub/grub.cfg                             1
   1.134212494 = 1.217851392    boot/initrd.img-2.6.38-11-generic-pae          2
   0.860782623 = 0.924258304    boot/vmlinuz-2.6.38-11-generic-pae             2
   1.134212494 = 1.217851392    initrd.img                                     2
   0.860782623 = 0.924258304    vmlinuz                                        2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 7f 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on nvidia_cbecdiba1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

ERROR: sil: invalid metadata checksum in area 1 on /dev/sda
ERROR: sil: invalid metadata checksum in area 1 on /dev/sda
ERROR: sil: invalid metadata checksum in area 1 on /dev/sda
ERROR: sil: invalid metadata checksum in area 1 on /dev/sda
unlzma: Decoder error
unlzma: Decoder error
ERROR: sil: invalid metadata checksum in area 1 on /dev/sda

```

---

### Post by YesWeCan on 2011-09-15
Hi and welcome. You appear to be suffering from a couple of things, one is the Ubuntu installer that has put the Grub boot code on the wrong disk and your Windows disk that looks like it was once used for a RAID. Ubuntu is detecting RAID signatures and this is confusing matters. You also have some Wubi files, but these probably dont matter.

First, I'd install Grub to the 160GB drive MBR
Boot into Ubuntu
sudo grub-install /dev/sdb

Then restore a normal MBR to the Windows drive
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

You may now be able to boot Windows again when the bios is set to boot the 750GB drive first. When you set the BIOS to boot the 160GB drive Ubuntu should boot.

To add Windows to the Ubuntu boot menu the RAID needs to be disabled. In this case I think I would be inclined to disable it in Ubuntu. Boot Ubuntu and run
sudo apt-get remove dmraid
sudo update-grub
and note whether the output lists Windows. If it does try rebooting and selecting Wndows.

If things still aren't right please post a fresh bootinfoscript results.

---

### Post by sublimnalxx on 2011-09-15
Hi YesWeCan

I followed your instructions up to the point where I add Windows to Ubuntu menu.
After entering: 
sudo lilo -M /dev/sda mbr
I proceeded to check if Vista booted by selecting the 750gb drive to boot first as you had said.

However, upon selecting it I seemed to be taken to the Windows boot menu which presented me with 2 options:

Windows Vista

Ubuntu

Let me give you a little background information about this as well. Before installing Ubuntu I did a bit of reading and installed some program (I forgot the name but it's very popular) that allowed me to make an entry into the Vista boot menu that would allow me to select Ubuntu from Windows(since I didn't expect Ubuntu to take over the booting with Grub). And when I tried it, the Ubuntu option showed up but didn't work since it wasn't installed yet, but the Vista option worked perfectly.

When I select Vista I get the following message:

```
[CENTER]Windows Boot Manager
[LEFT]Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:
[/LEFT]
[/CENTER]

1. Insert your windows installation disc and restart your computer.
2. Choose your language settings, and then click "next."
3. Click "repair your computer."

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

[CENTER]File: \Windows\system32\winload.exe
Status: 0xc000000e
Info: The selected entry could not be loaded because the application is missing or corrupt.[/CENTER]

```When I select the Ubuntu option, I'm presented with the same menu except the "File' entry says 
"File: \NST\AutoNeoGrub0.mbr"

Sorry that I'm not able to respond quickly, I'm usually on my computer all day evenings (-8 PST)

---

### Post by YesWeCan on 2011-09-15
I think the problem may be that there is a /boot/grub folder in your Vista C:
The bootinfoscript output is being obfuscated by the dmraid and doesn't show the partition contents but the Grub in MBR sda (which is no longer there) references it.

Would you boot the 160GB drive into Ubuntu. If you haven't already done it remove dmraid
[COLOR=DarkSlateBlue]sudo apt-get remove dmraid[/COLOR]

Then run bootinfoscript and post the results. This should show whether there are two folders BOOT and boot in the Vista drive partition #1. The boot folder needs to be deleted, Vista does not distinguish between upper and lower case and gets confused and won't boot.


Have a look at the RESULTS.txt. The Vista disk *may* be called sdb now and the first partition sdb1. It should also say Lilo in the MBR of sdb. Use whichever the correct drive name is.
Look at whether the boot files list contains both BOOT/... and boot/grub. If it does then mount the partition and delete boot/grub. You must not accidentally delete BOOT.
[COLOR=DarkSlateBlue]sudo mount /dev/sdb1 /mnt
ls /mnt
sudo rm -r /mnt/boot[/COLOR]
Then try booting the Vista disk again.

---

### Post by sublimnalxx on 2011-09-15
Here's what I did. I continued with your instructions from the other post, disabling raid, updating grub and then followed with the instructions you just gave me up to the bootinfoscript. Here are the results:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /wubildr /ubuntu/winboot/wubildr 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda1/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63 1,441,207,214 1,441,207,152   7 NTFS / exFAT / HPFS
/dev/sda2       1,441,207,215 1,465,144,064    23,936,850   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   304,193,535   304,191,488  83 Linux
/dev/sdb2         304,195,582   312,580,095     8,384,514   5 Extended
/dev/sdb5         304,195,584   312,580,095     8,384,512  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        BEE40923E408E00F                       ntfs       HP
/dev/sda2        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE
/dev/sdb1        e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b   ext4       
/dev/sdb5        f1349434-9d94-4a4a-afe9-34d15f143fdf   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b
    linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b
    echo    'Loading Linux 2.6.38-11-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root BEE40923E408E00F
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 949CA48C9CA46A86
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=e1367a67-3d6f-4dcd-bfbf-d44ef2c7fc8b /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  96.126991272 = 103.215570944  boot/grub/core.img                             1
  48.128108978 = 51.677163520   boot/grub/grub.cfg                             1
   1.086914062 = 1.167065088    boot/initrd.img-2.6.38-11-generic-pae          2
   0.860782623 = 0.924258304    boot/vmlinuz-2.6.38-11-generic-pae             2
   1.086914062 = 1.167065088    initrd.img                                     2
   0.860782623 = 0.924258304    vmlinuz                                        2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

Unknown BootLoader on sdb2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 7f 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

I forgot to mention that after I added Windows to my Ubuntu Boot Menu, it actually added 2 Windows Vista loaders. The two partitions on the 750gb drive are able to boot (I'm not sure if you already know this from reading the RESULTS.txt or not, but just letting you know) and the first partition from the menu takes me to the same place as if I were to boot the 750gb drive from the beginning. The second option takes me to a Vista Recovery mode of some sort where I'm guessing that I'm able to run a "Startup Repair". I'll take note of this as the easy way out, in the event that no one is able to help me out of this hole i dug myself into.

---

### Post by oldfred on 2011-09-16
Can you mount sda1 and do you have the Windows partitions - /windows & /windows/System32?
Vista/7 boot files
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

You show bootmgr & the BCD but no winload which is the error you are getting. You do have an install of wubi in sda1, but that should be just files inside your windows install.

The vendor recovery often just wipes drive and reimages drive to as purchased. It is not an install disk, but just an image. Be sure to back up anything you want first.

---

### Post by sublimnalxx on 2011-09-16
> **oldfred said:**
> Can you mount sda1 and do you have the Windows partitions - /windows & /windows/System32?
Vista/7 boot files
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

You show bootmgr & the BCD but no winload which is the error you are getting. You do have an install of wubi in sda1, but that should be just files inside your windows install.

The vendor recovery often just wipes drive and reimages drive to as purchased. It is not an install disk, but just an image. Be sure to back up anything you want first.

I'm able to mount both partitions sda1 and sda2.

Is there some way I can just download a copy of winload.exe, and navigate from Ubuntu through sda and place it where it belongs? Or is winload.exe unique to my computer? I really don't want to reimage my drive, that's the very last option. My personal files are scattered everywhere in that drive.

---

### Post by YesWeCan on 2011-09-16
So there is no boot/grub (I thought there might be based on the first bootinfoscript output) and Vista uses Boot not BOOT (where did I get BOOT from...XP?).

Windows.exe will be in sda2 (the recovery partition) but it may be inside some compressed file. I suppose if you have another disk you could copy sda1 to it, then run the recovery partition to restore the whole sda then copy the Windows.exe to the sda1 copy on the other disk then try to boot it. Sort of convoluted and fiddly but might work, might not. It is useful to make a copy anyhow if you have a big enough disk available.

---

### Post by oldfred on 2011-09-16
If you can mount the drive I would be sure to back up everything of importance if you have not yet.

If you can get to a recovery console make the windows repairCD. But I do not think the repair replaces winload.exe. It can update the BCD or replace bootmgr if missing.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by YesWeCan on 2011-09-16
> **oldfred said:**
> If you can get to a recovery console make the windows repairCD. But I do not think the repair replaces winload.exe. It can update the BCD or replace bootmgr if missing.
I'm not certain what sort of recovery partition this is. What do you think? Presumably if it is a "restore disk to factory defaults" there has to be a complete Vista in it, perhaps compressed image file.

---

### Post by oldfred on 2011-09-16
It is very confusing. There seem to be two recoveries. 

The vendor recovery is just the image of the hard drive. It will not do repairs and in fact those who start it by mistake and stop it midway, damage their system.  Many also let you write DVDs to make a copy which seems like a good idea as if drive fails how can you use recovery on drive. 
But full image backup may be better, since the image as purchased still has all the temporary test software & needs major updates to be current.

The Microsoft Windows recovery is tiny and is just the repair part of windows. It can be on a CD or USB flash drive. I installed one to a flash drive and it was only about 200-300MB.

---

### Post by sublimnalxx on 2011-09-17
I just navigated through my system32 folder and the Winload.exe is right there. I'm guessing there's something wrong with my MBR or something. I've downloaded a Windows Vista Recovery CD, and tried to run the commands to rebuild it, but it firsts asks to select the Operating system, and my Windows Vista doesn't come out. It also says that if my OS doesnt come up to load the drivers for my hard drives. thing is, I can't get them loaded cause it doesn't detect CD Drive, or anything that connects through the USB ports.

---

### Post by oldfred on 2011-09-17
It seems both the boot script and windows itself cannot find it. Did the folder get moved? Back in my early Windows days I often click & dragged a folder to an incorrect place under another folder.

This has to be the folder(s)/path:
/Windows/System32/winload.exe

---

### Post by sublimnalxx on 2011-09-17
That's correct, it's in Windows/System32.

---

### Post by oldfred on 2011-09-18
Do you have a windows repairCD or know anyone with a working windows 7. If so I would run chkdsk on the windows partitions.


Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

Anything beyond that and you may find better help with Windows issues in a Windows forum.
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)

---

