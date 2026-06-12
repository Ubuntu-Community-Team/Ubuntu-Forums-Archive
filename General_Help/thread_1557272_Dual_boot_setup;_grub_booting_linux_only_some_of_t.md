---
title: "Dual boot setup; grub booting linux only some of the time"
date: 2010-08-20
forum: General Help
---

### Post by rawlins02 on 2010-08-20
I'm not consistently able to boot into Ubuntu Lucid on my new dual boot (w/ Win7) setup. Machine is a Dell XPS 1645 laptop.  Usually it takes 1-3 tries of hard shut down and restart before the OS starts up.  Boot info script results are below. Windows starts up fine everytime. What I usually get is this:  Dell startup screen, then Grub2 menu, then after selecting Linux kernal a blinking cursor at upper left of monitor and it just hangs.  I've just disabled quiet splash and see that on last attempt bootup hung after a line that says:  214140 pages non-shared

I'm considering reinstalling Grub2 but thought I'd post this first. I see these boot issues with blinking cursor are not uncommon with Lucid and Grub2.  If all is well with the boot script, should I reinstall Grub2 from LiveCD?  Other suggestions?  TIA.

```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1         163,846,935   327,693,869   163,846,935   7 HPFS/NTFS
/dev/sda2    *             63   163,846,934   163,846,872   7 HPFS/NTFS
/dev/sda3         327,693,931   976,773,119   649,079,189   5 Extended
/dev/sda5         327,693,933   335,887,019     8,193,087  82 Linux swap / Solaris
/dev/sda6         947,476,480   976,773,119    29,296,640  83 Linux
/dev/sda7         918,169,600   947,466,239    29,296,640  83 Linux
/dev/sda8         335,888,384   918,163,455   582,275,072  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4844D2BA0BBDF06D                       ntfs                                     
/dev/sda2        F48A04028A03BFDA                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        42c7f179-a9d2-4cb7-8f89-601984ae7dcb   swap                                     
/dev/sda6        d530bdac-3e1d-4f6c-9ce9-5a0438da4ab9   ext4                                     
/dev/sda7        bde9cb90-6e16-4cdc-b443-6c76a032a354   ext4                                     
/dev/sda8        0d960a51-c446-403b-9e4b-0ba39bca61b4   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /usr                     ext4       (rw)
/dev/sda8        /home                    ext4       (rw)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set bde9cb90-6e16-4cdc-b443-6c76a032a354
if loadfont /share/grub/unicode.pf2 ; then
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set d530bdac-3e1d-4f6c-9ce9-5a0438da4ab9
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d530bdac-3e1d-4f6c-9ce9-5a0438da4ab9
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=d530bdac-3e1d-4f6c-9ce9-5a0438da4ab9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d530bdac-3e1d-4f6c-9ce9-5a0438da4ab9
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=d530bdac-3e1d-4f6c-9ce9-5a0438da4ab9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d530bdac-3e1d-4f6c-9ce9-5a0438da4ab9
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=d530bdac-3e1d-4f6c-9ce9-5a0438da4ab9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d530bdac-3e1d-4f6c-9ce9-5a0438da4ab9
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=d530bdac-3e1d-4f6c-9ce9-5a0438da4ab9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d530bdac-3e1d-4f6c-9ce9-5a0438da4ab9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set d530bdac-3e1d-4f6c-9ce9-5a0438da4ab9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set f48a04028a03bfda
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=d530bdac-3e1d-4f6c-9ce9-5a0438da4ab9 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=0d960a51-c446-403b-9e4b-0ba39bca61b4 /home           ext4    defaults        0       2
# /usr was on /dev/sda7 during installation
UUID=bde9cb90-6e16-4cdc-b443-6c76a032a354 /usr            ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=42c7f179-a9d2-4cb7-8f89-601984ae7dcb none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 487.4GB: boot/grub/core.img
 488.1GB: boot/grub/grub.cfg
 487.5GB: boot/initrd.img-2.6.32-21-generic
 488.2GB: boot/initrd.img-2.6.32-24-generic
 487.5GB: boot/vmlinuz-2.6.32-21-generic
 488.2GB: boot/vmlinuz-2.6.32-24-generic
 488.2GB: initrd.img
 487.5GB: initrd.img.old
 488.2GB: vmlinuz
 487.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 3f 04 7d 00 00 fe  |..........?.}...|
000001d0  ff ff 05 fe ff ff 95 f9  f0 24 00 30 bf 01 00 00  |.........$.0....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by Rubi1200 on 2010-08-20
I was wondering about this:

> /dev/sda6 [COLOR=Red]947,476,480[/COLOR]   976,773,119 [COLOR=Red]   29,296,640 [COLOR=Black] 83[/COLOR][/COLOR] Linux
/dev/sda7         [COLOR=Red]918,169,600[/COLOR]   947,466,239    [COLOR=Red]29,296,640 [COLOR=Black] 83[/COLOR][/COLOR] Linux
/dev/sda8         [COLOR=Red]335,888,384[/COLOR]   918,163,455[COLOR=Red]   582,275,072[/COLOR]  83 Linux

This might also be a graphics card issue; what do you have installed?

Thanks.

---

### Post by oldfred on 2010-08-20
It may be related to having /usr as a separate partition. Someone in the last week posted about a bug where he wanted some system folders on separate partitions and had issues. Not sure if it was /usr or another folder.

---

### Post by rawlins02 on 2010-08-20
Graphics card is ATI Mobility Radeon 4670. Driver is the ATI Catalyst fglrx installed from Synaptic.                  

Sure hope putting /usr on a separate partition is not the cause.  Got a lot of software already installed and prefer not to have to do a fresh install.  And these multiple reboots is getting old fast...

---

### Post by hal8000 on 2010-08-20
How much space is left on / and /usr ?
Can you post output of

df -h


I use XFX HD5770 Radeon and catalyst driver from restricted modules.
However I use a ext4 / partition assigned 10G and ext4 /home assigned 20G.
This could be partition related is space is low.

---

### Post by rawlins02 on 2010-08-20
> 
How much space is left on / and /usr ?
Can you post output of

df -h


I use XFX HD5770 Radeon and catalyst driver from restricted modules.
However I use a ext4 / partition assigned 10G and ext4 /home assigned 20G.
This could be partition related is space is low. 


I don't believe lack of space is an issue:

```

> df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              14G  1.6G   12G  12% /
none                  1.6G  328K  1.6G   1% /dev
none                  1.6G  260K  1.6G   1% /dev/shm
none                  1.6G   92K  1.6G   1% /var/run
none                  1.6G     0  1.6G   0% /var/lock
none                  1.6G     0  1.6G   0% /lib/init/rw
/dev/sda8             274G   23G  237G   9% /home
/dev/sda7              14G  3.4G  9.8G  26% /usr


```

---

### Post by hal8000 on 2010-08-20
Space looks ok, but Rubi caught sight of something:

/dev/sda6 947,476,480 976,773,119  29,296,640  83 Linux
/dev/sda7 918,169,600 947,466,239 29,296,640 83 Linux
/dev/sda8 335,888,384 918,163,455 582,275,072 83 Linux

Looks as though the partition table is not in order.
Can you post

sudo fdisk /dev/sda

(then press u to change units to cylinders, not sectors)

Press p to display partition table and post that please.

---

### Post by rawlins02 on 2010-08-20
OK. So I've been wondering about the Windows partitions since I did the installation.  When I set the first two partitions in gparted, I intended for the bootable Windows (OS) partition to be the first one.  But it appears that the Windows 7 went to /dev/sda2.  /dev/sda1 is my data NTFS partition.  Could this be causing problems when I boot linux?


```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3ae23d76

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       163846935   327693869    81923467+   7  HPFS/NTFS
/dev/sda2   *          63   163846934    81923436    7  HPFS/NTFS
/dev/sda3       327693931   976773119   324539594+   5  Extended
/dev/sda5       327693933   335887019     4096543+  82  Linux swap / Solaris
/dev/sda6       947476480   976773119    14648320   83  Linux
/dev/sda7       918169600   947466239    14648320   83  Linux
/dev/sda8       335888384   918163455   291137536   83  Linux

Partition table entries are not in disk order



```

---

### Post by rawlins02 on 2010-08-23
After a few more tests, it seems that the boot problem is more common after coming out of Windows.

It is my understanding that the problems with booting should not be related to table entries not in disk order. This goes for /dev/sda6 to /devsda8 (linux) AND /dev/sda2, where Windows 7 exists on the econd partition that is located at beginning of the drive. In other words, my partition table is fine.  

I'm hoping that re-installing Grub might fix the problem.  Could someone confirm that this is the right way to re-install for my dual boot system?  Or is there another method?  

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", or whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

I'm assuming that this will put GRUB back on the MBR (master boot record) of the hard drive instead of in the root partition.

I've also seen mention of re-installing with grub-install:

sudo grub-install --root-directory=/media/Zino-root /dev/sda
sudo update-grub

---

### Post by Rubi1200 on 2010-08-23
Personally, I think this method is the easiest way to reinstall GRUB:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Hope this helps.

---

### Post by oldfred on 2010-08-23
Follow Rubi1200's link for instructions.

rawlins02 the steps you posted are for grub legacy and not for grub2.
Only if booted can you directly use grub-install, from liveCD you have to mount the Ubuntu partition first.

---

### Post by rawlins02 on 2010-08-23
I've reinstalled Grub. The anomaly is still there. After installing grub from the LiveCD I clicked restart (still in LiveCD) and, interestingly, got a black screen. No reboot. So did a hard shutdown.  I was then able to hit power button and Ubuntu booted fine. Then restarted and chose Windows. It booted fine. Restarted again and this time it hung when I allowed it to go into Ubuntu (after countdown expires). Using the dmesg command I've locate where it hangs, right after the line "214235 pages non-shared" and before "Adding 4096532k swap on /dev/sda5...."


I've seen posts where it was mentioned that Windows 7 somehow corrupts Grub.  Will have to look closer into this. Although perhaps not a major issue I think in the long run I'd find this behavior to be troublesome.


```

[    4.604480] 958 total pagecache pages
[    4.604531] 0 pages in swap cache
[    4.604575] Swap cache stats: add 0, delete 0, find 0/0
[    4.604623] Free swap  = 0kB
[    4.604667] Total swap = 0kB
[    4.608704] 817152 pages RAM
[    4.608750] 589826 pages HighMem
[    4.608795] 13461 pages reserved
[    4.608840] 453 pages shared
[    4.608884] 214235 pages non-shared
[    5.025049] Adding 4096532k swap on /dev/sda5.  Priority:-1 extents:1 across:4096532k 
[    5.231883] udev: starting version 151
[    5.436509] type=1505 audit(1282584777.761:2):  operation="profile_load" pid=670 name="/sbin/dhclient3"
[    5.437031] type=1505 audit(1282584777.761:3):  operation="profile_load" pid=670 name="/usr/lib/NetworkManager/nm-dhcp-client.action"


```

---

### Post by rawlins02 on 2010-08-24
After a few more tests the problem reoccurs after a boot to Windows. I've restarted to Lucid and shutdown/restarted to Lucid several times with no hangup.  There's been discussion of a bug whereby Grub must be reinstalled after a boot to Windows:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

This is not the case with me, as I'm able to start (repair...) through a hard shutdown and restart.  Interestingly, another user with the same machine (Dell XPS 1645) had hangups at the same place in boot sequence:

[http://ubuntuforums.org/showthread.php?t=1478053&page=2](http://ubuntuforums.org/showthread.php?t=1478053&page=2)

see posts 13 and 14.  Although not certain, I understand that this issue may be related to the size of Grub2 (larger than Grub legacy) that gets written to the MBR.  Not solved yet.

---

### Post by oldfred on 2010-08-24
Dell's with windows 7 have some software that writes into the MBR. The MBR is reserved for booting but they want to write a serial number or other hidden data into the MBR and because grub2 uses a little more of the MBR than windows or old grub the Dell/Windows software corrupts grub2.

Writes to MBR-----------------------------------
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)
h

---

### Post by rawlins02 on 2010-08-25
I've now been able to restart under linux several times. Windows must be causing the problem.

Just after installing Windows 7 I removed Dell DataSafe Local Backup, which has often been cited as a culprit.  I'll follow the guidance on solutions in the sourceforge link for determining if another Windows program is writing to the MBR. If I can't identify another program, then perhaps (i) reverting to Legacy Grub or (ii) using a different boot loader in the MBR will fix this issue.

---

