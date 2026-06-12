---
title: "help!! ubuntu not booting!"
date: 2011-03-18
forum: General Help
---

### Post by rockager on 2011-03-18
my ubuntu installation has stopped booting after i deleted and again created one of my partitions (not the ubuntu partition but my data partition).
but now when i switch on my netbook it says:

error: unknown filesystem
grub rescue>

:(

i used gparted live to resize.

this is my disk partition structure:
/dev/sda1     20GB ( some pre-installed recovery software is in it that came when i purchased my netbook)
/dev/sda2     100MB (it's labeled SYSTEM' with a boot flag)
/dev/sda3     27.73GB (windows7 partition)
EXTENDED:---------/dev/sda4----------
----/dev/sda6  29.48GB(ubuntu partition)
----/dev/sda5  447MB(swap) 
----/dev/sda7  155.11GB(data partition: the one i deleted and created again)

before doing this, my ubuntu partition was /dev/sda7, the swap partition was /dev/sda 6, and the data partition was /dev/sda 7.

thanks in advance.

---

### Post by drs305 on 2011-03-18
If you get the menu, press "e" to edit the first menuentry:
Remove the entire "search" line using the cursor and DEL key.
Change the "linux" line section  "root=UUID=xxxxx" to "root=/dev/sda6"
CTRL-x to boot.

If you get just the Grub2 prompt, you can try this:
> 
configfile (hd0,6)/boot/grub/grub.cfg
or
```
set prefix=(hd0,6)/boot/grub
set root=(hd0,6)
insmod (hd0,6)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda6
initrd /initrd.img
boot
```

If it boots, run "sudo update-grub".

If it doesn't, please boot the LiveCD and download/run the boot info script from here:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net") and post the contents of RESULTS.txt

---

### Post by rockager on 2011-03-18
thanks for replying

i just got the rescue prompt so itried "configfile (hd0,6)/boot/grub/grub.cfg"
but it said: unknown command 'configfile'

the commands:

set prefix=(hd0,6)/boot/grub
set root=(hd0,6)
were taken in but when i entered
insmod (hd0,6)/boot/grub/linux.mod
it said:  'no such partition'

what do i do now?

---

### Post by drs305 on 2011-03-18
> **rockager said:**
> 
what do i do now?

Please post the contents of the RESULTS.txt from the boot info script.

---

### Post by rockager on 2011-03-18
```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda7 starts at sector 163108864.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    41,945,087    41,943,040  27 Hidden HPFS/NTFS
/dev/sda2    *     41,945,088    42,149,887       204,800   7 HPFS/NTFS
/dev/sda3          42,149,888   100,309,859    58,159,972   7 HPFS/NTFS
/dev/sda4         100,311,038   488,396,799   388,085,762   5 Extended
/dev/sda5         162,129,920   163,106,815       976,896  82 Linux swap / Solaris
/dev/sda6         100,311,040   162,127,871    61,816,832  83 Linux
/dev/sda7         163,108,864   488,396,799   325,287,936   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4010 MB, 4010803200 bytes
55 heads, 55 sectors/track, 2589 cylinders, total 7833600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          3,120     7,833,599     7,830,480   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9094ED2C94ED160E                       ntfs       RECOVERY                      
/dev/sda2        CA90331890330A89                       ntfs       SYSTEM                        
/dev/sda3        EA2EF0C22EF08939                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        eea1a8b8-7857-427f-9e2b-34613a88cafe   swap                                     
/dev/sda6        79c731d4-6005-467c-8c54-58eec33bbfb7   ext4                                     
/dev/sda7        11B6-60B5                              vfat       LocalDisk                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        928C-1A47                              vfat       GPARTED                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/GPARTED           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 79c731d4-6005-467c-8c54-58eec33bbfb7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 79c731d4-6005-467c-8c54-58eec33bbfb7
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 79c731d4-6005-467c-8c54-58eec33bbfb7
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=79c731d4-6005-467c-8c54-58eec33bbfb7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 79c731d4-6005-467c-8c54-58eec33bbfb7
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=79c731d4-6005-467c-8c54-58eec33bbfb7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 79c731d4-6005-467c-8c54-58eec33bbfb7
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=79c731d4-6005-467c-8c54-58eec33bbfb7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 79c731d4-6005-467c-8c54-58eec33bbfb7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=79c731d4-6005-467c-8c54-58eec33bbfb7 ro single 
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 79c731d4-6005-467c-8c54-58eec33bbfb7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 79c731d4-6005-467c-8c54-58eec33bbfb7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9094ed2c94ed160e
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set ca90331890330a89
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=79c731d4-6005-467c-8c54-58eec33bbfb7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=eea1a8b8-7857-427f-9e2b-34613a88cafe none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  58.1GB: boot/grub/core.img
  79.4GB: boot/grub/grub.cfg
  52.0GB: boot/initrd.img-2.6.35-22-generic
  52.1GB: boot/initrd.img-2.6.35-27-generic
  58.3GB: boot/vmlinuz-2.6.35-22-generic
  58.3GB: boot/vmlinuz-2.6.35-27-generic
  52.1GB: initrd.img
  52.0GB: initrd.img.old
  58.3GB: vmlinuz
  58.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 04 09  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 30 0c 00 00  |........?...0...|
00000020  d0 7b 77 00 7e 3b 00 00  00 00 00 00 02 00 00 00  |.{w.~;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 47 1a 8c 92 4e  4f 20 4e 41 4d 45 20 20  |..)G...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 e8  23 01 00 66 ba 00 00 00  |..E}.f..#..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by drs305 on 2011-03-18
This should be fairly easy to fix. You just need to make sure the MBR points to sda6. The following commands will do this.

Boot the LiveCD and from a terminal:
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Do not use the partition number in the second command.

Reboot and it should start working again.
Run this after rebooting:
```
sudo update-grub
```

---

### Post by rockager on 2011-03-18
> **drs305 said:**
> This should be fairly easy to fix. You just need to make sure the MBR points to sda6. The following commands will do this.

Boot the LiveCD and from a terminal:
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```Do not use the partition number in the second command.

Reboot and it should start working again.
Run this after rebooting:
```
sudo update-grub
```

did not work
i see a blinking '__' after rebooting

---

### Post by drs305 on 2011-03-18
> **rockager said:**
> did not work
i see a blinking '__' after rebooting

The blinking cursor is not a Grub2 problem. When Grub2 fails, it generates an error message of some sort or leaves you at a "grub" or "grub rescue" prompt.

Normally the blinking cursor is the result of a video problem. You can try some of these to see if you can get it to boot:

1. At the Grub menu (if you don't see it, hold down the SHIFT key during boot): Press 'e' to edit the first menuentry. Cursor to the 'linux' line, go to the end and remove "quiet splash" and add "nomodeset" (without the quotes). Press CTRL-x to boot.

2. Try the recovery mode option (if displayed) or try an older kernel. (Choose safe graphics if available)

If you are able to boot, go to System, Administration, Additional Drivers/Hardware Drivers and try to add your video card.

---

### Post by rockager on 2011-03-18
thanks a lot!! it worked!
thanks for helping me out with this.

---

