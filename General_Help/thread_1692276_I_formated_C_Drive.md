---
title: "I formated C Drive"
date: 2011-02-21
forum: General Help
---

### Post by baqar on 2011-02-21
I formatted C drive and lost my ubuntu login
now what shall i do to again log in ubuntu ??

---

### Post by aeiah on 2011-02-21
was ubuntu on your C drive? if not, you probably just removed grub, and could fix it with the super grub2 disc or something.

---

### Post by psusi on 2011-02-21
Ubuntu does not have a "C Drive".  You will have to be more specific about what you mean.

---

### Post by baqar on 2011-02-21
No Ubuntu was on other drive ext4
please tell me how to revive it

---

### Post by Rubi1200 on 2011-02-21
Did you install Ubuntu using Wubi?

---

### Post by baqar on 2011-02-22
> **Rubi1200 said:**
> Did you install Ubuntu using Wubi?

I installed it using my USB. what do u mean by wubi :confused:

---

### Post by Rubi1200 on 2011-02-22
Hi baqar,
if you want us to help you, please provide more information. You have given us practically nothing to work with.

I suggest you use a LiveCD and then download and run the boot info script (there is a link at the bottom of my post with instructions).

Post the results back here.

Thanks.

---

### Post by baqar on 2011-02-26
> **Rubi1200 said:**
> Hi baqar,
if you want us to help you, please provide more information. You have given us practically nothing to work with.

I suggest you use a LiveCD and then download and run the boot info script (there is a link at the bottom of my post with instructions).

Post the results back here.

Thanks.

Here are the results

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   157,573,119   157,571,072   7 HPFS/NTFS
/dev/sda2         157,581,646   976,771,071   819,189,426   5 Extended
/dev/sda5         670,601,216   826,936,379   156,335,164   7 HPFS/NTFS
/dev/sda6         157,581,648   663,420,239   505,838,592   7 HPFS/NTFS
/dev/sda7         663,420,928   670,599,167     7,178,240  82 Linux swap / Solaris
/dev/sda8         826,939,392   976,771,071   149,831,680  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2063 MB, 2063597568 bytes
64 heads, 62 sectors/track, 1015 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     4,027,519     4,027,458   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A83215AA32157E8E                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0E2927D21DED426C                       ntfs       Stuff                         
/dev/sda6        5991EC290642B622                       ntfs                                     
/dev/sda7        753b5f36-d51b-4ff5-9c39-46663a881d65   swap                                     
/dev/sda8        30ae54d3-b36a-4b83-a310-78d2ca325c37   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        17FD-1223                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 30ae54d3-b36a-4b83-a310-78d2ca325c37
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos'
search --no-floppy --fs-uuid --set 30ae54d3-b36a-4b83-a310-78d2ca325c37
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos'
    search --no-floppy --fs-uuid --set 30ae54d3-b36a-4b83-a310-78d2ca325c37
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=30ae54d3-b36a-4b83-a310-78d2ca325c37 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos'
    search --no-floppy --fs-uuid --set 30ae54d3-b36a-4b83-a310-78d2ca325c37
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=30ae54d3-b36a-4b83-a310-78d2ca325c37 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 30ae54d3-b36a-4b83-a310-78d2ca325c37
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=30ae54d3-b36a-4b83-a310-78d2ca325c37 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos'
    search --no-floppy --fsuuid --set 30ae54d3-b36a-4b83-a310-78d2ca325c37
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=30ae54d3-b36a-4b83-a310-78d2ca325c37 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos'
    search --no-floppy --fs-uuid --set 30ae54d3-b36a-4b83-a310-78d2ca325c37
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=30ae54d3-b36a-4b83-a310-78d2ca325c37 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos'
    search --no-floppy --fs-uuid --set 30ae54d3-b36a-4b83-a310-78d2ca325c37
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=30ae54d3-b36a-4b83-a310-78d2ca325c37 ro single 
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
    set root='(hd0,msdos'
    search --no-floppy --fs-uuid --set 30ae54d3-b36a-4b83-a310-78d2ca325c37
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos'
    search --no-floppy --fs-uuid --set 30ae54d3-b36a-4b83-a310-78d2ca325c37
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 37346414150ba421
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

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=30ae54d3-b36a-4b83-a310-78d2ca325c37 /               ext4    errors=remount-ro 0       1
/dev/sda7       none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 453.6GB: boot/grub/core.img
 449.6GB: boot/grub/grub.cfg
 441.1GB: boot/initrd.img-2.6.35-22-generic
 441.1GB: boot/initrd.img-2.6.35-24-generic
 437.5GB: boot/initrd.img-2.6.35-25-generic
 453.6GB: boot/vmlinuz-2.6.35-22-generic
 453.5GB: boot/vmlinuz-2.6.35-24-generic
 454.0GB: boot/vmlinuz-2.6.35-25-generic
 437.5GB: initrd.img
 441.1GB: initrd.img.old
 454.0GB: vmlinuz
 453.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3e 00 00 00  |........?...>...|
00000020  42 74 3d 00 56 0f 00 00  00 00 00 00 02 00 00 00  |Bt=.V...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 23 12 fd 17 4e  4f 20 4e 41 4d 45 20 20  |..)#...NO NAME  |
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
00000100  7d 00 66 b8 d4 1e 00 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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

---

### Post by baqar on 2011-02-26
Now What ???? :(

---

### Post by Rubi1200 on 2011-02-26
You only have Windows installed in the MBR. If you want the dual-boot option back again, you will need to reinstall the GRUB bootloader like this:

From a LiveCD:

```
sudo mount /dev/sda8 /mnt

sudo grub-install --root-directory=/mnt /dev/sda
```

Once Ubuntu is booting again you must run this command to add Windows to the GRUB menu:
```
sudo update-grub
```

---

### Post by baqar on 2011-02-26
> **Rubi1200 said:**
> You only have Windows installed in the MBR. If you want the dual-boot option back again, you will need to reinstall the GRUB bootloader like this:

From a LiveCD:

```
sudo mount /dev/sda8 /mnt

sudo grub-install --root-directory=/mnt /dev/sda
```Once Ubuntu is booting again you must run this command to add Windows to the GRUB menu:
```
sudo update-grub
```

Please tell me the exact command that i shall type in terminal, u are communicating with a noob :).
When i typed the above quoted command i get this 

> ubuntu@ubuntu:~$ sudo mount /dev/sda8/mnt
mount: can't find /dev/sda8/mnt in /etc/fstab or /etc/mtab


---

### Post by Rubi1200 on 2011-02-26
baqar,
the easiest thing to do is copy and paste the commands I gave you.

There is a spacing error in the command you typed in.

```
sudo mount /dev/sda8[COLOR=Red]/[/COLOR]mnt
```

```
sudo mount /dev/sda8 /mnt

```
Do you see the difference?

---

### Post by baqar on 2011-02-26
> ubuntu@ubuntu:~$ sudo mount /dev/sda8 /mnt
ubuntu@ubuntu:~$ 



Done sta8 mounter, now what ???

---

### Post by baqar on 2011-02-26
sorry its mounted

---

### Post by baqar on 2011-02-26
> ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt dev/sda
/usr/sbin/grub-probe: error: cannot stat `dev/sda'.


This was the next step u had given and i am getting this error .:(

---

### Post by baqar on 2011-02-26
> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda8 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.
ubuntu@ubuntu:~$ 


Now going for sudo update-grub

---

### Post by Rubi1200 on 2011-02-27
You should not run update-grub on the LiveCD. Do it after rebooting.

But there is another problem which may be the source of your troubles.
> Sector 32 is already in use by FlexNet; avoiding it.  This software may  cause boot or other problems in future.  Please ask its authors not to  store data in the boot track..

See here for more:
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install)

---

### Post by baqar on 2011-02-27
Done thanks :)

---

### Post by Rubi1200 on 2011-02-27
Are you able to boot both Windows and Ubuntu without any issues?

If yes, then excellent :-)

If no, please explain what did not work for you.

---

