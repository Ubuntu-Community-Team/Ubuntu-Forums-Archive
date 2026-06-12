---
title: "multiboot w/ 2 hdd's?"
date: 2010-12-22
forum: General Help
---

### Post by threestripebrand on 2010-12-22
i appologize in  advance if this is the wrong place for this post. I've been at this all  day without success. i found an old tower in my garage so i decided to  mess around with it a little bit and add a dvd drive and another hdd etc.  anyway it now has two 80gb hdd's i installed windows xp on one, and i  would like to install 10.10 on half of the other and maybe osx on the  remaining or whatever. anyway I've tried everything I've found in posts  and nothing has worked. i left wonder if this due to it being on another  drive. i would like the multi boot option. I've got 10.10 installed but  now all i have is grub rescue. even when i use the supergrub2 it doesn't  show linux there. and that seems to be the only way to get into windows  now. when in terminal when working from live cd, using fdisk -l i see  linux there. so basicly nothing works lol. any help would make this noob  very happy. thanks for your time whoever reads this.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,126    81,006,591    80,990,466   f W95 Ext d (LBA)
/dev/sdb5              16,128    77,934,896    77,918,769   7 HPFS/NTFS
/dev/sdb6          77,936,640    81,006,591     3,069,952  82 Linux swap / Solaris
/dev/sdb2          81,006,592   156,301,311    75,294,720  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        4C51000150FFF016                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        a3fa0b94-7953-414e-ab80-154d6b3acddd   ext4                                     
/dev/sdb5        E2A47A29A47A0079                       ntfs       New Volume                    
/dev/sdb6        064a7d45-aa75-4c55-acb5-057ba79c9d95   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set a3fa0b94-7953-414e-ab80-154d6b3acddd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set a3fa0b94-7953-414e-ab80-154d6b3acddd
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set a3fa0b94-7953-414e-ab80-154d6b3acddd
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a3fa0b94-7953-414e-ab80-154d6b3acddd ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set a3fa0b94-7953-414e-ab80-154d6b3acddd
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a3fa0b94-7953-414e-ab80-154d6b3acddd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set a3fa0b94-7953-414e-ab80-154d6b3acddd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set a3fa0b94-7953-414e-ab80-154d6b3acddd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4c51000150fff016
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

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=a3fa0b94-7953-414e-ab80-154d6b3acddd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=064a7d45-aa75-4c55-acb5-057ba79c9d95 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


  63.1GB: boot/grub/core.img
  69.5GB: boot/grub/grub.cfg
  42.3GB: boot/initrd.img-2.6.35-22-generic
  63.1GB: boot/vmlinuz-2.6.35-22-generic
  42.3GB: initrd.img
  63.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  a6 59 a2 98 5b 0f de af  38 8e fa e1 0a 31 ba 17  |.Y..[...8....1..|
00000010  ea e1 5d f9 b1 3f 76 7c  2f 95 70 8f 77 d7 03 37  |..]..?v|/.p.w..7|
00000020  8a b6 b3 04 c8 35 da e7  66 b9 ae 37 05 71 05 40  |.....5..f..7.q.@|
00000030  5c 5b 12 3d c9 4c 25 9e  0e 6a 3d ac 16 e3 52 1a  |\[.=.L%..j=...R.|
00000040  98 8c 02 dc a2 36 6e 94  a7 78 23 e1 d5 cc 8b e3  |.....6n..x#.....|
00000050  16 35 a7 1f 32 79 51 99  69 e5 4e d4 2f c2 1c 13  |.5..2yQ.i.N./...|
00000060  86 49 a9 eb f9 a0 3e c0  ad 77 53 15 17 1b a7 6f  |.I....>..wS....o|
00000070  e6 4d a8 3b 06 ee 3b 83  dd f5 52 4f 5c 86 8c 2b  |.M.;..;...RO\..+|
00000080  88 50 c5 05 52 bf c6 03  13 d4 51 85 9f 43 2e 6d  |.P..R.....Q..C.m|
00000090  8d a0 54 10 50 4d 8a b9  76 4d cc e0 3b 06 e9 fa  |..T.PM..vM..;...|
000000a0  52 5a db 25 09 4f 7a d8  3a e1 da d6 33 7a 2e 00  |RZ.%.Oz.:...3z..|
000000b0  2f 7e 73 88 39 e5 3f 43  22 b5 6e c7 9e 17 d1 a6  |/~s.9.?C".n.....|
000000c0  f8 dc 92 1e 84 97 5f e1  6a 2c ef ea a3 5d cb 92  |......_.j,...]..|
000000d0  dc 62 5a f8 4f f9 33 66  8d c9 67 99 e2 a6 9d e6  |.bZ.O.3f..g.....|
000000e0  5e dc 6e f4 e6 3c e2 64  dd 3a 97 17 fb 85 e7 26  |^.n..<.d.:.....&|
000000f0  57 49 76 01 9a 91 27 be  22 59 7e 9b 93 6e f4 c0  |WIv...'."Y~..n..|
00000100  eb 9c 18 39 92 f0 86 cb  54 0d 5a fa 46 ff 16 35  |...9....T.Z.F..5|
00000110  f6 e5 16 8e ce 6e 40 ba  e9 79 68 85 d1 fd d3 52  |.....n@..yh....R|
00000120  a1 40 5a 3a af 9f 29 57  1c c9 35 b5 69 16 94 fc  |.@Z:..)W..5.i...|
00000130  8e 87 25 a6 31 74 68 be  e6 6e 44 95 27 18 d2 c3  |..%.1th..nD.'...|
00000140  da 95 99 ce 29 56 46 85  21 ee e2 e6 c1 0a 39 d0  |....)VF.!.....9.|
00000150  66 94 51 f3 54 53 67 73  56 f9 23 93 d3 4e a8 7a  |f.Q.TSgsV.#..N.z|
00000160  41 df 28 5d 4a 56 a3 70  fa a3 a4 7d 5e 0f 07 0a  |A.(]JV.p...}^...|
00000170  38 0e 5c ee 42 45 86 bd  d3 7a 20 da 5e d8 e9 44  |8.\.BE...z .^..D|
00000180  d9 ba b3 e4 2e 82 df c2  57 8b c6 4f 21 7c 7a 5f  |........W..O!|z_|
00000190  86 07 99 7e eb 91 6c 07  8f c8 5f 38 8d ec 78 9b  |...~..l..._8..x.|
000001a0  1d 3c 70 14 d1 7a c7 73  59 7d 48 cb 89 90 4b 18  |.<p..z.sY}H...K.|
000001b0  60 c5 8a 30 00 32 2a 99  0a d3 e7 b7 49 77 00 01  |`..0.2*.....Iw..|
000001c0  01 01 07 fe ff ff 02 00  00 00 31 f2 a4 04 00 fe  |..........1.....|
000001d0  ff ff 05 fe ff ff 33 f2  a4 04 cf de 2e 00 00 00  |......3.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2010-12-22
Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

You want the MS bootloader in sda boot the XP cd go to the repair command and run /fixmbr. Make sure your pointed at the sda HD mbr which is sda.

Then put the sdb to boot first in the bios grub should boot Ubuntu, if it does run in the Ubuntu terminal.
sudo update-grub.

Also if that is not a Apple computer you can't legally install OSX don't mention it again, they will close your thread.

---

### Post by threestripebrand on 2010-12-22
thank for the fast reply. would being in the hd of windows before i restart and boot from cd be good enought for pointing the fixmbr to sda? because i dont think there is an option to choose diferent hd's before running the fixmbr. if there isnt a choice should i run it anyway or will that effect both sda and sdb? i'll go check it out.

---

### Post by wilee-nilee on 2010-12-22
> **threestripebrand said:**
> thank for the fast reply. would being in the hd of windows before i restart and boot from cd be good enought for pointing the fixmbr to sda? because i dont think there is an option to choose diferent hd's before running the fixmbr. if there isnt a choice should i run it anyway or will that effect both sda and sdb? i'll go check it out.

Your booting the cd it will probably find windows for you.

---

### Post by threestripebrand on 2010-12-22
well the fixmbr went well the only hd available was c. guess i'll google how to  put the sdb to boot first in the bios grub.

---

### Post by wilee-nilee on 2010-12-22
> **threestripebrand said:**
> well the fixmbr went well the only hd available was c. guess i'll google how to  put the sdb to boot first in the bios grub.

On my computer it is the f2 key immediately at powering on, yours may be different.

Is XP booting straight in right now?

---

### Post by threestripebrand on 2010-12-22
well the grub option is there now for windows and ubuntu havent tried it yet though, i figured i might get part 2 done first. off to try f2.  fingers crossed

---

### Post by threestripebrand on 2010-12-22
okay mines is the f2 key also. i went to boot sequence and only have 3 choices, diskette,ide cdrom device and hard disk drive C: what should i do?

---

### Post by wilee-nilee on 2010-12-22
> **threestripebrand said:**
> well the grub option is there now for windows and ubuntu havent tried it yet though, i figured i might get part 2 done first. off to try f2.  fingers crossed

You might be reading the sdb first if it is actual grub. You have a wubi remnants in the MS boot line. 
Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM **/wubildr.mbr /wubildr**

Are you sure you're seeing grub? Could it be the MS boot choice screen.

There is also a per-session boot from menu choice, that is good to know when you have two HD and separate bootloaders in their own mbr's, this would allow you to boot straight into MS without using grub if needed. Mine is f12, if you boot the live Ubuntu cd generally or the computer it tells on the screen the bios key and the boot menu key goes by fast though, if its there.:)

You can just look up per-session boot with the computer model on Google to get that info as well.  You have a bit of a franken-build but the prompt keys are part of the bios and/or motherboard in some manner I believe.

---

### Post by wilee-nilee on 2010-12-22
So if you boot it what does it do? Can you boot into Ubuntu and is it the grub menu?

---

### Post by threestripebrand on 2010-12-22
okay mines is the f2 key also. i went to boot sequence and only have 3 choices, diskette,ide cdrom device and hard disk drive C: what should i do? well i'm thinking its not grub, i think its msboot

---

### Post by wilee-nilee on 2010-12-22
if you just power it on and don't touch any keys what menu comes up a windows type or boots straight to windows, or a actual grub menu? If you see a grub menu try to boot into Ubuntu and if you get in trun in the terminal.
sudo update-grub

Take a look at my post on the per-session boot, you hit a different key just like you would for going to the bios and a post bios boot from menu comes up, see if you see 2 HD there, choose and see what boots. My per-session key is f12.

---

### Post by threestripebrand on 2010-12-22
the per session didnt have the extra drive. just diskette,hard disk, cd rom device and normal. the boot up screen gives me 2 optoins,xp or ubuntu. xp works. when i select ubuntu it gives me the minimal bash - like ..... grub> boot      says no loaded kernel     grub> linux       no kernel specified.

---

### Post by wilee-nilee on 2010-12-22
> **threestripebrand said:**
> the per session didnt have the extra drive. just diskette,hard disk, cd rom device and normal. **the boot up screen** gives me 2 optoins,xp or ubuntu. xp works. when i select ubuntu it gives me the minimal bash - like ..... grub> boot      says no loaded kernel     grub> linux       no kernel specified.

I think the way it's setup is the problem the Ubuntu probably should have just been dual booted up next to XP. The grub bootloader would work fine then I think. If its only showing one HD for booting you will need a bootloader in that HD that will read both; Grub is what I would use.

The highlighted part of your text do you know what the grub boot screen looks like? and what screen are you seeing for a choice of XP or Ubuntu? MS or Grub?

---

### Post by oldfred on 2010-12-22
wilee-nilee is correct that you need to have grub installed to the drive you boot.

We are used to the newer BIOS, that work with SATA drives and give choices in the BIOS on which drive to boot. 

Old IDE drives would only boot the primary master, which was selected with jumpers on the hard drive or cable select with 80 wire cable and location on cable determined primary master. BIOS was just smart enough to boot the one hard drive - primary master, floppy or CD. Usually no other devices were supported back with those system.

---

### Post by threestripebrand on 2010-12-23
well i thank you guys for all the help and info, also thank you for your patience. i'm going to go run it beside xp and if thats a success then i'll make sure to mark this as solved. thanks again.

---

### Post by threestripebrand on 2010-12-23
well i decided to do a little more investigating and noticed in the "f2" menu that there was a "primary 0" and a "primary 1" drive and C: was in 0 and nothing in 1. so i changed to it auto and after a reboot it has c: in 0 and d: in 1. off to experiment! :)

---

### Post by threestripebrand on 2011-01-06
dumped windows completely

---

