---
title: "Windows XP Won't Boot From Grub Menu"
date: 2011-06-28
forum: General Help
---

### Post by JBA2337 on 2011-06-28
I have my computer set up for dual boot, Ubuntu 11.04 or Windows XP SP3. When I started up the computer it opens the Grub boot menu as it should. On the Grub menu if I select Ubuntu, it starts up Ubuntu as it should. However if I select Windows XP on the Grub boot menu it does not start Windows XP. Nothing happens. After selecting Windows XP it returns to the the Grub boot menu. It seems to be stuck in a loop.

I thought that Grub was corrupted, so I reinstalled it from the Super Grub Disk. The reinstallation of Grub went smoothly, with no errors. Even after I reinstalled Grub, I still have the same problem described above.

I am stuck on the Grub boot menu, and I can't get Windows XP to boot.

Does anyone have any ideas how to fix this?
   
JBA2337

---

### Post by oldfred on 2011-06-29
Post this so we can see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by JBA2337 on 2011-06-30
Here is the RESULTS.txt file from boot_info_script.sh:



```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 109492076 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    97,193,249    97,193,187   7 NTFS / exFAT / HPFS
/dev/sda2          97,193,311   195,366,464    98,173,154   f W95 Extended (LBA)
/dev/sda5          97,193,313    99,297,764     2,104,452  82 Linux swap / Solaris
/dev/sda6          99,297,828   195,366,464    96,068,637  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        FEC485C5C485811F                       ntfs       TDiskCntfs
/dev/sda5                                               swap       
/dev/sda6        4b660084-c46d-4861-8992-fa814e6a8167   ext3       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[Boot Loader]

Timeout=5

Default=C:\$WIN_NT$.~BT\BOOTSECT.DAT

[Operating Systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /fastdetect /NoExecute=OptIn

## (enables Data Execution Prevention for the

## operating system and all processes except those specified 

## in the DEP configuration dialog (System in Control Panel))



##

## (enables Data Execution Prevention for the 

## operating system and all processes. This includes the Windows

## kernel and drivers)

C:\$WIN_NT$.~BT\BOOTSECT.DAT="Microsoft Windows XP Professional Setup"

--------------------------------------------------------------------------------

=========================== sda6/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set=root 4b660084-c46d-4861-8992-fa814e6a8167
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 4b660084-c46d-4861-8992-fa814e6a8167
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
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4b660084-c46d-4861-8992-fa814e6a8167
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=4b660084-c46d-4861-8992-fa814e6a8167 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4b660084-c46d-4861-8992-fa814e6a8167
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=4b660084-c46d-4861-8992-fa814e6a8167 ro single 
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
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4b660084-c46d-4861-8992-fa814e6a8167
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 4b660084-c46d-4861-8992-fa814e6a8167
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root FEC485C5C485811F
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

=============================== sda6/etc/fstab: ================================

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
UUID=4b660084-c46d-4861-8992-fa814e6a8167 /               ext3    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

#  /dev/sr0  /media/cdrom  auto  defaults,noauto,users,ro,nohide  0 0
#  /dev/sr0 /media/cdrom auto ro,noauto,user,exec 0 0
# none of the above lines succeded in adding a cdrom to devices
# I never could figure out how to add a cdrom to the software sources 6/26/11

--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  52.177045822 = 56.024676352   boot/grub/core.img                             1
  52.100938797 = 55.942957056   boot/grub/grub.cfg                             1
  52.196886063 = 56.045979648   boot/initrd.img-2.6.38-8-generic               5
  52.129991531 = 55.974152192   boot/vmlinuz-2.6.38-8-generic                  3
  52.196886063 = 56.045979648   initrd.img                                     5
  52.129991531 = 55.974152192   vmlinuz                                        3

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```


What next?
JBA2337

---

### Post by drs305 on 2011-06-30
Grub is installed in the Windows partition boot record. (When you install Grub2, install it only to the drive and not a specific partition unless you have a specific need to do so.) 

You need to repair the Windows installation. Afterward you will probably have to reinstall Grub 2 from the LiveCD.

Here is a link to Windows repair options:
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

Once you have Windows working, if it boots directly to Windows you can reinstall G2 from the LiveCD by running the following commands:
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```
Don't use the partition number in the second command.

---

### Post by seawolf167 on 2011-06-30
> **JBA2337 said:**
> sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 109492076 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM


The boot sector type here should be "Windows XP". You should place your Windows XP installation cd in the cd/dvd drive, then reboot into it. You may have to adjust your BIOS settings (hit [F2] or [DEL] during POST to enter the BIOS setup screen), an change the boot priority order so it boots off a cd first. If for some reason you can't get this working, you can usually hit [F12] during POST for a boot menu, then select to boot off the cd.

Once booted to the cd, select the recovery console. You'll then be presented with a MS-DOS style console. In there, type in the command 

```
fixboot C:\
```

then reboot and check to see if your menu entries work.

---

### Post by oldfred on 2011-06-30
Both of the above will work if you have a windows disk. But windows keeps a backup of the boot sector in the partition. This will recover the backup using just Linux.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by JBA2337 on 2011-06-30
Success! I got my computer to boot as it should, which gives me a choice whether to boot Ubuntu 11.04 or Windows XP. Everything works as it should.

Thank you to everyone for your suggestions!!!:):D

It turned out to be not very difficult to repair the problem.
(1) I booted from a Windows XP installation CD, and I ran the Windows Recovery Console.
(2) At the command prompt I entered [code] fixboot C:\. After rebooting, Windows XP ran as it should, but Grub was gone.
(3) Finally, I booted from a Rescatux live CD (ver. 0.28 ), and using this CD Grub was restored. 

The above three steps took less than 10 minutes to accomplish. I will be sure to make a note of what I did, in case I ever need to do it again.

Thanks again to everyone.

JBA2337

---

### Post by seawolf167 on 2011-07-01
Glad its all working for you again!

---

