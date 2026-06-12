---
title: "boot issue"
date: 2011-11-13
forum: General Help
---

### Post by VVAW on 2011-11-13
I haven't used my pc in a few weeks and when I went to boot it up.
I have dual boot win7 and ubuntu.Instal inside windows

It when i click on ubuntu it keeps rebooting it is like there is a file missing not sure what and how to repair it.

I checked my windows c drive and ubuntu folder is there but not sure what to check for 

Any advice would be great.
I know you cant see but I have ubuntu highlighted

---

### Post by Rubi1200 on 2011-11-13
Hi,
please post the results of the boot info script to help us diagnose the problem.

There is a link at the bottom of my post with instructions.

You will need to either get hold of or make a LiveCD or LiveUSB to boot the computer.

Thanks.

---

### Post by VVAW on 2011-11-13
```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdh.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sdb1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdh1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   The info in boot sector on the starting sector of the 
                       MFT is wrong. The info in the boot sector on the 
                       starting sector of the MFT Mirror is wrong.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63 2,930,272,704 2,930,272,642   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   609,008,084   609,008,022   7 NTFS / exFAT / HPFS
/dev/sdb2         609,008,085   625,137,344    16,129,260   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   312,576,704   312,576,642   b W95 FAT32


Drive: sdh _____________________________________________________________________
Note: sector size is 4096 (not 512)

Disk /dev/sdh: 3000.6 GB, 3000558944256 bytes
255 heads, 63 sectors/track, 45599 cylinders, total 732558336 sectors
Units = sectors of 1 * 4096 = 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdh1                 256   732,558,335   732,558,080   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        BA8CB4B88CB4708D                       ntfs       
/dev/sdb1        0CB68709B686F30E                       ntfs       HP
/dev/sdb2        2C88743C8874071C                       ntfs       Recovery
/dev/sdc1        1234-5678                              vfat       SONICVIEW
/dev/sdh1        FA7AA76F7AA726FB                       ntfs       My Book

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== sdb1/Wubi/boot/grub/grub.cfg: =========================

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
insmod ntfs
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 0CB68709B686F30E
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 0CB68709B686F30E
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-10-generic-pae" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 0CB68709B686F30E
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=0CB68709B686F30E loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-10-generic-pae
}
menuentry "Ubuntu, Linux 2.6.38-10-generic-pae (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 0CB68709B686F30E
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=0CB68709B686F30E loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-10-generic-pae
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 0CB68709B686F30E
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 2C88743C8874071C
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

============================= sdb1/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sdb1/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

   4.202159882 = 4.512034816    boot/grub/grub.cfg                             1
   2.921875000 = 3.137339392    boot/initrd.img-2.6.38-10-generic-pae          2
   1.668399811 = 1.791430656    boot/vmlinuz-2.6.38-10-generic-pae             1
   2.921875000 = 3.137339392    initrd.img                                     2
   1.668399811 = 1.791430656    vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

MFT Sector of sdh1

00000000  89 03 48 8b 0f 48 85 c9  74 1e 8b c6 f0 0f c1 41  |..H..H..t......A|
00000010  08 03 c6 75 0f 48 85 c9  74 0a 48 8b 01 ba 01 00  |...u.H..t.H.....|
00000020  00 00 ff 10 48 83 27 00  48 8b c3 4c 8d 5c 24 70  |....H.'.H..L.\$p|
00000030  49 8b 5b 38 0f 28 74 24  60 0f 28 7c 24 50 45 0f  |I.[8.(t$`.(|$PE.|
00000040  28 43 d0 49 8b e3 5f 5e  5d c3 cc cc cc cc cc cc  |(C.I.._^].......|
00000050  cc cc cc cc cc cc cc cc  40 55 48 83 ec 20 48 8b  |........@UH.. H.|
00000060  ea 48 8b 8d 98 00 00 00  e8 73 f9 03 00 48 83 c4  |.H.......s...H..|
00000070  20 5d c3 cc cc cc cc cc  40 55 48 83 ec 20 48 8b  | ]......@UH.. H.|
00000080  ea 48 8b 8d 90 00 00 00  e8 53 f9 03 00 48 83 c4  |.H.......S...H..|
00000090  20 5d c3 cc cc cc cc cc  40 55 48 83 ec 20 48 8b  | ]......@UH.. H.|
000000a0  ea 48 8b 8d 90 00 00 00  48 83 c1 10 e8 9f 9b 00  |.H......H.......|
000000b0  00 48 83 c4 20 5d c3 cc  40 55 48 83 ec 20 48 8b  |.H.. ]..@UH.. H.|
000000c0  ea 48 8b 8d 90 00 00 00  48 83 c1 70 e8 3f f4 ff  |.H......H..p.?..|
000000d0  ff 48 83 c4 20 5d c3 cc  40 55 48 83 ec 20 48 8b  |.H.. ]..@UH.. H.|
000000e0  ea 48 8b 8d a0 00 00 00  e8 5b 98 00 00 48 83 c4  |.H.......[...H..|
000000f0  20 5d c3 cc cc cc cc cc  40 55 48 83 ec 20 48 8b  | ]......@UH.. H.|
00000100  ea 48 8b 8d 90 00 00 00  48 81 c1 b8 00 00 00 e8  |.H......H.......|
00000110  8c 02 00 00 48 83 c4 20  5d c3 cc cc cc cc cc cc  |....H.. ].......|
00000120  cc cc cc cc cc cc cc cc  40 55 48 83 ec 20 48 8b  |........@UH.. H.|
00000130  ea 48 8b 8d a0 00 00 00  e8 0b 98 00 00 48 83 c4  |.H...........H..|
00000140  20 5d c3 cc cc cc cc cc  40 55 48 83 ec 20 48 8b  | ]......@UH.. H.|
00000150  ea 48 8b 8d 90 00 00 00  48 81 c1 00 01 00 00 e8  |.H......H.......|
00000160  3c 02 00 00 48 83 c4 20  5d c3 cc cc cc cc cc cc  |<...H.. ].......|
00000170  cc cc cc cc cc cc cc cc  40 55 48 83 ec 20 48 8b  |........@UH.. H.|
00000180  ea 48 8b 8d a0 00 00 00  e8 bb 97 00 00 48 83 c4  |.H...........H..|
00000190  20 5d c3 cc cc cc cc cc  40 55 48 83 ec 20 48 8b  | ]......@UH.. H.|
000001a0  ea 48 8b 8d 90 00 00 00  48 81 c1 48 01 00 00 e8  |.H......H..H....|
000001b0  ec 01 00 00 48 83 c4 20  5d c3 cc cc cc cc cc cc  |....H.. ].......|
000001c0  cc cc cc cc cc cc cc cc  40 55 48 83 ec 20 48 8b  |........@UH.. H.|
000001d0  ea 48 8b 8d a0 00 00 00  e8 6b 97 00 00 48 83 c4  |.H.......k...H..|
000001e0  20 5d c3 cc cc cc cc cc  40 55 48 83 ec 20 48 8b  | ]......@UH.. H.|
000001f0  ea 48 8b 8d 90 00 00 00  48 81 c1 90 01 00 00 e8  |.H......H.......|
00000200

========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

ERROR: unsupported sector size 4096 on /dev/sdh.
ERROR: unsupported sector size 4096 on /dev/sdh.
```

---

### Post by Rubi1200 on 2011-11-14
Thanks for posting the results.

Not quite sure what is going on here and I will ask some other members to take a look and offer their perspectives.

Please be patient and wait for us to respond.

---

### Post by coffeecat on 2011-11-14
Hi. I don't have an answer, but a couple of questions.

> **VVAW said:**
> It when i click on ubuntu it keeps rebooting it is like there is a file missing not sure what and how to repair it.

After you select Ubuntu from the white on black wubi menu that you posted, you should see a second (grub) menu with these choices:

```
Ubuntu, Linux 2.6.38-10-generic-pae
Ubuntu, Linux 2.6.38-10-generic-pae (recovery mode)
Windows 7 (loader) (on /dev/sda1)
Windows Vista (loader) (on /dev/sda2)
```

Do you see them? If so, and when you choose the first, do you get any error messages before it reboots? When it reboots, do you get the BIOS POST screen and then the white on black wubi menu, or are you simply taken back to the grub menu?

One little oddity in your boot script output that I don't think is related to your problem, but a question anyway. 

> **VVAW said:**
> ```

sdh1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   The info in boot sector on the starting sector of the 
                       MFT is wrong. The info in the boot sector on the 
                       starting sector of the MFT Mirror is wrong.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

<snip>

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        BA8CB4B88CB4708D                       ntfs       
/dev/sdb1        0CB68709B686F30E                       ntfs       HP
/dev/sdb2        2C88743C8874071C                       ntfs       Recovery
/dev/sdc1        1234-5678                              vfat       SONICVIEW
/dev/sdh1        FA7AA76F7AA726FB                       ntfs       My Book
```

/dev/sdh1 looks to be a 3TB Western Digital "My Book" USB drive. Is that correct? Are you able to access it OK from Windows? If so, the MFT mirror issue in the boot sector may be of little consequence, but to be honest I'm not sure.

---

### Post by wowcolombia1 on 2011-11-14
Maybe(i think)that when you go to the Ubuntu's boot you are  chosing the incorrect one,be sure that you go to the first one in the list.I think there are 4 but maybe you are going to the second one,just go to the first and try out if it works.
Hope this helped:)

---

### Post by VVAW on 2011-11-14
when I click on ubuntu the pc just reboots it doesn't go to that screen.

I removed all of the usb drives and tried with no success

---

### Post by bcbc on 2011-11-14
Did you add the 1.5 TB drive recently? (it looks like it was added since the last time the grub.cfg was regenerated). Did you remove that and try booting the Wubi install?

I am guessing that grub4dos is blowing it's brains out on that. Otherwise you'd at least see a "Try (hd0,0): wubildr not found" message.

---

### Post by VVAW on 2011-11-14
tried it and still nothing

---

### Post by VVAW on 2011-11-14
I remember I copied the ubuntu file to one of my usb drives and deleted it because thought I never needed it.
I used recuva to try to recover the file but not finding it.

Do you guys recommend a good free program to recover deleted files on windows 

thanks

---

### Post by bcbc on 2011-11-14
> **VVAW said:**
> I remember I copied the ubuntu file to one of my usb drives and deleted it because thought I never needed it.
I used recuva to try to recover the file but not finding it.

Do you guys recommend a good free program to recover deleted files on windows 

thanks
What file? Can you recall the name? The bootinfoscript doesn't indicate there's a missing file.

---

### Post by VVAW on 2011-11-15
[QUOTE=coffeecat;11455375]Hi. I don't have an answer, but a couple of questions.



After you select Ubuntu from the white on black wubi menu that you posted, you should see a second (grub) menu with these choices:

```
Ubuntu, Linux 2.6.38-10-generic-pae
Ubuntu, Linux 2.6.38-10-generic-pae (recovery mode)
Windows 7 (loader) (on /dev/sda1)
Windows Vista (loader) (on /dev/sda2)
```

Do you see them? If so, and when you choose the first, do you get any error messages before it reboots? When it reboots, do you get the BIOS POST screen and then the white on black wubi menu, or are you simply taken back to the grub menu?

I never see this screen after I choose ubuntu pc reboots
Now it says error file not found

---

### Post by VVAW on 2011-11-15
Hey guys fixed the issue 

[https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu)

I did a chkdsk /r and it fixed my issue

---

### Post by bcbc on 2011-11-15
Cool! Sometimes it's the simplest thing! Good job.

---

### Post by Rubi1200 on 2011-11-15
> **VVAW said:**
> Hey guys fixed the issue 

[https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu)

I did a chkdsk /r and it fixed my issue
Excellent! Glad you got things sorted out :D

Please mark this Solved using the Thread Tools near the top of the page.

---

### Post by VVAW on 2011-11-20
Crazy 
Now this happened to me
Note that sometimes files are moved by Windows into a hidden folder called C:\found.000. You need to have C:\ubuntu\disks\root.disk. If you do not see those, look for found.000. You need to change the Windows Explorer settings to be able to see hidden folders first, then move the files from found.000 to their original location. Sometimes the entire \ubuntu\disks directory may be recovered to \found.000 in a folder named dir0000.chk.

Fixed now not sure what is going on.

I have 2 questions.
1 Can I copy these ubuntu files over to a new windows 7 install.

2 Can I increase this wubi install to more then 30 gig

---

### Post by bcbc on 2011-11-20
If you're running into corruption, it could be because you are doing a hard poweroff. This is not a good idea - if the wubi install is hanging then use Alt+SysRq R-E-I-S-U-B to safely reboot instead.

If that's not the cause of your corruption, then it could be some hardware incompatibility. 

While it is possible to increase a wubi install size beyond 30GB - it's not a good idea, especially if your install gets corrupted. Because in some cases if the corruption is severe enough you can lose your root.disk completely (and all the data on it). You can store data on your windows /host instead (safer) or try doing a traditional dual boot.

---

### Post by VVAW on 2011-11-20
I don't remember doing a Hard boot but it is possible.

what about copying this file over the a new windows install.

---

### Post by bcbc on 2011-11-20
> **VVAW said:**
> I don't remember doing a Hard boot but it is possible.

what about copying this file over the a new windows install.

Check this out: [http://askubuntu.com/questions/56726/can-i-copy-my-wubi-install-between-machines](http://askubuntu.com/questions/56726/can-i-copy-my-wubi-install-between-machines)

---

### Post by VVAW on 2012-01-10
ok same issue again today however I am unable to get it to boot at all. I get  either the grub screen or blinking cursor.

I backed up root.disk so can I uinstall wubi then reinstall then copy over the root.disk file will this bring back my install.

Or can I somehow install root.disk onto a new hardrive to boot as it own OS 

PLEASE SOME HELP HERE 

THIS IS A ONGOING ISSUES I NEED TO RESOLVE

---

### Post by oldfred on 2012-01-10
bcbc has some of the best info on wubi.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

I am not sure if your 4K drive is causing confusion. I do not fully understand them, but have seen where Windows with MBR does not see them correctly. Normally larger drives are gpt. Windows will also read gpt drives, but will not boot from them unless using UEFI. But windows will not boot from an external anyway.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

Since you have several drives & lots of space, you should consider a full install of Ubuntu to partitions on a different drive. Note the grub has had some issues with very large drives and very large root partitions. So I would keep / (root) smaller and make /home a separate larger partition.

Just for consideration:
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by VVAW on 2012-01-10
ok great thanks for reply however In order for me to migrate I need to boot into my current Ubuntu OS Which I can't at the moment.

---

