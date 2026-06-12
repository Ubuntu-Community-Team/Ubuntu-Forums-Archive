---
title: "Grub Rescue Help"
date: 2011-07-08
forum: General Help
---

### Post by Ericj1186 on 2011-07-08
So, I had Ubuntu and Mint on my second hard drive (first drive has 7), and I reinstalled Ubuntu over the entire thing (upgraded from 10.04).  Ubuntu now has one drive to itself, while Windows has the other.

When I did this, I booted into Grub Rescue.  Restarted and switched hard drives, same thing.  I loaded the LiveCD and followed [this repair guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

I discovered I don't have a Boot.cfg (or .lst) or another file of the three required.  I noticed my install did not have any /boot partition, so I reinstalled a few times, all with the same error.  Finally, I go back to the LiveCD desktop and run the following:
```
sudo grub-install --boot-directory=/media/[long string]/boot /dev/sda

```

And this is the output:

```
/usr/sbin/grub-probe: error: cannot stat: /dev/sda/
```

This is on Ubuntu 11.04 with GRUB2 (1.99).

---

### Post by YesWeCan on 2011-07-08
Hi there. A little more info is needed. A convenient tool can be downloaded from here:  [FONT=Nimbus Sans L, sans-serif]http://bootinfoscript.sourceforge.net/[/FONT]
[FONT=Nimbus Sans L, sans-serif]Would you please post the RESULTS.txt here?
[/FONT]

---

### Post by Ericj1186 on 2011-07-08
Done and done:
```

  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 4 for (,msdos4)/boot/grub.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     9,764,863     9,762,816  82 Linux swap / Solaris
/dev/sda2    *      9,764,864    29,296,639    19,531,776  83 Linux
/dev/sda3          29,298,686 1,953,523,711 1,924,225,026   5 Extended
/dev/sda5          29,298,688 1,953,523,711 1,924,225,024  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848   978,016,255   977,809,408   7 NTFS / exFAT / HPFS
/dev/sdb3         978,016,256 1,953,519,615   975,503,360   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        b69ca8a3-f096-4a0f-97ac-cc0b789387f3   swap       
/dev/sda2        454b7a48-96f5-474b-8e8f-99a4a5c669f6   ext4       
/dev/sda5        b572a474-75b0-4ef1-9cfb-3a2e2faff5a4   ext4       
/dev/sdb1        10701029701017D4                       ntfs       System Reserved
/dev/sdb2        588415028414E3F2                       ntfs       
/dev/sdb3        AA0C74920C745AF1                       ntfs       Local Disk

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/454b7a48-96f5-474b-8e8f-99a4a5c669f6 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


============================= sda2/grub/grub.cfg: ==============================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root b572a474-75b0-4ef1-9cfb-3a2e2faff5a4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 454b7a48-96f5-474b-8e8f-99a4a5c669f6
set locale_dir=($root)/grub/locale
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
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 454b7a48-96f5-474b-8e8f-99a4a5c669f6
    linux    /vmlinuz-2.6.38-8-generic root=UUID=b572a474-75b0-4ef1-9cfb-3a2e2faff5a4 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 454b7a48-96f5-474b-8e8f-99a4a5c669f6
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=b572a474-75b0-4ef1-9cfb-3a2e2faff5a4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 454b7a48-96f5-474b-8e8f-99a4a5c669f6
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 454b7a48-96f5-474b-8e8f-99a4a5c669f6
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 10701029701017D4
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

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   6.782981873 = 7.283171328    grub/core.img                                  1
   6.783210754 = 7.283417088    grub/grub.cfg                                  1
   4.804687500 = 5.158993920    initrd.img-2.6.38-8-generic                    2
   4.791385651 = 5.144711168    vmlinuz-2.6.38-8-generic                       1

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
UUID=b572a474-75b0-4ef1-9cfb-3a2e2faff5a4 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=454b7a48-96f5-474b-8e8f-99a4a5c669f6 /boot           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=b69ca8a3-f096-4a0f-97ac-cc0b789387f3 none            swap    sw              0       0
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  ae 6d 6f 7b 7c b4 3b 35  c1 6f 40 75 b1 a8 8c c1  |.mo{|.;5.o@u....|
00000010  fa f5 c1 be bc ba 92 dc  28 9f c8 29 8e 9b 55 24  |........(..)..U$|
00000020  a4 5a 09 c0 86 15 fc 6e  a1 f4 5e 18 96 94 70 c1  |.Z.....n..^...p.|
00000030  d8 e6 36 f6 c2 7d ef 4c  a0 14 02 34 59 92 48 dd  |..6..}.L...4Y.H.|
00000040  57 92 d8 18 48 9e c9 bd  f4 f2 e4 77 ed 69 02 38  |W...H......w.i.8|
00000050  25 fb e5 17 b0 78 92 f1  fd 89 46 db 17 6e 4e f1  |%....x....F..nN.|
00000060  a6 b0 f1 fc 4a 30 72 72  df d4 89 c7 00 87 c4 a4  |....J0rr........|
00000070  ba c6 99 27 1a a9 c6 1e  a1 5c 15 57 27 2b 04 85  |...'.....\.W'+..|
00000080  c4 66 b7 4b 05 5c ac ae  d6 d9 17 ed b6 50 f0 db  |.f.K.\.......P..|
00000090  00 4c 1c 8d 59 bb 6f 26  bd 1e cf cf cb eb 04 ba  |.L..Y.o&........|
000000a0  2f 04 13 b6 a2 0c 91 c8  9d ab 4e 63 e7 06 42 41  |/.........Nc..BA|
000000b0  cd cd 01 52 cb 87 d6 aa  4d 97 fe ad 4a 6c a4 98  |...R....M...Jl..|
000000c0  36 d9 8b 3c 65 ac a3 87  82 5f e2 70 e5 2a 12 f1  |6..<e...._.p.*..|
000000d0  b8 f7 a7 3e 89 3b c7 bd  e8 cf fb f6 ce ab 59 3c  |...>.;........Y<|
000000e0  9b 39 7c 54 56 cc 03 73  0c 05 3e ca 63 f1 cf a7  |.9|TV..s..>.c...|
000000f0  fd 5a fb d3 59 b6 ec cd  f3 dc 03 61 48 d5 8d 8e  |.Z..Y......aH...|
00000100  ff 4e 9d cc e7 94 ee 31  ba 2c 68 bc 96 9e 41 28  |.N.....1.,h...A(|
00000110  82 19 cb ce 72 8c cb 69  9d 30 d7 00 7c 00 af 43  |....r..i.0..|..C|
00000120  76 6e 01 f9 c7 12 95 ae  55 0f f0 80 b0 35 4f 3d  |vn......U....5O=|
00000130  d8 4e 19 9b 73 fe 38 de  ff b0 67 f2 c2 9f 44 72  |.N..s.8...g...Dr|
00000140  a7 9c 79 f2 87 05 e4 21  e6 b0 70 8a 93 1a 4e 5a  |..y....!..p...NZ|
00000150  e8 50 f0 94 14 c7 49 7c  c6 e3 80 80 05 13 80 75  |.P....I|.......u|
00000160  86 f9 0b ea e1 28 f4 50  ce 10 c9 b6 73 34 f9 76  |.....(.P....s4.v|
00000170  14 50 65 fc 91 b1 e1 2a  8b 38 bd 1e 72 ed 32 c7  |.Pe....*.8..r.2.|
00000180  c7 6f 03 0f a4 dd 57 38  eb b9 53 cd b1 1d fa b0  |.o....W8..S.....|
00000190  21 f7 c7 2d eb 01 80 39  74 3a aa a1 85 c4 f9 c8  |!..-...9t:......|
000001a0  4b 1b c9 75 cb cc 46 2b  2e 3b e2 1c 8b 3b 68 41  |K..u..F+.;...;hA|
000001b0  ad 94 a5 31 47 55 23 68  70 b6 c9 63 44 18 00 fe  |...1GU#hp..cD...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 58 b1 72 00 00  |...........X.r..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by YesWeCan on 2011-07-08
[LEFT]It looks like your Grub boot code thinks your boot partition is in sda1 instead of sda2. This is why you get the rescue prompt.
From your 11.04 live CD try:
[COLOR=Navy]sudo mount /dev/sda2 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda[/COLOR]

Also, your sbd disk, that has only Windows on it, also has a Grub boot code in its MBR. You probably don't want this - better to have the standard MBR in case you ever need to boot Windows directly. Best to do this using your Windows CD and repair the MBR code.
You can install a similar MBR code using Ubuntu:
[COLOR=Navy]sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr[/COLOR]

If you find that your Windows 7 is missing from the Grub menu when you boot sda, once in Ubuntu run [COLOR=Navy]sudo update-grub[/COLOR].
[/LEFT]

---

### Post by Ericj1186 on 2011-07-08
Dang... Is there anyway to get a copy of the Windows Rescue disc?  I have recovery discs for my Acer Laptop which have Windows on it.  Is there any way I can make a rescue disc from that (or even my version of Windows)?

Thanks for the suggestions, I'll give this a try when I get home and report back.

---

### Post by Blasphemist on 2011-07-08
> **Ericj1186 said:**
> Dang... Is there anyway to get a copy of the Windows Rescue disc?  I have recovery discs for my Acer Laptop which have Windows on it.  Is there any way I can make a rescue disc from that (or even my version of Windows)?

Thanks for the suggestions, I'll give this a try when I get home and report back.

[http://www.addictivetips.com/windows-tips/windows-7-recovery-disk-boot-disk/](http://www.addictivetips.com/windows-tips/windows-7-recovery-disk-boot-disk/)

This is one of the links that google found for me. It shows how to create one from any win 7 system that you can use and it also has a link to download one. I can't speak for the safety of the download.

---

### Post by Ericj1186 on 2011-07-09
Two things:

1. When I ran what YesWeCan said, I rebooted with no GRUB, but booted into Windows, which was better than I was doing before.  Is this because Windows had the MBR?

2. When I restarted, my Windows 7 lost its genuine status.

---

### Post by Blasphemist on 2011-07-09
The answer to the first question is yes, grub isn't in the mbr anymore. You'll need to follow the first post in this thread [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Specifically, this section.
> Reinstalling GRUB 2 from LiveCD 
If you cannot boot from GRUB 2 and need to reinstall it, here is the simple method. For more details or for advanced options, refer to the Ubuntu community documentation here: Grub2 - Reinstalling GRUB 2:
Boot the Ubuntu Live CD (Try without installing).
From the Desktop, open a terminal - Applications, Accessories, Terminal.
Determine your normal system partition - `sudo fdisk -l` (That is a lowercase L)
If you aren't sure, run `df -Th`. Look for the correct disk size and ext3 or ext4 format.
Mount your normal system partition:
Code:
sudo mount /dev/sdXY /mnt
If you aren't sure if you mounted the correct partition, once it's mounted run "nautilus /mnt" to inspect the partition. If it is the correct partition, you should see the normal Ubuntu folders such as /bin, /boot, /etc, /home, etc
Example: sudo mount /dev/sda1 /mnt
Note: The partition to mount is normally the partition on which Ubuntu was installed: sda1, sdb5, etc. If you have a separate /boot partition, use the device on which the /boot partition is located. Grub 2 works best when installed in the MBR of the drive to which BIOS boots. Also remember that you mount the partition (including the number) in this step, but you do not include the partition number when you run the "sudo grub-install" command later.
Note: GRUB 2 counts the first drive (X) as "0", but the first partition (Y) as "1"
Only if you have a separate boot partition:
Code:
sudo mount /dev/sdXY /mnt/boot
with sdXY being your /boot partition designation.
Reinstall GRUB 2:
Code:
sudo grub-install --root-directory=/mnt /dev/sdX
Do NOT include the partition number.
Example: sudo grub-install --root-directory=/mnt /dev/sda
Note: Substitute the device on which Ubuntu was installed - sda, sdb, etc. Do not specify a partition number.
Unmount the partition *:
Code:
sudo umount /mnt
* Note: If you mounted a separate /boot partition, unmount it first: 
Code:
sudo umount /mnt/boot
Reboot.

You could also use this reference to reinstall grub2. [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

On your second issue, Wow! I know they always want to update that genuine advantage tool or whatever it is. Is that causing issues? Not that I know off hand how to help with that.

---

### Post by Ericj1186 on 2011-07-09
I'll give the first a try, but I figured out the second.

I recently rebuilt my computer with a new case, video card, and motherboard.  While the HDDs were the same, Windows gave me a "This version is non-genuine," which went away.  When I booted up, my internet didn't connect, and Windows saw this as me running a counterfeit version.  It's all resolved now, but quite the headache.

---

### Post by YesWeCan on 2011-07-10
Have you got it sorted now? The idea is that when you tell the bios to boot sda first it boots using Grub and you get a menu to choose between Ubuntu and Windows. But if you tell the bios to boot sdb first it should boot directly into Windows. Normally, you should have the bios booting sda first.

---

### Post by Ericj1186 on 2011-07-10
I was busy today, so I didn't get to try it, but I will update when I do.  I should be Tuesday at the latest.

---

