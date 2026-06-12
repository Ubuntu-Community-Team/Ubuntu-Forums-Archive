---
title: "Grub not showing windows 7"
date: 2010-02-11
forum: General Help
---

### Post by BucksRok on 2010-02-11
I was foolishly messing around with Grub trying to get it so it only show my two most recent kernel versions of Ubuntu and Windows 7.  The tutorials on how to do this were not clear, so I deemed it not a big deal and ultimately didn't end up making any changes.  However when I restarted to boot into Windows 7 it was gone for Grub's boot list.  I looked at the grub.cfg file and in it under os-prober, where i'm assuming Windows 7 should be there was only Vista (which wouldn't boot when I tried it, just a black screen). I had upgraded from Vista over the internet when Windows 7 first came out, then installed Ubuntu and it worked fine until this.  I am using 64-bit Ubuntu 9.10, and have Grub 1.97 beta~4 installed, which was installed with Ubunutu.

Thanks
Alex

---

### Post by Mark Phelps on 2010-02-11
Have you tried running "sudo update-grub" and watching what kernels and OSs it detects?

---

### Post by BucksRok on 2010-02-11
**Here's the output:**
> Found kernel: /boot/vmlinuz-2.6.31-19-generic
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-15-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... doneNow vista isn't even showing.

---

### Post by James M on 2010-02-11
... Grub is so great. Rofl

---

### Post by samantha_ on 2010-02-11
```

sudo apt-get --purge remove grub-pc grub-common
sudo apt-get install grub-pc grub-common

```
I had the same problem when I was messing with the os-prober file when I was banging my head against the wall wondering why osx just refused to show up.

---

### Post by BucksRok on 2010-02-11
That put vista back, but still no windows 7.  At the end where windows 7 should be it says:
> Found Windows Vista (loader) on /dev/sda17 is on /dev/sda2. sda1 is suppose to be my recovery.  Disk Utility shows sda2 as NTFS and bootable.

---

### Post by samantha_ on 2010-02-11
> **BucksRok said:**
> That put vista back, but still no windows 7.  At the end where windows 7 should be it says:
7 is on /dev/sda2. sda1 is suppose to be my recovery.  Disk Utility shows sda2 as NTFS and bootable.

I guess a temperory solution would be to manually create the entries ourselves.
Can you run
```

cat /boot/grub/grub.cfg
```

EDIT:
```

gksudo gedit /etc/grub.d/25_windows

```
c&p
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
menuentry "Windows Vienna" {
insmod ntfs
set root=(hd0,2)
chainloader +1
}

```
run
```

sudo chmod -x 25_windows
sudo chmod 774 20*
```

---

### Post by BucksRok on 2010-02-11
Yes.  It showed the same linux kernels and this under os prober:
> ### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1ee8b4b7e8b48f11
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###


---

### Post by samantha_ on 2010-02-11
> **BucksRok said:**
> Yes.  It showed the same linux kernels and this under os prober:

[s]whats the UUID for the windows 7 partition?[/s]
nvm.
follow directions above.

---

### Post by BucksRok on 2010-02-11
OK I ran the instructions above.

---

### Post by samantha_ on 2010-02-12
now run "update-grub" and the windows 7 should now show up in the menu

---

### Post by Mark Phelps on 2010-02-12
> **BucksRok said:**
> **Here's the output:**
Now vista isn't even showing.

This shows you have legacy GRUB installed because GRUB2 doesn't use a menu.lst file. 

I saw in a later post that you've made some repairs and GRUB2 now finds the Vista loader.

Have you tried that and seen what it does?  I'm asking because GRUB2 often only finds 1 loader, and when you select that, you generally get an OS menu where you can select XP, Vista, Win7 -- whichever ones you have installed.

---

### Post by BucksRok on 2010-02-12
It just starts the windows recovery, which doesn't appear to be working because it just goes to a black screen with my mouse on it.

And Samantha after running update-grub and restarting windows 7 did show up, but after the load screen it goes blue for an instant then just reboots.  And selecting the recovery option just gives me the same things as above.

---

### Post by samantha_ on 2010-02-12
> **BucksRok said:**
> It just starts the windows recovery, which doesn't appear to be working because it just goes to a black screen with my mouse on it.

And Samantha after running update-grub and restarting windows 7 did show up, but after the load screen it goes blue for an instant then just reboots.  And selecting the recovery option just gives me the same things as above.

welcome to the wonderful world of BSODs.
Right after selecting the windows 7 entry in grub2, press F5
select "disable restart after crash" (or something along those lines, I dont have windows)

At least we got win7 booting, but its crashing.....

hmm wait.
better idea.
You could have a corrupt disk/partition, so

Download this: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
burn it.
boot up from it.
select your language
select "command prompt"
type in
```

chkdsk C: /r

```

---

### Post by BucksRok on 2010-02-12
I downloaded the .iso and burned it.  After starting the computer and booting from the CD a status bar came up saying "configuring windows files"  then a loading bar comes up, after a long time a black screen shows up with just a mouse on it.  All I can do is move the mouse, not select anything (although there is nothing to select)  no right clicking, nothing.

---

### Post by Muirdoch on 2011-05-27
Can someone help me as well?


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => No boot loader? is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   185,478,983   185,478,921   7 NTFS / exFAT / HPFS
/dev/sda2         185,479,166   234,440,703    48,961,538   5 Extended
/dev/sda5         185,479,168   232,321,023    46,841,856  83 Linux
/dev/sda6         232,323,072   234,440,703     2,117,632  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2031 MB, 2031091712 bytes
16 heads, 32 sectors/track, 7748 cylinders, total 3966976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064     3,966,975     3,958,912   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        6030943C30941ADC                       ntfs       
/dev/sda5        84da7a0f-5aa9-4e05-8836-42ad939e6867   ext4       
/dev/sda6        39a29c0b-6025-4669-92cc-ddde9be77512   swap       
/dev/sdb1        F249-76E2                              vfat       eX=»ßd›¢Lß‚

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/eX=               vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 84da7a0f-5aa9-4e05-8836-42ad939e6867
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 84da7a0f-5aa9-4e05-8836-42ad939e6867
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
menuentry 'Ubuntu, with Linux 2.6.38-9-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 84da7a0f-5aa9-4e05-8836-42ad939e6867
	linux	/boot/vmlinuz-2.6.38-9-generic root=UUID=84da7a0f-5aa9-4e05-8836-42ad939e6867 ro  splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 84da7a0f-5aa9-4e05-8836-42ad939e6867
	echo	'Loading Linux 2.6.38-9-generic ...'
	linux	/boot/vmlinuz-2.6.38-9-generic root=UUID=84da7a0f-5aa9-4e05-8836-42ad939e6867 ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-9-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 84da7a0f-5aa9-4e05-8836-42ad939e6867
	linux	/boot/vmlinuz-2.6.35-29-generic root=UUID=84da7a0f-5aa9-4e05-8836-42ad939e6867 ro  splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 84da7a0f-5aa9-4e05-8836-42ad939e6867
	echo	'Loading Linux 2.6.35-29-generic ...'
	linux	/boot/vmlinuz-2.6.35-29-generic root=UUID=84da7a0f-5aa9-4e05-8836-42ad939e6867 ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-29-generic
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
	search --no-floppy --fs-uuid --set=root 84da7a0f-5aa9-4e05-8836-42ad939e6867
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 84da7a0f-5aa9-4e05-8836-42ad939e6867
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=84da7a0f-5aa9-4e05-8836-42ad939e6867 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=39a29c0b-6025-4669-92cc-ddde9be77512 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  94.639125824 = 101.617987584  boot/grub/core.img                             1
  94.974960327 = 101.978587136  boot/grub/grub.cfg                             1
  89.715126038 = 96.330883072   boot/initrd.img-2.6.35-29-generic              2
  95.944675446 = 103.019810816  boot/initrd.img-2.6.38-9-generic               2
  94.703067780 = 101.686644736  boot/vmlinuz-2.6.35-29-generic                 1
  94.002258301 = 100.934156288  boot/vmlinuz-2.6.38-9-generic                  1
  95.944675446 = 103.019810816  initrd.img                                     2
  89.715126038 = 96.330883072   initrd.img.old                                 2
  94.002258301 = 100.934156288  vmlinuz                                        1
  94.703067780 = 101.686644736  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 da 01  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......|
00000020  80 68 3c 00 13 0f 00 00  00 00 00 00 02 00 00 00  |.h<.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 e2 76 49 f2 4e  4f 20 4e 41 4d 45 20 20  |..).vI.NO NAME  |
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

