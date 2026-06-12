---
title: "Ubuntu updates killed GRUB"
date: 2010-08-09
forum: General Help
---

### Post by five0xpres on 2010-08-09
I've been a Windows users since waaaay back when (ahh...Windows for Workgroups 3.1). I've tried Linux in the past (Mandrake many years ago), but didn't feel it was quite ready to be a Windows substitute for me.
 
A couple of weeks ago, I downloaded the latest version of Ubuntu (10.04) and installed it in a dual boot setup with Windows XPSP3. All seemed to be running well, until it came time to install updates in the Update Manager. First an update for GRUB, which promptly killed GRUB and left me with "Minimal BASH-like line editing is supported" message and a GRUB prompt. After booting up the Windows XP install CD, I was able to rewrite the MBR and get back into Windows. I deleted the Ubuntu installation and reinstalled it, making sure I didn't allow it to update GRUB after finishing up. The other updates listed installed fine and I was able to dual boot with ease.
 
Another round of updates were listed yesterday when I booted up in Ubuntu, I made sure not to include the GRUB update, downloaded and installed them, rebooted and was faced with "Minimal BASH-like line editing is supported" again. Argh. Once again I had to pull out the Windows CD and run FIXMBR to resolve the boot problem.
 
I'll admit to being tempted to just go back to Windows completely (while not perfect, atleast I can get it to boot after updates 99.9% of the time) and forget the idea of running Linux if I'm going to be faced with having to reinstall the OS everytime because something killed the boot loader. :frown:

---

### Post by john newbuntu on 2010-08-09
Welcome to the forums five0xpres.

To help you with your problem, download and run the boot info script courtesy of our forum member meierfra. Open a browser window and go to: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instructions on this page to download and run the boot_info_script.  Post the output using code tags.  Someone here will help you diagnose your problem.

---

### Post by five0xpres on 2010-08-09
output as requested:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   201,915,783   201,915,721   7 HPFS/NTFS
/dev/sda2         201,916,414   312,580,095   110,663,682   5 Extended
/dev/sda5         201,916,416   308,086,783   106,170,368  83 Linux
/dev/sda6         308,088,832   312,580,095     4,491,264  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        DAC8060FC805EB19                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        e89cdf8a-1ccc-459a-8960-38af729961cf   ext4                                     
/dev/sda6        d5b210e1-4f78-44f5-ab25-9a25444aca81   swap                                     
/dev/sda: PTTYPE="dos" 

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

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e89cdf8a-1ccc-459a-8960-38af729961cf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e89cdf8a-1ccc-459a-8960-38af729961cf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e89cdf8a-1ccc-459a-8960-38af729961cf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e89cdf8a-1ccc-459a-8960-38af729961cf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set dac8060fc805eb19
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=e89cdf8a-1ccc-459a-8960-38af729961cf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d5b210e1-4f78-44f5-ab25-9a25444aca81 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 125.0GB: boot/grub/core.img
 141.9GB: boot/grub/grub.cfg
 121.7GB: boot/initrd.img-2.6.32-21-generic
 125.4GB: boot/initrd.img-2.6.32-24-generic
 103.5GB: boot/vmlinuz-2.6.32-21-generic
 125.3GB: boot/vmlinuz-2.6.32-24-generic
 125.4GB: initrd.img
 121.7GB: initrd.img.old
 125.3GB: vmlinuz
 103.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  75 ec 89 75 f0 89 75 f8  89 75 e0 75 0c c7 45 fc  |u..u..u..u.u..E.|
00000010  57 00 07 80 e9 b5 02 00  00 8d 45 e8 50 68 3f 00  |W.........E.Ph?.|
00000020  0f 00 ff 75 0c e8 93 df  fb ff 85 c0 74 0c c7 45  |...u........t..E|
00000030  fc 05 40 00 80 e9 3a 02  00 00 56 8d 45 f4 50 56  |..@...:...V.E.PV|
00000040  68 d8 f1 33 60 ff 75 e8  e8 8e 02 00 00 3b c6 89  |h..3`.u......;..|
00000050  45 fc 7d 16 39 75 f4 74  11 a1 14 37 46 60 ff 75  |E.}.9u.t...7F`.u|
00000060  f4 8b 08 50 ff 51 14 89  75 f4 53 57 8b 3d 28 10  |...P.Q..u.SW.=(.|
00000070  33 60 6a 04 5b 8d 45 dc  50 8d 45 e4 50 56 56 68  |3`j.[.E.P.E.PVVh|
00000080  e0 f1 33 60 ff 75 e8 89  5d dc ff d7 85 c0 75 44  |..3`.u..].....uD|
00000090  39 75 e4 89 5d dc 0f 94  c0 bb ac ca 33 60 89 45  |9u..].......3`.E|
000000a0  d8 8d 45 dc 50 8d 45 e4  50 56 56 53 ff 75 e8 ff  |..E.P.E.PVVS.u..|
000000b0  d7 3b c6 74 2b 83 f8 02  75 1a 6a 04 8d 45 e4 50  |.;.t+...u.j..E.P|
000000c0  6a 04 56 53 ff 75 e8 89  75 e4 ff 15 3c 10 33 60  |j.VS.u..u...<.3`|
000000d0  85 c0 74 0c c7 45 fc 05  40 00 80 e9 92 01 00 00  |..t..E..@.......|
000000e0  8b 45 e4 8b 75 08 ff 75  0c 8b 3d e8 12 33 60 89  |.E..u..u..=..3`.|
000000f0  46 1c ff d7 68 e8 f1 33  60 8b d8 ff d7 8d 7c 18  |F...h..3`.....|.|
00000100  02 57 8d 45 f8 50 e8 7d  02 00 00 85 c0 0f 8c 5d  |.W.E.P.}.......]|
00000110  01 00 00 57 ff 75 0c ff  75 f8 ff 15 cc 12 33 60  |...W.u..u.....3`|
00000120  8b 45 0c 80 3c 03 5c 74  0f 57 68 88 cc 33 60 ff  |.E..<.\t.Wh..3`.|
00000130  75 f8 e8 e7 fe 08 00 43  57 68 e8 f1 33 60 ff 75  |u......CWh..3`.u|
00000140  f8 e8 d8 fe 08 00 8d 45  ec 50 e8 67 02 00 00 85  |.......E.P.g....|
00000150  c0 89 45 fc 0f 8c 16 01  00 00 8b 45 ec ff 75 f8  |..E........E..u.|
00000160  8b 08 50 ff 51 28 85 c0  89 45 fc 0f 8c ff 00 00  |..P.Q(...E......|
00000170  00 8b 45 ec 8b 08 8d 55  e0 52 50 ff 51 10 85 c0  |..E....U.RP.Q...|
00000180  89 45 fc 0f 8c e7 00 00  00 8b 46 0c 33 45 e0 2b  |.E........F.3E.+|
00000190  fb 25 00 00 ff 00 31 46  0c 8b 45 f8 57 68 f4 f1  |.%....1F..E.Wh..|
000001a0  33 60 03 d8 53 ff 15 cc  12 33 60 8d 45 f0 50 e8  |3`..S....3`.E.P.|
000001b0  1b 09 00 00 85 c0 89 45  fc 0f 8c b1 00 00 00 fe  |.......E........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 08 54 06 00 fe  |............T...|
000001d0  ff ff 05 fe ff ff 02 08  54 06 00 90 44 00 00 00  |........T...D...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by john newbuntu on 2010-08-09
I can't see anything wrong with the output.  Anyway, install GRUB2 to the MBR of /dev/sda.  Boot using the Ubuntu liveCD.  Fire up a terminal (applications->accessories->terminal) and run the following commands:

```
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
sudo grub-install --root-directory=/mnt /dev/sda --recheck
sudo grub-mkconfig -o /mnt/boot/grub/grub.cfg
sudo umount /mnt/dev
sudo umount /mnt
```This will overwrite your MBR with GRUB2.  Reboot and see if you can boot in using the GRUB2 menu to your latest kernel (2.6.32-24).
Once you boot in, run "sudo update-grub" just to keep grub.cfg up-to-date (paranoia).
I guess we will then have to wait till the next update to see if something breaks.

Also report any errors you get while doing this (or even otherwise)

---

### Post by five0xpres on 2010-08-09
Ran the commands listed.  Got a few errors but I also got "completed" messages.  Rebooted and was greeted with the GRUB boot menu, but it is now missing the option to boot into Windows XP.  Ran the update grub command and it listed the XP installation, but when I rebooted again to make sure it was added, it's still missing from the GRUB boot menu.

---

### Post by five0xpres on 2010-08-09
I re-ran the bootinfo script and here's the resulting output in case it's needed.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /mnt/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   201,915,783   201,915,721   7 HPFS/NTFS
/dev/sda2         201,916,414   312,580,095   110,663,682   5 Extended
/dev/sda5         201,916,416   308,086,783   106,170,368  83 Linux
/dev/sda6         308,088,832   312,580,095     4,491,264  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DAC8060FC805EB19                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        e89cdf8a-1ccc-459a-8960-38af729961cf   ext4                                     
/dev/sda6        d5b210e1-4f78-44f5-ab25-9a25444aca81   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/DAC8060FC805EB19  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e89cdf8a-1ccc-459a-8960-38af729961cf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e89cdf8a-1ccc-459a-8960-38af729961cf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e89cdf8a-1ccc-459a-8960-38af729961cf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e89cdf8a-1ccc-459a-8960-38af729961cf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set dac8060fc805eb19
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=e89cdf8a-1ccc-459a-8960-38af729961cf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d5b210e1-4f78-44f5-ab25-9a25444aca81 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 125.0GB: boot/grub/core.img
 144.0GB: boot/grub/grub.cfg
 121.7GB: boot/initrd.img-2.6.32-21-generic
 125.4GB: boot/initrd.img-2.6.32-24-generic
 103.5GB: boot/vmlinuz-2.6.32-21-generic
 125.3GB: boot/vmlinuz-2.6.32-24-generic
 125.4GB: initrd.img
 121.7GB: initrd.img.old
 125.3GB: vmlinuz
 103.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  75 ec 89 75 f0 89 75 f8  89 75 e0 75 0c c7 45 fc  |u..u..u..u.u..E.|
00000010  57 00 07 80 e9 b5 02 00  00 8d 45 e8 50 68 3f 00  |W.........E.Ph?.|
00000020  0f 00 ff 75 0c e8 93 df  fb ff 85 c0 74 0c c7 45  |...u........t..E|
00000030  fc 05 40 00 80 e9 3a 02  00 00 56 8d 45 f4 50 56  |..@...:...V.E.PV|
00000040  68 d8 f1 33 60 ff 75 e8  e8 8e 02 00 00 3b c6 89  |h..3`.u......;..|
00000050  45 fc 7d 16 39 75 f4 74  11 a1 14 37 46 60 ff 75  |E.}.9u.t...7F`.u|
00000060  f4 8b 08 50 ff 51 14 89  75 f4 53 57 8b 3d 28 10  |...P.Q..u.SW.=(.|
00000070  33 60 6a 04 5b 8d 45 dc  50 8d 45 e4 50 56 56 68  |3`j.[.E.P.E.PVVh|
00000080  e0 f1 33 60 ff 75 e8 89  5d dc ff d7 85 c0 75 44  |..3`.u..].....uD|
00000090  39 75 e4 89 5d dc 0f 94  c0 bb ac ca 33 60 89 45  |9u..].......3`.E|
000000a0  d8 8d 45 dc 50 8d 45 e4  50 56 56 53 ff 75 e8 ff  |..E.P.E.PVVS.u..|
000000b0  d7 3b c6 74 2b 83 f8 02  75 1a 6a 04 8d 45 e4 50  |.;.t+...u.j..E.P|
000000c0  6a 04 56 53 ff 75 e8 89  75 e4 ff 15 3c 10 33 60  |j.VS.u..u...<.3`|
000000d0  85 c0 74 0c c7 45 fc 05  40 00 80 e9 92 01 00 00  |..t..E..@.......|
000000e0  8b 45 e4 8b 75 08 ff 75  0c 8b 3d e8 12 33 60 89  |.E..u..u..=..3`.|
000000f0  46 1c ff d7 68 e8 f1 33  60 8b d8 ff d7 8d 7c 18  |F...h..3`.....|.|
00000100  02 57 8d 45 f8 50 e8 7d  02 00 00 85 c0 0f 8c 5d  |.W.E.P.}.......]|
00000110  01 00 00 57 ff 75 0c ff  75 f8 ff 15 cc 12 33 60  |...W.u..u.....3`|
00000120  8b 45 0c 80 3c 03 5c 74  0f 57 68 88 cc 33 60 ff  |.E..<.\t.Wh..3`.|
00000130  75 f8 e8 e7 fe 08 00 43  57 68 e8 f1 33 60 ff 75  |u......CWh..3`.u|
00000140  f8 e8 d8 fe 08 00 8d 45  ec 50 e8 67 02 00 00 85  |.......E.P.g....|
00000150  c0 89 45 fc 0f 8c 16 01  00 00 8b 45 ec ff 75 f8  |..E........E..u.|
00000160  8b 08 50 ff 51 28 85 c0  89 45 fc 0f 8c ff 00 00  |..P.Q(...E......|
00000170  00 8b 45 ec 8b 08 8d 55  e0 52 50 ff 51 10 85 c0  |..E....U.RP.Q...|
00000180  89 45 fc 0f 8c e7 00 00  00 8b 46 0c 33 45 e0 2b  |.E........F.3E.+|
00000190  fb 25 00 00 ff 00 31 46  0c 8b 45 f8 57 68 f4 f1  |.%....1F..E.Wh..|
000001a0  33 60 03 d8 53 ff 15 cc  12 33 60 8d 45 f0 50 e8  |3`..S....3`.E.P.|
000001b0  1b 09 00 00 85 c0 89 45  fc 0f 8c b1 00 00 00 fe  |.......E........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 08 54 06 00 fe  |............T...|
000001d0  ff ff 05 fe ff ff 02 08  54 06 00 90 44 00 00 00  |........T...D...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

EDIT:  I can't be without a way into Windows, so once again I ran FIXMBR from the Windows XP setup CD so I could boot up Windows.  So I went ahead and booted back into the LiveCD and re-ran the bootinfo script, including the current info:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   201,915,783   201,915,721   7 HPFS/NTFS
/dev/sda2         201,916,414   312,580,095   110,663,682   5 Extended
/dev/sda5         201,916,416   308,086,783   106,170,368  83 Linux
/dev/sda6         308,088,832   312,580,095     4,491,264  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        DAC8060FC805EB19                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        e89cdf8a-1ccc-459a-8960-38af729961cf   ext4                                     
/dev/sda6        d5b210e1-4f78-44f5-ab25-9a25444aca81   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/e89cdf8a-1ccc-459a-8960-38af729961cf ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e89cdf8a-1ccc-459a-8960-38af729961cf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e89cdf8a-1ccc-459a-8960-38af729961cf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e89cdf8a-1ccc-459a-8960-38af729961cf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e89cdf8a-1ccc-459a-8960-38af729961cf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e89cdf8a-1ccc-459a-8960-38af729961cf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set dac8060fc805eb19
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=e89cdf8a-1ccc-459a-8960-38af729961cf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d5b210e1-4f78-44f5-ab25-9a25444aca81 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 125.0GB: boot/grub/core.img
 137.9GB: boot/grub/grub.cfg
 121.7GB: boot/initrd.img-2.6.32-21-generic
 125.4GB: boot/initrd.img-2.6.32-24-generic
 103.5GB: boot/vmlinuz-2.6.32-21-generic
 125.3GB: boot/vmlinuz-2.6.32-24-generic
 125.4GB: initrd.img
 121.7GB: initrd.img.old
 125.3GB: vmlinuz
 103.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  75 ec 89 75 f0 89 75 f8  89 75 e0 75 0c c7 45 fc  |u..u..u..u.u..E.|
00000010  57 00 07 80 e9 b5 02 00  00 8d 45 e8 50 68 3f 00  |W.........E.Ph?.|
00000020  0f 00 ff 75 0c e8 93 df  fb ff 85 c0 74 0c c7 45  |...u........t..E|
00000030  fc 05 40 00 80 e9 3a 02  00 00 56 8d 45 f4 50 56  |..@...:...V.E.PV|
00000040  68 d8 f1 33 60 ff 75 e8  e8 8e 02 00 00 3b c6 89  |h..3`.u......;..|
00000050  45 fc 7d 16 39 75 f4 74  11 a1 14 37 46 60 ff 75  |E.}.9u.t...7F`.u|
00000060  f4 8b 08 50 ff 51 14 89  75 f4 53 57 8b 3d 28 10  |...P.Q..u.SW.=(.|
00000070  33 60 6a 04 5b 8d 45 dc  50 8d 45 e4 50 56 56 68  |3`j.[.E.P.E.PVVh|
00000080  e0 f1 33 60 ff 75 e8 89  5d dc ff d7 85 c0 75 44  |..3`.u..].....uD|
00000090  39 75 e4 89 5d dc 0f 94  c0 bb ac ca 33 60 89 45  |9u..].......3`.E|
000000a0  d8 8d 45 dc 50 8d 45 e4  50 56 56 53 ff 75 e8 ff  |..E.P.E.PVVS.u..|
000000b0  d7 3b c6 74 2b 83 f8 02  75 1a 6a 04 8d 45 e4 50  |.;.t+...u.j..E.P|
000000c0  6a 04 56 53 ff 75 e8 89  75 e4 ff 15 3c 10 33 60  |j.VS.u..u...<.3`|
000000d0  85 c0 74 0c c7 45 fc 05  40 00 80 e9 92 01 00 00  |..t..E..@.......|
000000e0  8b 45 e4 8b 75 08 ff 75  0c 8b 3d e8 12 33 60 89  |.E..u..u..=..3`.|
000000f0  46 1c ff d7 68 e8 f1 33  60 8b d8 ff d7 8d 7c 18  |F...h..3`.....|.|
00000100  02 57 8d 45 f8 50 e8 7d  02 00 00 85 c0 0f 8c 5d  |.W.E.P.}.......]|
00000110  01 00 00 57 ff 75 0c ff  75 f8 ff 15 cc 12 33 60  |...W.u..u.....3`|
00000120  8b 45 0c 80 3c 03 5c 74  0f 57 68 88 cc 33 60 ff  |.E..<.\t.Wh..3`.|
00000130  75 f8 e8 e7 fe 08 00 43  57 68 e8 f1 33 60 ff 75  |u......CWh..3`.u|
00000140  f8 e8 d8 fe 08 00 8d 45  ec 50 e8 67 02 00 00 85  |.......E.P.g....|
00000150  c0 89 45 fc 0f 8c 16 01  00 00 8b 45 ec ff 75 f8  |..E........E..u.|
00000160  8b 08 50 ff 51 28 85 c0  89 45 fc 0f 8c ff 00 00  |..P.Q(...E......|
00000170  00 8b 45 ec 8b 08 8d 55  e0 52 50 ff 51 10 85 c0  |..E....U.RP.Q...|
00000180  89 45 fc 0f 8c e7 00 00  00 8b 46 0c 33 45 e0 2b  |.E........F.3E.+|
00000190  fb 25 00 00 ff 00 31 46  0c 8b 45 f8 57 68 f4 f1  |.%....1F..E.Wh..|
000001a0  33 60 03 d8 53 ff 15 cc  12 33 60 8d 45 f0 50 e8  |3`..S....3`.E.P.|
000001b0  1b 09 00 00 85 c0 89 45  fc 0f 8c b1 00 00 00 fe  |.......E........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 08 54 06 00 fe  |............T...|
000001d0  ff ff 05 fe ff ff 02 08  54 06 00 90 44 00 00 00  |........T...D...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by five0xpres on 2010-08-09
I tried the commands listed above again, this time I'm going to copy/paste the errors I got:

```
root@ubuntu:/# sudo grub-install --root-directory=/mnt /dev/sda
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Installation finished. No error reported.
``````
root@ubuntu:/# sudo grub-mkconfig -o /mnt/boot/grub/grub.cfg
Generating grub.cfg ...
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!
done
```

```
root@ubuntu:/# sudo umount /mnt/dev
umount: /mnt/dev: not found
root@ubuntu:/# sudo umount /mnt
umount: /mnt: not mounted
```

---

### Post by john newbuntu on 2010-08-10
In your post #6, grub.cfg does show an entry for Windows as "Microsoft Windows XP Home Edition (on /dev/sda1)" as the last entry. I am not sure on why this does not show up in the menu after a reboot.  Perhaps someone else who has experienced this problem can help here.

But as a workaround, what you could do is to add the XP boot entry to the file /etc/grub.d/40_custom file and see if it helps.  

First boot from a Karmic or Lucid Desktop liveCD and reinstall grub2 to MBR using this simplified set of commands:
```
sudo mount /dev/sda5 /mnt       
sudo grub-install --root-directory=/mnt /dev/sda
sudo mount /dev/sda5 /mnt
sudo grub-mkconfig -o /mnt/boot/grub/grub.cfg
```

Reboot.  Log onto Ubuntu and from a terminal, type "gksu gedit /etc/grub.d/40_custom". Add:

```
menuentry "Windows XP" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set dac8060fc805eb19
    drivemap -s (hd0) ${root}
    chainloader +1
}
```

Save the file.  Then run "sudo update-grub".  Reboot and you should see XP as the last option. (You might even see 2 XP options.  Choose any to boot into XP)

---

### Post by five0xpres on 2010-08-10
Booted from the LiveCD, entered the first set of commands and here's the output:
```
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
mount: /dev/sda5 already mounted or /mnt busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-mkconfig -o /mnt/boot/grub/grub.cfg
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```

I'm going to reboot now and see what happens and will post my results.

---

### Post by five0xpres on 2010-08-10
Rebooted right back to "Minimal BASH-like line editing is supported" with the GRUB prompt.
 
This is very frustrating and one of the reasons I don't see Linux gaining much traction with non-geek computer users. For better or worse, Windows just works...most of the time. Granted there are some issues with it, but I've never had to fight like this to get Windows to setup after an install or an update.
 
I'm about to just wipe the Linux partitiions, resize Windows back to it's original size on the disk and toss this Ubunutu LiveCD in the trash and forget about it. What good is an OS that you can't even boot into it?
 
Please don't think I'm not grateful for the assistance you've given me, I am very much thankful to find a place to ask questions.  It's just that the frustration I'm going through trying to get this working shows me that despite the strides Linux has made to become more user-friendly, it still has a long way to go.

---

### Post by john newbuntu on 2010-08-10
sorry five0xpres, I understand your pain.  I wish I could be of more help to get this working.  You might want to wait for someone else who is more qualified than me who can chip in and work with you on this before you throw in the towel.

---

### Post by dabl on 2010-08-10
@five0express, if you can get back to where you were at post #6 (i.e. just install Grub to the MBR of the first drive, and reboot into Ubuntu), then you can fix the boot menu from the booted system.  No need to boot a Live CD to fix it.

With Ubuntu running, use "gkesu gedit" as John wrote, to add this to the file /etc/grub.d/40_custom:

```
menuentry "Windows XP" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set dac8060fc805eb19
    drivemap -s (hd0) ${root}
    chainloader +1
}
```

Save it and exit gedit.

Now open a terminal and issue ```
sudo update-grub
```

Observe the messages -- does it find XP?  If yes ```
sudo shutdown now -r
```

and reboot.  Upon rebooting, you should see Win XP on the menu.

---

### Post by hypecat on 2010-08-10
I had the same exact issue last night, installed Ubuntu updates and my netbook went into a boot loop and never got far enough to choose an OS.
 
I ended up booting from a USB (I have no optical drive), deleted the Ubuntu partion (partitions), then re-installed Ubuntu into the "free space".  It was a pain because I had to rebuild the apps, profiles, etc....
 
Twice I have had to rebuild the Ubuntu side because of problems with updates which is frustrating.  I am guessing it was Grub that was the issue, but I lack the expertise in fixing Grub.  
 
I wish there was a way to delay the installation of updates until they have been more thoroughly tested.
 
Bleeding edge is not my preference.
 
I also wish there was a better boot loader, something "outside" of Ubuntu or Windows so if something happened to one OS, you could simply choose the other.  I seem to remember back in the day one I used for OS/2 and Windows that was independent of either OS.... But then again, I have become old and forgetful!

---

### Post by five0xpres on 2010-08-10
Thanks for the info, [dabl]("http://ubuntuforums.org/member.php?u=217451").  I followed your instructions, saved and rebooted to find the GRUB menu, minus the option to boot in Windows XP, despite the messages after 'sudo update-grub' telling me that it found my Windows XP installation.

One step closer to turning the LiveCD into a coaster.

---

### Post by Xalorplex on 2010-08-10
Just my 2 cents....

I'm new to the whole Ubuntu scene as well, five0xpres.  I tried a clean 10.04 install on an old computer and had nothing but problems (random reboots, screen would start tripping out, mouse would disappear, internet connection wouldn't be recognized, etc).  I then wiped the HDD and installed Ubuntu 9.04 and have nothing but good things to say (so far..)!  

Before you lose complete faith in Linux, try 9.04 (a handy google search of "Ubuntu 9.04 download" should do the trick) and see if it works any better.  If Linux is already on your "bad list", then please disregard. :)

---

### Post by dabl on 2010-08-10
There must be a problem with the form of the menu entry in /etc/grub.d/40_custom

If you review the /boot/grub/grub.cfg file (just "cat" it), under the part that reads > ### BEGIN /etc/grub.d/40_custom ### there is a stanza that is supposed to show the Win XP menu item.  It should look like the stanza that you entered and saved in /etc/grub.d/40_custom -- does it look exactly the same?

Also, I'm not sure the apostrophes are required around the "set root=" statement in /etc/grub.d/40_custom.  You might try removing them, re-run sudo update-grub, and see if helps.  I found this example for booting Windows:


> Windows XP on sda1
menuentry “Windows XP on sda1, by chainloader”  {
set root=(hd0,1)
chainloader +1
}

On this thread:  [http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

---

### Post by five0xpres on 2010-08-10
here's what's currently at the end of the grub.cfg file
```
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows XP" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set dac8060fc805eb19
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/40_custom ###
```I'll try removing the apostrophes at the set root line, reinstall GRUB, update it and reboot again and report back the results.

---

### Post by five0xpres on 2010-08-10
I used the instructions in reply#4 of this post to reinstall GRUB.  I left off the recheck parameter because I recall reading that it should be used only if the command returns an error, if I should use it anyway, please let me know and I'll try it with it.  Here's the output:
```

root@ubuntu:~# sudo mount /dev/sda5 /mnt
root@ubuntu:~# sudo mount --bind /dev /mnt/dev
root@ubuntu:~# sudo chroot /mnt
root@ubuntu:/# sudo grub-install --root-directory=/mnt /dev/sda
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Installation finished. No error reported.
root@ubuntu:/# sudo grub-mkconfig -o /mnt/boot/grub/grub.cfg
Generating grub.cfg ...
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!
done
root@ubuntu:/# sudo umount /mnt/dev
umount: /mnt/dev: not found
root@ubuntu:/# sudo umount /mnt
umount: /mnt: not mounted
root@ubuntu:/# 

```

Now to reboot and see what I have.

---

### Post by five0xpres on 2010-08-10
Ok, now I'm REALLY confused.  After doing the things listed in my last reply, I rebooted, got the GRUB menu and it finally listed my XP installation, using the menu entry I added at the end of the grub.cfg file.  (My initial XP installation was listed as "Microsoft Windows XP Home Edition", where the addition I made was just "Windows XP".)

While I'm happy that I'm able to dual boot again, I'm worried that the next set of updates is going to leave me at the broken GRUB prompt once again.  And if that's the case, then I guess I'll have to just remove Ubuntu and stay with Windows because I can't be doing all this extra work each time a system update is pushed out.  I must say that if I was anything but a wanna-be hardcore PC geek, I would have given up on this flavor of Linux (probably all flavors to tell the truth) after restoring my Windows MBR and told my friends not to bother trying it out themselves.

I'd like to thank [john newbuntu]("http://ubuntuforums.org/member.php?u=956991") and [dabl]("http://ubuntuforums.org/member.php?u=217451") for their assistance.  While I hope to not have anymore problems, at least I know where I can come to find some help.

---

### Post by dabl on 2010-08-10
> **five0xpres said:**
> 

it finally listed my XP installation, using the menu entry I added at the end of the grub.cfg file.



If you edited the file /boot/grub/grub.cfg, then that edit will not survive the next update that runs "update-grub".

However, if this means you now know what the entry needs to say, in /etc/grub.d/40_custom, then that's a good thing.  :)

You do NOT need to reinstall Grub, once you have it installed and working (the basic booting thing, not the menu necessarily).  In other words, Grub is a tiny OS that lives on the MBR and launches whatever is in /boot/grub/grub.cfg (which is built dynamically from the scripts in /etc/grub.d/, so even if the menu requires tweaking, there's no necessity to reinstall Grub itself.

You're comfortable working with Windows, and uncomfortable working with Linux and Grub.  About how many months and/or years did you spend building that comfort level with Windows?  ;)

---

### Post by five0xpres on 2010-08-10
> **dabl said:**
> If you edited the file /boot/grub/grub.cfg, then that edit will not survive the next update that runs "update-grub".

I had run the "update-grub" command at several points during this adventure, both after reinstalling grub about a dozen times and after the manual editing of /etc/grub.d/40_custom with no success.  Why it decided this time to actually do the updating, I have no idea...could it have been because this time I had set myself as root in the LiveCD environment before I set GRUB back up in the MBR?

> However, if this means you now know what the entry needs to say, in /etc/grub.d/40_custom, then that's a good thing.  :)

I installed Startup Manager from the Ubuntu Software Center I saw in another post, so I could more easily set Windows XP as the default OS.  When I run that, it shows both the Microsoft Windows XP Home Edition entry and the Windows XP entry I manually added.  I'd like to remove the first listing, since it doesn't show up in the GRUB menu at boot time.  How do I do that without messing up anything else?

> You do NOT need to reinstall Grub, once you have it installed and working (the basic booting thing, not the menu necessarily).  In other words, Grub is a tiny OS that lives on the MBR and launches whatever is in /boot/grub/grub.cfg (which is built dynamically from the scripts in /etc/grub.d/, so even if the menu requires tweaking, there's no necessity to reinstall Grub itself.

If you read my initial post, you'd see that an update to GRUB after I first installed Ubuntu left me with no boot menu, just a GRUB prompt.  I can not be without a working Windows system, so I had no choice but to use the XP install CD to enter the repair console and rewrite the MBR so I could at least boot up Windows.  I assume that when I did that, GRUB was removed from my system and needed to be reinstalled into the MBR.  Was this an incorrect conclusion?

> You're comfortable working with Windows, and uncomfortable working with Linux and Grub.  About how many months and/or years did you spend building that comfort level with Windows?  ;)

True, but in my defense, I was a lot younger and more adventurous back then.  Now, I have little time and less patience with those things that don't work like they should.  Don't even get me started on the time I read the riot act to our local cable provider when repeated speed tests showed I wasn't getting even close the throughput I was paying for. :D  Or my visit to my cell company today to tell them if they don't reinstate my corporate employee discount (my employer has an agreement with them to give employees a 20% discount), I would go across the street to their competitor and sign up for service right then and there.  I left with my discount and a service credit for the inconvenience. ;)

---

### Post by dabl on 2010-08-10
> **five0xpres said:**
> 

in my defense, I was a lot younger and more adventurous back then.  

Yeah, I can sympathize (closing in on 60 here).

Probably this project would be a lot more enjoyable if it were NOT being performed on your critical Win XP box, which you cannot afford to break.  When time permits, may I suggest you take a USB memory stick, and play with Grub 2 on that, where it can't hurt anything.  Here are some links:

[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

[http://kubuntuforums.net/forums/index.php?topic=3106368](http://kubuntuforums.net/forums/index.php?topic=3106368)

[http://kubuntuforums.net/forums/index.php?topic=3107512.0](http://kubuntuforums.net/forums/index.php?topic=3107512.0)

---

### Post by ptm on 2010-08-10
I resolved this issue by reinstalling ubuntu 9.10  I wish Canonical would come up with something that was a quick fix for those of us that are a little weak in understanding the underlying issues.

---

### Post by five0xpres on 2010-08-10
Thanks for the links...I'll look into them when I get a chance.  And thanks for the help, I probably would have dumped Linux for good this time if I couldn't get the system to boot reliably today.  I was just tired of fighting with it and would have finally shown it who was the Boss. :)

---

### Post by five0xpres on 2010-08-10
My initial install went fine.  It even copied my desktop wallpaper in Windows XP and had it as the background on my Linux desktop.  I found some cool things to add to the panel, namely system temp since my XP install tended to run a little hot when watching/editing/trans-coding a lot of video.  The problem started when I installed the update for GRUB listed.  I was able to work through that problem, only to have something break dealing with GRUB a few days later.  Looking at the install history, it appears a new kernel {maybe? - linux-headers-2.6.32-24 (2.6.32-24.38) to 2.6.32-24.39} might have been the cause of my latest problem.

Next time I'll be more aware of GRUB and kernel updates and make sure I don't install them when they become immediately available because I might not be able to get back into either OS right away.

---

