---
title: "Partition Problem"
date: 2011-06-29
forum: General Help
---

### Post by calebi on 2011-06-29
Okay so I had switched over from Windows to Ubuntu and got rid of windows completely but still had the recovery partition and deleted it. I then tried to add that space to another partition, "Media." For whatever reason it deleted the "Media" partition so I used TestDisk to restore it. I did something wrong and when I rebooted my computer it would not boot so I used my LiveCD to check whats wrong and it had deleted all of my partitions and Ubuntu was nowhere to be found. So I used TestDisk again to recover them, this time it was successful. The problem now however is that when I start my computer it does not boot into Ubuntu it just shows a black screen with the white underscore ("_") flashing in the corner. I'm not sure but I don't think it is booting into the correct partition, I think it would be trying to boot the first partition, /dev/sda1, rather than /dev/sda3. If this is the problem how could I fix it?

Thanks,
Caleb

---

### Post by Ozymandias_117 on 2011-06-29
Boot to a livecd, then mount your root drive and post the contents of your /etc/fstab file also, try to reinstall grub2. Usually I'd provide a link, but I'm on my phone.

---

### Post by coffeecat on 2011-06-29
Boot up with a live CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script according to the instructions there. The RESULTS.txt file will contain comprehensive information about your system including the /etc/fstab file. Post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for legibility. You can use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] icon in the message toolbar for this.

Hopefully, we'll be able to see what is wrong from the output of the boot script.

---

### Post by calebi on 2011-06-29
Here it is:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 7716 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048    30,617,592    30,615,545 Data partition (Windows/Linux)
/dev/sda2      30,617,600   481,177,599   450,560,000 Data partition (Windows/Linux)
/dev/sda3     481,179,648   934,991,871   453,812,224 EFI System partition
/dev/sda4     934,993,920   958,337,007    23,343,088 Swap partition (Linux)
/dev/sda5     958,339,072   976,771,055    18,431,984 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1010 MB, 1010826752 bytes
32 heads, 61 sectors/track, 1011 cylinders, total 1974271 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             61     1,973,471     1,973,411   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        DC1E32251E31F95A                       ntfs       BIOS_RVY
/dev/sda2        6faa6680-a157-4c1c-aaba-9423829e1d1e   ext4       Media
/dev/sda3        aeeb2ad3-b056-4369-b38c-b14b9226f7f7   ext4       /
/dev/sda4        5647e392-ac60-4685-b650-bbb9d76490b6   swap       
/dev/sda5        c5049d52-bcf7-49a0-a39c-d4ba606307dd   swap       
/dev/sdb1        1016-273B                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root aeeb2ad3-b056-4369-b38c-b14b9226f7f7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root aeeb2ad3-b056-4369-b38c-b14b9226f7f7
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root aeeb2ad3-b056-4369-b38c-b14b9226f7f7
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=aeeb2ad3-b056-4369-b38c-b14b9226f7f7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root aeeb2ad3-b056-4369-b38c-b14b9226f7f7
    echo    'Loading Linux 2.6.38-8-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=aeeb2ad3-b056-4369-b38c-b14b9226f7f7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root aeeb2ad3-b056-4369-b38c-b14b9226f7f7
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=aeeb2ad3-b056-4369-b38c-b14b9226f7f7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root aeeb2ad3-b056-4369-b38c-b14b9226f7f7
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=aeeb2ad3-b056-4369-b38c-b14b9226f7f7 ro single 
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root aeeb2ad3-b056-4369-b38c-b14b9226f7f7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root aeeb2ad3-b056-4369-b38c-b14b9226f7f7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root DC1E32251E31F95A
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
# / was on /dev/sda6 during installation
UUID=aeeb2ad3-b056-4369-b38c-b14b9226f7f7 /               ext4    errors=remount-ro 0       1
# /media/BIOS_RVY was on /dev/sda1 during installation
UUID=DC1E32251E31F95A /media/BIOS_RVY ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=5647e392-ac60-4685-b650-bbb9d76490b6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 319.576332092 = 343.142473728  boot/grub/core.img                             1
 281.702598572 = 302.475862016  boot/grub/grub.cfg                             1
 235.877960205 = 253.272031232  boot/initrd.img-2.6.35-28-generic              1
 266.959960938 = 286.646075392  boot/initrd.img-2.6.38-8-generic-pae           2
 321.497882843 = 345.205723136  boot/vmlinuz-2.6.35-28-generic                 1
 279.944763184 = 300.588400640  boot/vmlinuz-2.6.38-8-generic-pae              2
 266.959960938 = 286.646075392  initrd.img                                     2
 279.944763184 = 300.588400640  vmlinuz                                        2

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 



```

---

### Post by coffeecat on 2011-06-29
Your boot script output is quite unexpected.

Unless I've missed something, grub.cfg and /etc/fstab look OK but the reason why grub is not booting is because core.img is missing. Normally, one would advise simply re-installing grub from the live CD, but I think this would be inadvisable because of other matters that the boot script is reporting.

It says you have a GUID partition table and that your Ubuntu root partition, sda3, is the EFI system partition. You also have two swap partitions, only one of which is referenced in /etc/fstab. I suspect that testdisk may have miswritten the partition table, since this drive was originally used for Windows. Windows can boot from a GPT drive, but not with a conventional BIOS. Or if this really is a GPT drive, then we need to take care. That EFI partition = sda3 looks just wrong to me.

I suggest you do nothing at the moment. This requires a more expert look. I'll pm someone who will be able to give an expert opinion.

In the meantime, does the machine have a conventional BIOS or EFI firmware?

---

### Post by calebi on 2011-06-29
I'm not sure how to find out if it's EFI Firmware or BIOS. I've been looking online but nothing seems very clear.

---

### Post by coffeecat on 2011-06-29
What's the make and model of the computer? Or, if home-built, make and model of motherboard? Unless very new, it's likely to have a standard BIOS, but it would be worth checking anyway.

---

### Post by oldfred on 2011-06-29
If it was gpt then you would need a bios_grub partition for grub's core.img. If using BIOS. Or a separate efi partition if UEFI (not the one you have with system data).

But when you installed Ubuntu it was MBR(msdos).

set root='(/dev/sda,[COLOR=Red]msdos[/COLOR]6)'

I now prefer gpt if not using windows, but it actual only has minor advantages over msdos partitions.
GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

You can use fixparts to remove gpt data.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
or use gdisk:
Remove old parts of gpt
[http://ubuntuforums.org/showpost.php?p=10022223&postcount=34](http://ubuntuforums.org/showpost.php?p=10022223&postcount=34)

If never installing windows you could stay with gpt. Not sure what clean up may be required. But I would run gdisk and see what it says. 
GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)


At the minimum you will have to reinstall grub to the MBR whatever you do.

---

### Post by srs5694 on 2011-06-29
I believe coffeecat is correct. I've used TestDisk before, but I'm not intimately familiar with it. My recollection is that it asks you about your partition table type at one point, so if you responded "GPT," it might have restored your partitions using GPT rather than MBR, effectively converting your disk from MBR to GPT. This will prevent the computer from booting because you need to re-install GRUB after such a conversion.

Incidentally, my suspicion is that your second use of TestDisk was unnecessary and is what caused the problem. TestDisk has a known bug that causes GParted and related partitioning tools to incorrectly report that a disk is empty when in fact it isn't. This can be repaired with my [FixParts](http://www.rodsbooks.com/fixparts/) program. Not that this information does you any good right now, but mentioning it might keep you or somebody else from making the same mistake in the future....

The partition type issues are probably due to TestDisk guessing wrong about that detail. (TestDisk has to guess about partition type codes, since that's part of the information that's lost when a partition table is damaged or destroyed.)

The best course of action depends on what you plan to do with the computer. It sounds like you don't want to go back to Windows, so that makes consolidation of your GPT setup the best thing, IMHO. To do that, follow these steps:


[list=1]
[*]Download and prepare a copy of [Super GRUB 2 Disc.](http://www.supergrubdisk.org)
[*]Boot with a recovery disc, such as the Ubuntu install disc in "live CD" mode.
[*]If necessary (it will be with the Ubuntu disc), install the gptfdisk or gdisk package. You can do this by typing "sudo apt-get install gdisk". (You can read the full gdisk documentation [here.](http://www.rodsbooks.com/gdisk/)) Alternatively, download the latest version using links [here.](http://www.rodsbooks.com/gdisk/download.html#obs)
[*]Type "sudo gdisk /dev/sda" to launch gdisk on the disk.
[*]Type "p" to view the partition table. Verify that all your partitions are present. If not, type "q" to exit and try again with another device or post back with details.
[*]Type "v" to verify the partition table to be sure there aren't any problems. If there are, post back with details. (This is just a precaution; I suspect it's OK.)
[*]Type "t" to change a partition's type code. Enter "3" to change partition 3's type code and type "0700" as the code. (Note that a new code, "8300", has been introduced for Linux filesystems with gdisk 0.7.2, so if you use the latest gdisk you might as well use "8300"; but on a Linux-only system, the old "0700" code will work just as well.)
[*]Type "n" to create a new partition. Select the default start and end points (this will probably create a ~1 MiB partition at the end of the disk) and give it a type code of "EF02". This will create a BIOS Boot Partition for the disk, which will be helpful (possibly necessary) for re-installing GRUB.
[*]Reboot using Super GRUB 2 Disk. You should be able to use one of its menu options to locate and boot into your Linux system in a normal fashion. You might need to try a few options before you find one that works, though.
[*]Once you're into your normal installation, open a Terminal window and type "sudo grub-install /dev/sda". That should re-install GRUB.
[*]To test your new system, remove the Super GRUB Disk and reboot. With any luck, the computer will boot normally.
[*]At this point, you can put a new filesystem on your /dev/sda1 partition or delete it and resize your partitions in whatever way you see fit.
[*]You might also consider deleting /dev/sda5, since it's not referenced in /etc/fstab, and increase the size of /dev/sda4 or move it to the end of the available space. This is optional "housecleaning," though.
[/list]


There's a chance that you won't be able to get Super GRUB 2 Disk to boot your installation. If that happens, you can re-install GRUB using the Ubuntu install disc. I don't recall the exact details of that procedure offhand, but there are several threads and Web sites that describe it, so try a Web search or post back here and somebody who recalls the exact procedure will be able to help.

The alternative to this whole procedure is to convert back from GPT format to MBR format. This is possible using gdisk, but it won't be any easier; the new GPT data on your disk have wiped out your second-stage boot loader code, so you'll need to re-install GRUB either way you do it, and converting from GPT to MBR is no easier than changing the type code on /dev/sda3 and creating a BIOS Boot Partition. The only advantage of a GPT-to-MBR conversion is that you'll be able to boot Windows on the computer. (Windows can't boot from GPT on a BIOS-based computer.)

---

### Post by srs5694 on 2011-06-29
The computer is almost certainly BIOS-based, not UEFI-based. The fact that there's boot loader code in the MBR, the "msdos" references in the GRUB configuration, the fact that there's no legitimate EFI System Partition (ESP) on the disk, and the gaps between all but the first two partitions all point to the computer being BIOS-based. None of these makes for a 100% certainty on this score, but they add up to about 99% certainty.

FixParts will be useless on the disk as it exists now, since the disk ***is*** a GPT disk; FixParts is useful in removing *old* GPT data from an MBR disk, not in converting a GPT disk back to MBR form. In fact, if you were to try FixParts on the disk, it should just complain that the disk is a GPT disk and then exit without doing anything else.

---

### Post by calebi on 2011-06-29
> **coffeecat said:**
> What's the make and model of the computer? Or, if home-built, make and model of motherboard? Unless very new, it's likely to have a standard BIOS, but it would be worth checking anyway.

It is an MSI A6200, it has an Intel Core i3-350M processor.

---

### Post by coffeecat on 2011-06-29
srs5694's analysis is that your machine is BIOS-based. I couldn't find anything on MSI's website, but what I could find on a Google search confirms that it is BIOS-based, so it must have had an MBR partitition table originally.

---

