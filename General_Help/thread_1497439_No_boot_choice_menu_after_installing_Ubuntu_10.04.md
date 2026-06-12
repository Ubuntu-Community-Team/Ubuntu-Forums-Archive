---
title: "No boot choice menu after installing Ubuntu 10.04"
date: 2010-05-30
forum: General Help
---

### Post by rizameister on 2010-05-30
Hi all. I have an issue. I had 1TB drive with Windows 7 on it. Before installing Ubuntu I have made the partition of 100GB's for Ubuntu, and installed Ubuntu 10.04 on it - through option "Use Largest Continuous Free Space". The installation finished ok. But when I restarted my PC there was no boot choice menu between Windows 7/Ubuntu 10.04. Just loading Windows 7 like Ubuntu isn't installed. Please help me, how to get boot menu when starting PC. Thanks

---

### Post by r_s on 2010-05-30
boot a live cd  and post the output of sudo fdisk -l

---

### Post by ibuclaw on 2010-05-30
If GRUB installed OK, you hold down the SHIFT key to show the menu.
If GRUB didn't, then it will need installing.

Regards
Iain

---

### Post by rizameister on 2010-05-30
> **r_s said:**
> boot a live cd  and post the output of sudo fdisk -l

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0a21a442

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       77825   625121280    f  W95 Ext'd (LBA)
/dev/sda5               2       77825   625121248+   7  HPFS/NTFS

Disk /dev/sdb: 16.2 GB, 16173236224 bytes
255 heads, 63 sectors/track, 1966 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1967    15794144+   c  W95 FAT32 (LBA)

Disk /dev/sdc: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb9a2b9a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      108488   871428836    7  HPFS/NTFS
/dev/sdc2          108489      121602   105330689    5  Extended
/dev/sdc5          108489      121063   101004288   83  Linux
/dev/sdc6          121063      121602     4325376   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

> **ibuclaw said:**
> If GRUB installed OK, you hold down the SHIFT key to show the menu.
If GRUB didn't, then it will need installing.

Regards
Iain
Nothing happens, how to install GRUB?

---

### Post by r_s on 2010-05-30
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
Go to  "Recover Grub2 via LiveCD"
and change the partitions accordingly , in your case sdc instead of sda.

---

### Post by ibuclaw on 2010-05-30
> **rizameister said:**
> ```

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      108488   871428836    7  HPFS/NTFS
/dev/sdc2          108489      121602   105330689    5  Extended
/dev/sdc5          108489      121063   101004288   83  Linux
/dev/sdc6          121063      121602     4325376   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```


What happens if you try to boot off the third disk?

---

### Post by rizameister on 2010-05-30
> **ibuclaw said:**
> What happens if you try to boot off the third disk?
BIOS is set to boot from the third disk (Both Windows 7 and Ubuntu are on this disk), and nothing happens, no boot menu. Immediately loading Windows ...

---

### Post by r_s on 2010-05-30
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) use this script and post its output

---

### Post by rizameister on 2010-05-30
> **r_s said:**
> [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) use this script and post its output
This is the output:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         16,065 1,250,258,624 1,250,242,560   f W95 Ext d (LBA)
/dev/sda5              16,128 1,250,258,624 1,250,242,497   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.2 GB, 16173236224 bytes
255 heads, 63 sectors/track, 1966 cylinders, total 31588352 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    31,588,351    31,588,289   c W95 FAT32 (LBA)


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048 1,742,859,719 1,742,857,672   7 HPFS/NTFS
/dev/sdc2       1,742,860,286 1,953,521,663   210,661,378   5 Extended
/dev/sdc5       1,742,860,288 1,944,868,863   202,008,576  83 Linux
/dev/sdc6       1,944,870,912 1,953,521,663     8,650,752  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: PTTYPE="dos" 
/dev/sda5        01C9A81D49F59900                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C4E6-6D78                              vfat       RIZAMEISTER                   
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        C6D26EF0D26EE3E1                       ntfs                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        e831a7ba-bb7c-41e2-98b7-69b08ec74563   ext4                                     
/dev/sdc6        0dc9dc2e-3384-4fc7-8dab-6863399d781f   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/RIZAMEISTER       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdc5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set e831a7ba-bb7c-41e2-98b7-69b08ec74563
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set e831a7ba-bb7c-41e2-98b7-69b08ec74563
set locale_dir=($root)/boot/grub/locale
set lang=hr
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set e831a7ba-bb7c-41e2-98b7-69b08ec74563
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=e831a7ba-bb7c-41e2-98b7-69b08ec74563 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set e831a7ba-bb7c-41e2-98b7-69b08ec74563
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=e831a7ba-bb7c-41e2-98b7-69b08ec74563 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set e831a7ba-bb7c-41e2-98b7-69b08ec74563
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set e831a7ba-bb7c-41e2-98b7-69b08ec74563
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set c6d26ef0d26ee3e1
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=e831a7ba-bb7c-41e2-98b7-69b08ec74563 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=0dc9dc2e-3384-4fc7-8dab-6863399d781f none            swap    sw              0       0

=================== sdc5: Location of files loaded by Grub: ===================


 918.2GB: boot/grub/core.img
 954.9GB: boot/grub/grub.cfg
 918.2GB: boot/initrd.img-2.6.32-21-generic
 918.2GB: boot/vmlinuz-2.6.32-21-generic
 918.2GB: initrd.img
 918.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  2f 81 87 6e c2 ef cd d4  18 0b 83 9c 54 74 2a 02  |/..n........Tt*.|
00000010  95 ea 22 91 70 59 ad fe  32 c7 e5 00 21 30 28 0e  |..".pY..2...!0(.|
00000020  16 17 e8 12 e0 06 cc 32  25 05 3f 7e a8 76 18 16  |.......2%.?~.v..|
00000030  1d 2e f0 d8 fa aa d1 d2  07 d9 88 a8 2a d5 f3 74  |............*..t|
00000040  4c c5 c5 24 d4 33 18 ae  2b 2a 11 ee 11 0a 41 26  |L..$.3..+*....A&|
00000050  b4 5f 95 e2 17 60 9a 81  1f 85 70 dd a3 2a b7 d3  |._...`....p..*..|
00000060  fd 3b a3 1a 04 42 96 d7  5f 7e 64 28 80 49 45 e2  |.;...B.._~d(.IE.|
00000070  bf 78 2a aa b1 30 08 5a  01 e0 39 16 e7 ba 63 1d  |.x*..0.Z..9...c.|
00000080  60 b7 f9 be cd 3d 01 5d  6c ec 3c 42 e4 8a 73 be  |`....=.]l.<B..s.|
00000090  9c 38 ca b9 ff e2 8b 50  56 3e 67 e2 09 8e 38 03  |.8.....PV>g...8.|
000000a0  90 01 f9 26 ce a5 18 85  2e 73 fe 8c 0d cb 44 98  |...&.....s....D.|
000000b0  42 8a 6e 92 3b bc 87 29  0c 41 26 5d 1e e6 0e 01  |B.n.;..).A&]....|
000000c0  88 c0 65 28 97 23 10 a1  09 5d 18 43 ce 11 01 90  |..e(.#...].C....|
000000d0  24 0e 92 94 74 f3 23 09  0a 24 c8 dc c6 c7 e4 e3  |$...t.#..$......|
000000e0  43 a6 33 ff c9 03 31 9c  3a 32 74 49 5e 39 38 e7  |C.3...1.:2tI^98.|
000000f0  ca e2 c6 42 f2 80 aa 6c  4e 4e f3 29 df e0 97 4f  |...B...lNN.)...O|
00000100  38 30 1d 4f 10 73 4b 82  e7 09 e8 e4 9f e7 73 6f  |80.O.sK.......so|
00000110  fe e0 66 07 43 61 b4 9e  87 94 71 d3 c3 83 4c e2  |..f.Ca....q...L.|
00000120  ec bf d2 eb c1 3e 7c d7  a1 05 a5 c7 33 e1 51 0f  |.....>|.....3.Q.|
00000130  00 78 be db eb d3 f2 94  af 60 e0 7c f2 b1 09 fb  |.x.......`.|....|
00000140  8d 20 80 d2 ec a4 87 25  3e 2e cf c0 68 2d 3f 9c  |. .....%>...h-?.|
00000150  ef 9a 70 e4 28 2f d0 a9  95 9f 33 63 01 0d 1e 0f  |..p.(/....3c....|
00000160  4b 32 58 70 e2 7b 0e 3d  48 ce 10 2a f3 e9 7e 7e  |K2Xp.{.=H..*..~~|
00000170  bd 31 5c 67 3b e9 00 ff  18 ee f8 21 80 24 99 bd  |.1\g;......!.$..|
00000180  70 b7 8b 5e 5f 13 74 c4  73 60 cf 51 48 e5 3f 63  |p..^_.t.s`.QH.?c|
00000190  3e cf cf dc f3 ee 96 10  e9 c7 c1 fa 19 e0 74 96  |>.............t.|
000001a0  24 dc 7c 3e f3 04 bb 1d  14 11 01 9f a7 f9 53 cd  |$.|>..........S.|
000001b0  47 6f b7 e3 69 30 d0 7b  8a f3 44 37 70 fa 00 fe  |Go..i0.{..D7p...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 68 0a 0c 00 fe  |...........h....|
000001d0  ff ff 05 fe ff ff 02 68  0a 0c 00 08 84 00 00 00  |.......h........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by r_s on 2010-05-30
>>Windows is installed in the MBR of /dev/sdc

>>BIOS is set to boot from the third disk (Both Windows 7 and Ubuntu are  on this disk), and nothing happens, no boot menu. Immediately loading  Windows ...

Just install grub for your third disk and then try booting through it.

---

### Post by rizameister on 2010-05-30
> **r_s said:**
> >>Windows is installed in the MBR of /dev/sdc

>>BIOS is set to boot from the third disk (Both Windows 7 and Ubuntu are  on this disk), and nothing happens, no boot menu. Immediately loading  Windows ...

Just install grub for your third disk and then try booting through it.

which commands? i have a clue, but please tell me because i don't want to switch between os-es so many times. thank you

---

### Post by r_s on 2010-05-30
> **r_s said:**
> [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
Go to  "Recover Grub2 via LiveCD"
and change the partitions accordingly , in your case sdc instead of sda.

sudo mount /dev/sda1 /mnt

in your case /dev/sda1 refers to /dev/sdc5
then 
$ sudo mount --bind /dev /mnt/dev
 $ sudo mount --bind /proc /mnt/proc
 $ sudo mount --bind /sys /mnt/sys
$ sudo chroot /mnt
$ nano /etc/default/grub
$ update-grub
$ grub-install /dev/sdc
$ grub-install --recheck /dev/sdc

I think that does it , press ctrl-D to get out of chroot and unmount.
and for mapping to other drives using MBR of /dev/sdc this might be helpful
[http://ubuntuforums.org/showthread.php?t=664401](http://ubuntuforums.org/showthread.php?t=664401)

---

### Post by rizameister on 2010-05-30
> **r_s said:**
> sudo mount /dev/sda1 /mnt

in your case /dev/sda1 refers to /dev/sdc5
then 
$ sudo mount --bind /dev /mnt/dev
 $ sudo mount --bind /proc /mnt/proc
 $ sudo mount --bind /sys /mnt/sys
$ sudo chroot /mnt
$ nano /etc/default/grub
$ update-grub
$ grub-install /dev/sdc
$ grub-install --recheck /dev/sdc

I think that does it , press ctrl-D to get out of chroot and unmount.
and for mapping to other drives using MBR of /dev/sdc this might be helpful
[http://ubuntuforums.org/showthread.php?t=664401](http://ubuntuforums.org/showthread.php?t=664401)
That worked!! Thank you very much, but one question. Why this 5 choices, I dont need lines 2, 3 and 4 ...
[IMG]http://img411.imageshack.us/img411/6546/dsc00995ci.jpg[/IMG]

---

### Post by drs305 on 2010-05-30
> **rizameister said:**
> That worked!! Thank you very much, but one question. Why this 5 choices, I dont need lines 2, 3 and 4 ...
[IMG]http://img411.imageshack.us/img411/6546/dsc00995ci.jpg[/IMG]

The second choice is the recovery mode. It is useful if you need to boot into your system when you have troubles. Think of it as a "safe" mode and as insurance. If you don't want it, you don't have to have it but may wish you did some day. However, there are ways to enter the recovery mode without having the menu entry - by manually editing the Grub2 menu during boot. 

You can disable it by opening /etc/default/grub:
```
gksu gedit /etc/default/grub
```

Change:
```
[COLOR="Red"]**#**[/COLOR] GRUB_DISABLE_LINUX_RECOVERY="true"
```
To:
```
GRUB_DISABLE_LINUX_RECOVERY="true"
```

Options 3 & 4 are memory test functions which usually aren't necessary. You disable them by making the script un-executable with this command:
```
sudo chmod -x /etc/grub.d/20_memtest86+
```

After you make the changes you want, update the Grub 2 menu with this command:
```
sudo update-grub
```

---

### Post by rizameister on 2010-05-30
> **drs305 said:**
> The second choice is the recovery mode. It is useful if you need to boot into your system when you have troubles. Think of it as a "safe" mode and as insurance. If you don't want it, you don't have to have it but may wish you did some day. However, there are ways to enter the recovery mode without having the menu entry - by manually editing the Grub2 menu during boot. 

You can disable it by opening /etc/default/grub:
```
gksu gedit /etc/default/grub
```

Change:
```
[COLOR="Red"]**#**[/COLOR] GRUB_DISABLE_LINUX_RECOVERY="true"
```
To:
```
GRUB_DISABLE_LINUX_RECOVERY="true"
```

Options 3 & 4 are memory test functions which usually aren't necessary. You disable them by making the script un-executable with this command:
```
sudo chmod -x /etc/grub.d/20_memtest86+
```

After you make the changes you want, update the Grub 2 menu with this command:
```
sudo update-grub
```

Great, thank you for all your help!
PS One more irrelevant question to ask - Why GRUB wasn't installed automatically with the system, or can it be installed automatically, just to know for the next time. Is it my mistake to choose "Continuous Free Space installation" except Side-by-Side because it clearly sais in SBS installation "Install them side by side, CHOOSING BETWEEN EACH at startup", not such a thing have been written in Continuous Free Space installation. Sorry for bothering. Thanks

---

### Post by drs305 on 2010-05-30
> **rizameister said:**
> Great, thank you for all your help!
PS One more irrelevant question to ask - Why GRUB wasn't installed automatically with the system, or can it be installed automatically, just to know for the next time. Is it my mistake to choose "Continuous Free Space installation" except Side-by-Side (info for SBS - "Install them side by side, choosing between each at startup"). Thanks

It is not normal behavior to leave Grub2 uninstalled. That option should only be available in one of the last steps, under the "Advanced" tab. 

I have not used the "Side-by-Side" or "Largest contiguous space" options since a bug in Jaunty produced problems for users and I had to do some testing. I haven't seen reports of Grub2 installation failure being a problem with Lucid with these options, but I will keep watching and also search the bug reports. If I find a problem, I'll post here.

---

