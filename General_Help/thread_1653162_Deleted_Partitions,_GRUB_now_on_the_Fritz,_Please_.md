---
title: "Deleted Partitions, GRUB now on the Fritz, Please Help..."
date: 2010-12-26
forum: General Help
---

### Post by rainbowagent7 on 2010-12-26
Hi all. I recently used GParted to delete an unused partition and when I went to restart my computer I received the message "no such partition, GRUB rescue". I am running Ubuntu and Windows 7 on dual boot. The computer came with Windows on it, but I am a die-hard Ubuntu user so I installed Lucid. The first install was messy so I re-installed it. However, I was unaware that I could have adjusted the partitions on the second install, so I used GParted to remove the unnecessary ones. I'm quite sure I deleted the right ones, but somehow the Grub is not being read. I am fairly proficient with Ubuntu, and know this can be corrected, but I really don't want to mess anything up. I have read many posts on this same subject but to no avail, so I find myself in need of expert guidance once again. Any help would be greatly appreciated, however, due to the sensitive nature of working with partitions I would appreciate any help offered to be from experience and not guesswork. Thanks in advance.

---

### Post by coffeecat on 2010-12-26
You probably deleted the partition that grub stage 1 in the mbr looks to for the grub menu and module files. But with a second installation already in situ this should be easily repairable. Boot up the live CD, make sure you are connected to the internet and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the RESULTS.txt file in code tags for legibility. That will give us the details we need and we can take it from there.

---

### Post by rainbowagent7 on 2010-12-26
Thanks for the speedy reply Coffeecat. Here are the results:
                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   344,687,642   344,480,795   7 HPFS/NTFS
/dev/sda3         344,688,638 1,227,309,055   882,620,418   5 Extended
/dev/sda5         344,688,640 1,215,590,354   870,901,715  83 Linux
/dev/sda6       1,215,590,418 1,227,301,739    11,711,322  82 Linux swap / Solaris
/dev/sda4       1,227,309,056 1,250,260,991    22,951,936   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        986CF2956CF26CFE                       ntfs       SYSTEM                        
/dev/sda2        1448111D4810FEE4                       ntfs       HP                            
/dev/sda3: PTTYPE="dos" 
/dev/sda4        5A8446BB84469981                       ntfs       FACTORY_IMAGE                 
/dev/sda5        a49e9a95-a726-4b2a-9eaa-bcd743fca5b8   ext4                                     
/dev/sda6        f569d946-d041-44a8-b366-0e03b99f0780   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set a49e9a95-a726-4b2a-9eaa-bcd743fca5b8
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set a49e9a95-a726-4b2a-9eaa-bcd743fca5b8
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set a49e9a95-a726-4b2a-9eaa-bcd743fca5b8
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=a49e9a95-a726-4b2a-9eaa-bcd743fca5b8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set a49e9a95-a726-4b2a-9eaa-bcd743fca5b8
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=a49e9a95-a726-4b2a-9eaa-bcd743fca5b8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set a49e9a95-a726-4b2a-9eaa-bcd743fca5b8
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=a49e9a95-a726-4b2a-9eaa-bcd743fca5b8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set a49e9a95-a726-4b2a-9eaa-bcd743fca5b8
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=a49e9a95-a726-4b2a-9eaa-bcd743fca5b8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set a49e9a95-a726-4b2a-9eaa-bcd743fca5b8
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=a49e9a95-a726-4b2a-9eaa-bcd743fca5b8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set a49e9a95-a726-4b2a-9eaa-bcd743fca5b8
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=a49e9a95-a726-4b2a-9eaa-bcd743fca5b8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set a49e9a95-a726-4b2a-9eaa-bcd743fca5b8
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=a49e9a95-a726-4b2a-9eaa-bcd743fca5b8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set a49e9a95-a726-4b2a-9eaa-bcd743fca5b8
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=a49e9a95-a726-4b2a-9eaa-bcd743fca5b8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set a49e9a95-a726-4b2a-9eaa-bcd743fca5b8
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a49e9a95-a726-4b2a-9eaa-bcd743fca5b8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set a49e9a95-a726-4b2a-9eaa-bcd743fca5b8
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a49e9a95-a726-4b2a-9eaa-bcd743fca5b8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set a49e9a95-a726-4b2a-9eaa-bcd743fca5b8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set a49e9a95-a726-4b2a-9eaa-bcd743fca5b8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 986cf2956cf26cfe
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 5a8446bb84469981
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
# / was on /dev/sda7 during installation
UUID=a49e9a95-a726-4b2a-9eaa-bcd743fca5b8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=f569d946-d041-44a8-b366-0e03b99f0780 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 249.6GB: boot/grub/core.img
 248.6GB: boot/grub/grub.cfg
 249.7GB: boot/initrd.img-2.6.32-21-generic
 249.7GB: boot/initrd.img-2.6.32-24-generic
 249.8GB: boot/initrd.img-2.6.32-25-generic
 249.8GB: boot/initrd.img-2.6.32-26-generic
 249.8GB: boot/initrd.img-2.6.32-27-generic
 176.6GB: boot/vmlinuz-2.6.32-21-generic
 249.7GB: boot/vmlinuz-2.6.32-24-generic
 249.8GB: boot/vmlinuz-2.6.32-25-generic
 249.7GB: boot/vmlinuz-2.6.32-26-generic
 249.7GB: boot/vmlinuz-2.6.32-27-generic
 249.8GB: initrd.img
 249.8GB: initrd.img.old
 249.7GB: vmlinuz
 249.7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by coffeecat on 2010-12-26
OK, the situation is slightly different from what I thought. Grub in the mbr is not pointing to the deleted partition, but your surviving Ubuntu root partition has changed its designation from sda7 to sda5 with the partition deletion. Hence, grub is getting a bit confused. You'll have to do two things: reinstall grub to the mbr and chroot into sda5 to run grub-update to sort out the grub.cfg file.

Here's what to do. Boot up with the live CD. Open a terminal and mount sda5.

```
sudo mount /dev/sda5 /mnt
```Repair grub in the mbr:

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```Now for chrooting. First, change to root (it makes the following easier):

```
sudo su
```Now chroot into sda5. Do each of these commands one after the other.

```
mount -t proc none /mnt/proc
mount -o bind /dev /mnt/dev
chroot /mnt /bin/bash
```Now to regenerate grub.cfg.

```
update-grub
```That will get the correct code into the Ubuntu stanzas, but you may see a 'can't find list of  partitions' error (or words to that effect). If that happens, there will be no Windows entry in the regenerated grub menu, but that's easily fixed - below.

Now:

```
exit
exit
exit
```Yes, three times. Reboot and remove CD to boot into Ubuntu on your hard drive. If there is no Windows entry, simply open a terminal once you are logged in and:

```
sudo update-grub
```That should fix it.

---

### Post by rainbowagent7 on 2010-12-26
You're a genius Coffeecat! I entered the commands exactly as you prescribed and everything worked like a charm. I now have 420 GiB (what a great number!) on my Ubuntu partition, and windows is also showing up. Thanks a million, semi-newbies like me would be lost without knowledgeable people like you @ the helm. Keep up the great work, I'm happy to call this one solved:D

---

### Post by coffeecat on 2010-12-26
Excellent. Glad it's working.

Happy Ubuntu-ing!

---

### Post by Wejdan on 2010-12-31
> **coffeecat said:**
> You probably deleted the partition that grub stage 1 in the mbr looks to for the grub menu and module files. But with a second installation already in situ this should be easily repairable. Boot up the live CD, make sure you are connected to the internet and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the RESULTS.txt file in code tags for legibility. That will give us the details we need and we can take it from there.
[U][COLOR=Magenta]
Hi, I have the same exact problem, and did what you replied here... and got almost the same results (with differences in partitions i guess):[/COLOR][/U]

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

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

/dev/sda1               2,048    20,482,047    20,480,000  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     20,482,048   488,394,751   467,912,704   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4008 MB, 4008706048 bytes
118 heads, 54 sectors/track, 1228 cylinders, total 7829504 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,829,503     7,821,440   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        84A0CA3EA0CA3688                       ntfs       VistaOS                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        72A8-224E                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 72 04  |.X.SYSLINUX...r.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......|
00000020  80 58 77 00 c7 1d 00 00  00 00 00 00 02 00 00 00  |.Xw.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 4e 22 a8 72 4e  4f 20 4e 41 4d 45 20 20  |..)N".rNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 e0 e7 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

[U][COLOR=Magenta]___________________________

and since my partitions are different, and the fact that I'm freaking out.. I didn't want to do one more thing that I'm not sure of.. and so, would you please tell what to do next? (I know it's almost the same but what to put instead of sda5 ...etc in the terminal)[/COLOR][/U]

thank you :)

---

### Post by coffeecat on 2010-12-31
> **Wejdan said:**
> [U][COLOR=Magenta]
Hi, I have the same exact problem,[/COLOR][/U]

No, you don't. You have a somewhat different problem. You do not have Ubuntu on your system at all. You must have had once though, because grub stage 1 in the mbr is trying to find the rest of itself in partition sda5, which doesn't exist. You have only two partitions, sda1 which is the recovery partition and sda2 which is the Windows C: partition. Between them sda1 and sda2 cover the whole of the 250GB hard drive. You also have a 4GB pendrive which I guess is your live Ubuntu usb used to run the bootscript.

If you want to get Vista booting again you need to repair the mbr from the Vista install DVD or from a Vista recovery CD, here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Alternatively, you can reinstall Ubuntu which will reinstate grub, but that would mean resizing the Vista partition with the Ubuntu installer. It would be safer to repair the Windows mbr to get Vista booting and then use the Vista Disk Management tool to shrink the Vista partition.

By the way, when posting code or output such as that from the boot script, please remember to enclose it in [noparse]```

```[/noparse]. You have lost essential formatting by not doing so which makes it very difficult to read.

---

