---
title: "grub2 can not find device for /, big mess-up"
date: 2010-02-24
forum: General Help
---

### Post by lindsay7 on 2010-02-24
I had grub trouble with a hardware change and have been trying to solve this. I think I have done more harm then good. I can not boot into Ubuntu or Windows 7. Here is the boot info script and other info on my problem.  Can someone please help me with this,

```
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
ubuntu@ubuntu:~$ sudo os-prober
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sdb1:Windows 7 (loader):Windows1:chain
/dev/sdb2:Ubuntu 9.10 (9.10):Ubuntu:linux
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.
```

```
ubuntu@ubuntu:~$ grub-install -v
grub-install (GNU GRUB 1.97~beta4)
ubuntu@ubuntu:~$ ls -l /etc/grub.d/
total 17
-rwxr-xr-x 1 root root 3296 2009-10-24 00:43 00_header
-rwxr-xr-x 1 root root 1154 2009-10-24 00:31 05_debian_theme
-rwxr-xr-x 1 root root 3778 2009-10-24 00:43 10_linux
-rwxr-xr-x 1 root root  772 2009-10-23 16:24 20_memtest86+
-rwxr-xr-x 1 root root 5332 2009-10-24 00:43 30_os-prober
-rwxr-xr-x 1 root root  214 2009-10-24 00:43 40_custom
-rw-r--r-- 1 root root  483 2009-10-24 00:43 README
ubuntu@ubuntu:~$
```

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 617199464 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

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
Disk identifier: 0x99d2cca0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,769,023   976,766,976   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7358e39d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   586,854,449   586,854,387   7 HPFS/NTFS
/dev/sdb2         586,856,448   731,278,799   144,422,352  83 Linux
/dev/sdb3         731,278,800   976,768,064   245,489,265   5 Extended
/dev/sdb5         731,294,865   743,006,249    11,711,385  82 Linux swap / Solaris
/dev/sdb6         743,006,313   976,768,064   233,761,752  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        CACAEC03CAEBEA21                       ntfs       adrive                        
/dev/sdb1        442604C22604B6C8                       ntfs                                     
/dev/sdb2        fd027f5c-7e2e-4161-84b4-c4b32265a175   ext4                                     
/dev/sdb5        031a2a69-63d5-465f-bbe8-ca43d957b05a   swap                                     
/dev/sdb6        8aaf3307-6206-4e45-b365-49b16e4bc88a   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sdb2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,2)
search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=6
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd1,2)
search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
insmod tga
if background_image /boot/grub/Lake_mapourika_NZ.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
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

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=031a2a69-63d5-465f-bbe8-ca43d957b05a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 317.8GB: boot/grub/core.img
 317.8GB: boot/grub/grub.cfg
 320.0GB: boot/initrd.img-2.6.31-14-generic
 319.4GB: boot/initrd.img-2.6.31-15-generic
 302.9GB: boot/vmlinuz-2.6.31-14-generic
 316.4GB: boot/vmlinuz-2.6.31-15-generic
 319.4GB: initrd.img
 320.0GB: initrd.img.old
 316.4GB: vmlinuz
 302.9GB: vmlinuz.old

```

---

### Post by meierfra. on 2010-02-24
Your RESULTS.txt does not reveal any problems.
Did you try to boot  with the Bios set boot from the Ubuntu drive?  
If yes, what exactly happens during boot up ?
If no,  try it now. If you are able to boot into Ubuntu run "sudo update-grub" in Ubuntu to add "Window 7" to the Grub menu.

---

### Post by lindsay7 on 2010-02-24
I have tried booting with each of the drives first and all that happens is I get

grub>_  

I just tried sudo update-grub from the Ubuntu live cd and it returens

grub-probe: error: can not find a device for / .


I can not boot into windows or ubuntu.

---

### Post by meierfra. on 2010-02-24
OK. Try reinstalling grub via:

```
sudo mount /dev/sdb2 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sdb
```

Reboot with the bios set to boot from the Ubuntu drive.

---

### Post by lindsay7 on 2010-02-24
this is what I received

Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
ubuntu@ubuntu:~$ 

Should I reboot now?

---

### Post by lindsay7 on 2010-02-24
I rebooted and tried booting with each drive making the change in the bios.

I still get 

grub_  and that is all.

---

### Post by meierfra. on 2010-02-24
Sorry, I have no clue what's going on.

Couple of things to try.

1) Purge and reinstall grub2:

```
sudo mount /dev/sdb2 /mnt
for i in dev proc sys dev/pts; do sudo mount --bind  /$i /mnt/$i;done
sudo cp /etc/resolv.conf /mnt/etc
sudo chroot /mnt
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl
apt-get update
apt-get purge grub-pc grub-common
apt-get install grub-pc grub-common
grub-install --recheck /dev/sdb
update-grub
rm /sbin/initctl
dpkg-divert --local --rename --remove /sbin/initctl
exit
for i in dev/pts dev proc sys /; do sudo umount /mnt/$i;done
```

Reboot from the Ubuntu drive


2) Make sure your hard drives are plugged in correctly. See whether you can boot if you unplug your second hard drive (the non-Ubuntu drive)

---

### Post by lindsay7 on 2010-02-24
Im I missing something with the code. when I type sudo /dev/sdb2 .mnt it comes back and says command not found.

---

### Post by meierfra. on 2010-02-24
> sudo /dev/sdb2 .mnt

it's supposed to be 

```
sudo mount /dev/sdb2 /mnt
```

---

### Post by lindsay7 on 2010-02-24
Ok, I ran the code and now I get the following

grub loading.
error: no such disk
grub rescue>_


I did find a loose sata (data cable) and replaced it.  I also tried booting from both disks by changing the bios and also tried booting with each disk with the other disconnected.

---

### Post by meierfra. on 2010-02-24
> grub loading.
error: no such disk
grub rescue>_


At least a little bit of progress. Just to make things simpler unplug  the non Ubuntu drive.  Then   post the output of the following commands at the "grub rescue" prompt:

```
ls
set 
ls (hd0,2)/
set root=(hd0,2)
set prefix=(hd0,2)/boot/grub
insmod ext2
insmod linux
linux /vmlinuz root=/dev/sda2 ro 
initrd /initrd.img
boot
```

---

### Post by lindsay7 on 2010-02-24
Ok, I will do that in a minute.  Here is the boot info script as of now..

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 617199464 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

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
Disk identifier: 0x99d2cca0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,769,023   976,766,976   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7358e39d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   586,854,449   586,854,387   7 HPFS/NTFS
/dev/sdb2         586,856,448   731,278,799   144,422,352  83 Linux
/dev/sdb3         731,278,800   976,768,064   245,489,265   5 Extended
/dev/sdb5         731,294,865   743,006,249    11,711,385  82 Linux swap / Solaris
/dev/sdb6         743,006,313   976,768,064   233,761,752  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        CACAEC03CAEBEA21                       ntfs       adrive                        
/dev/sdb1        442604C22604B6C8                       ntfs                                     
/dev/sdb2        fd027f5c-7e2e-4161-84b4-c4b32265a175   ext4                                     
/dev/sdb5        031a2a69-63d5-465f-bbe8-ca43d957b05a   swap                                     
/dev/sdb6        8aaf3307-6206-4e45-b365-49b16e4bc88a   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sdb2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,2)
search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=6
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd1,2)
search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
insmod tga
if background_image /boot/grub/Lake_mapourika_NZ.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set fd027f5c-7e2e-4161-84b4-c4b32265a175
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set cacaec03caebea21
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 442604c22604b6c8
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=031a2a69-63d5-465f-bbe8-ca43d957b05a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 320.2GB: boot/grub/core.img
 320.2GB: boot/grub/grub.cfg
 320.0GB: boot/initrd.img-2.6.31-14-generic
 319.4GB: boot/initrd.img-2.6.31-15-generic
 302.9GB: boot/vmlinuz-2.6.31-14-generic
 316.4GB: boot/vmlinuz-2.6.31-15-generic
 319.4GB: initrd.img
 320.0GB: initrd.img.old
 316.4GB: vmlinuz
 302.9GB: vmlinuz.old
```

---

### Post by meierfra. on 2010-02-24
> Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=fd027f5c-7e2e-4161-84b4-c4b32265a175)/boot/grub.

How did this happen?  Did you use "grub-install /dev/sda" instead of "grub-install /dev/sdb"?

---

### Post by lindsay7 on 2010-02-24
I only can get to the grub rescue with both drives plugged in.

This is what I got ls
(hd0) (hd0,1)
grub rscue> set
prefix=(uuid=fd027f5c-7e2e........boot/grub
root=uuid=fd027f5c......
grub rescue> ls (hd0,2)/
error:no such partition
grub rescue>


Sorry about the typing I have to go from one computer to the other.

---

### Post by meierfra. on 2010-02-24
> I only can get to the grub rescue with both drives plugged in.
Actually, I had guessed that after you posted the latest RESULTS.txt. 
Did you install install grub to /dev/sda?  Why?
Did  you carry out the  instructions in post 7 with "grub-install --recheck /dev/sdb" or with  "grub-install --recheck /dev/sda"?  


> This is what I got ls
(hd0) (hd0,1)

It seems Grub 2 is not able to detect your Ubuntu drive.   This might due to bug in Grub2, or  a BIOS problem or some hardware problems. You said that you  already tried all kinds of setting in the Bios. Did you reset the bios back to default at the end?  You might check on your CMOS battery.


Anyway, lets see what happens if you install Legacy grub. With just your Ubuntu drive attached:


```
sudo mount [COLOR="Red"]/dev/sda2 [/COLOR]/mnt
for i in dev proc sys dev/pts; do sudo mount --bind  /$i /mnt/$i;done
sudo cp /etc/resolv.conf /mnt/etc
sudo chroot /mnt
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl
apt-get update
apt-get purge grub-pc grub-common
apt-get install [COLOR="Red"]grub [/COLOR]grub-common
grub-install --recheck [COLOR="Red"]/dev/sda[/COLOR]
update-grub
rm /sbin/initctl
dpkg-divert --local --rename --remove /sbin/initctl
exit
for i in dev/pts dev proc sys /; do sudo umount /mnt/$i;done
```[COLOR="Red"][/COLOR]

(These are essentially the same instruction has in post 7, (I marked the changes in red)

---

### Post by lindsay7 on 2010-02-24
> Did you install install grub to /dev/sda? Why?
Did you carry out the instructions in post 7 with "grub-install --recheck /dev/sdb" or with "grub-install --recheck /dev/sda"?


If I did it was a typo, I went back and redid this.  I will go ahead and do what you just told me and get back with you.

---

### Post by lindsay7 on 2010-02-25
ok I did what you said. Here is the results

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
ubuntu@ubuntu:~$ for i in dev proc sys dev/pts; do sudo mount --bind  /$i /mnt/$i;done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# dpkg-divert --local --rename --add /sbin/initctl
Adding `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@ubuntu:/# ln -s /bin/true /sbin/initctl
root@ubuntu:/# apt-get update
Hit http://us.archive.ubuntu.com karmic Release.gpg                 
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US      
Hit http://security.ubuntu.com karmic-security Release.gpg          
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Hit http://archive.canonical.com karmic Release.gpg                  
Ign http://archive.canonical.com karmic/partner Translation-en_US    
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US

```

I will try rebooting.  By the way, the only things that I changed in the Bios was the boot order of the drives.

---

### Post by meierfra. on 2010-02-25
The last command in your output is "apt-get update". Did you run all the command?

---

### Post by meierfra. on 2010-02-25
> By the way, the only things that I changed in the Bios was the boot order of the drives.
Opps, I got mixed up with a different case.

So that might be one more thing to try (if legacy grub does not work)
Have a look at your bios and see whether there is some setting  which might prevent the Ubuntu drive from being detected. But if you change something, make sure to write down the original settings.

---

### Post by lindsay7 on 2010-02-25
Yes I did.  I do not know why the list was cut off when I copied it.  I made sure that I ran them all. but to be safe I will do it again.  I trie booting and what I got back was


Reboot and select proper boot device....

What do you think of me doing a reinstall of Ubuntu parititon on this drive. I will keep the windows partition and hope that a reinstall will bring back grub.  What do you think?

I am going to have to call it a night.  Thank you for your help.

Let me know what you think about the reinstall and I will work on it in the morning and post whatever happens.

Thanks again.

---

### Post by lindsay7 on 2010-02-25
Here is the full output of the code that you gave me.

```



ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# dpkg-divert --local --rename --add /sbin/initctl
Adding `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@ubuntu:/# ln -s /bin/true /sbin/initctl
root@ubuntu:/# apt-get update
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Hit http://archive.canonical.com karmic Release.gpg                 
Ign http://archive.canonical.com karmic/partner Translation-en_US    
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-security Release               
Hit http://us.archive.ubuntu.com karmic Release.gpg                  
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US
Hit http://archive.canonical.com karmic Release
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-backports Release.gpg
Ign http://us.archive.ubuntu.com karmic-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-proposed Release.gpg       
Ign http://us.archive.ubuntu.com karmic-proposed/restricted Translation-en_US
Hit http://security.ubuntu.com karmic-security/main Packages       
Ign http://us.archive.ubuntu.com karmic-proposed/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-proposed/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com karmic-proposed/universe Translation-en_US
Hit http://archive.canonical.com karmic/partner Packages             
Hit http://us.archive.ubuntu.com karmic Release                      
Hit http://us.archive.ubuntu.com karmic-updates Release                        
Hit http://us.archive.ubuntu.com karmic-backports Release                      
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/main Sources                    
Hit http://security.ubuntu.com karmic-security/restricted Sources              
Hit http://archive.canonical.com karmic/partner Sources                        
Hit http://us.archive.ubuntu.com karmic-proposed Release                       
Hit http://security.ubuntu.com karmic-security/universe Packages    
Hit http://security.ubuntu.com karmic-security/universe Sources     
Hit http://security.ubuntu.com karmic-security/multiverse Packages  
Hit http://security.ubuntu.com karmic-security/multiverse Sources   
Hit http://us.archive.ubuntu.com karmic/main Packages               
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-backports/main Packages
Hit http://us.archive.ubuntu.com karmic-backports/restricted Packages
Hit http://us.archive.ubuntu.com karmic-backports/universe Packages
Hit http://us.archive.ubuntu.com karmic-backports/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-proposed/restricted Packages
Hit http://us.archive.ubuntu.com karmic-proposed/main Packages
Hit http://us.archive.ubuntu.com karmic-proposed/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-proposed/universe Packages
Reading package lists... Done
root@ubuntu:/# apt-get purge grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-common* grub-pc* startupmanager*
0 upgraded, 0 newly installed, 3 to remove and 208 not upgraded.
After this operation, 5,333kB disk space will be freed.
Do you want to continue [Y/n]? y
Abort.
root@ubuntu:/# sudo mount /dev/sda2 /mnt
sudo: unable to resolve host ubuntu
root@ubuntu:/# for i in dev proc sys dev/pts; do sudo mount --bind  /$i /mnt/$i;done
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
root@ubuntu:/# sudo cp /etc/resolv.conf /mnt/etc
sudo: unable to resolve host ubuntu
cp: `/etc/resolv.conf' and `/mnt/etc/resolv.conf' are the same file
root@ubuntu:/# sudo chroot /mnt
sudo: unable to resolve host ubuntu
root@ubuntu:/# dpkg-divert --local --rename --add /sbin/initctl
Leaving `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@ubuntu:/# ln -s /bin/true /sbin/initctl
ln: creating symbolic link `/sbin/initctl': File exists
root@ubuntu:/# apt-get update
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Hit http://archive.canonical.com karmic Release.gpg                 
Ign http://archive.canonical.com karmic/partner Translation-en_US    
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-security Release               
Hit http://us.archive.ubuntu.com karmic Release.gpg                  
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US
Hit http://archive.canonical.com karmic Release
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US 
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Hit http://security.ubuntu.com karmic-security/main Packages         
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Hit http://archive.canonical.com karmic/partner Packages
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-backports Release.gpg        
Ign http://us.archive.ubuntu.com karmic-backports/main Translation-en_US
Hit http://security.ubuntu.com karmic-security/restricted Packages   
Hit http://security.ubuntu.com karmic-security/main Sources          
Hit http://security.ubuntu.com karmic-security/restricted Sources    
Hit http://security.ubuntu.com karmic-security/universe Packages     
Hit http://archive.canonical.com karmic/partner Sources              
Ign http://us.archive.ubuntu.com karmic-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-proposed Release.gpg
Ign http://us.archive.ubuntu.com karmic-proposed/restricted Translation-en_US
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Ign http://us.archive.ubuntu.com karmic-proposed/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-proposed/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com karmic-proposed/universe Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release
Hit http://us.archive.ubuntu.com karmic-updates Release
Hit http://us.archive.ubuntu.com karmic-backports Release
Hit http://us.archive.ubuntu.com karmic-proposed Release
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-backports/main Packages
Hit http://us.archive.ubuntu.com karmic-backports/restricted Packages
Hit http://us.archive.ubuntu.com karmic-backports/universe Packages
Hit http://us.archive.ubuntu.com karmic-backports/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-proposed/restricted Packages
Hit http://us.archive.ubuntu.com karmic-proposed/main Packages
Hit http://us.archive.ubuntu.com karmic-proposed/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-proposed/universe Packages
Reading package lists... Done
root@ubuntu:/# apt-get purge grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-common* grub-pc* startupmanager*
0 upgraded, 0 newly installed, 3 to remove and 208 not upgraded.
After this operation, 5,333kB disk space will be freed.
Do you want to continue [Y/n]? 
Abort.
root@ubuntu:/# sudo mount /dev/sda2 /mnt
sudo: unable to resolve host ubuntu
root@ubuntu:/# for i in dev proc sys dev/pts; do sudo mount --bind  /$i /mnt/$i;done
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
root@ubuntu:/# sudo cp /etc/resolv.conf /mnt/etc
sudo: unable to resolve host ubuntu
cp: `/etc/resolv.conf' and `/mnt/etc/resolv.conf' are the same file
root@ubuntu:/# sudo chroot /mnt
sudo: unable to resolve host ubuntu
root@ubuntu:/# dpkg-divert --local --rename --add /sbin/initctl
Leaving `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@ubuntu:/# ln -s /bin/true /sbin/initctl
ln: creating symbolic link `/sbin/initctl': File exists
root@ubuntu:/# apt-get update
Hit http://us.archive.ubuntu.com karmic Release.gpg
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US      
Hit http://security.ubuntu.com karmic-security Release.gpg          
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Hit http://archive.canonical.com karmic Release.gpg                  
Ign http://archive.canonical.com karmic/partner Translation-en_US    
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-security Release               
Hit http://archive.canonical.com karmic Release                      
Hit http://us.archive.ubuntu.com karmic-backports Release.gpg
Ign http://us.archive.ubuntu.com karmic-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-backports/multiverse Translation-en_US
Hit http://archive.canonical.com karmic/partner Packages             
Hit http://security.ubuntu.com karmic-security/main Packages         
Hit http://us.archive.ubuntu.com karmic-proposed Release.gpg
Ign http://us.archive.ubuntu.com karmic-proposed/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-proposed/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-proposed/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com karmic-proposed/universe Translation-en_US
Hit http://archive.canonical.com karmic/partner Sources              
Hit http://us.archive.ubuntu.com karmic Release                      
Hit http://us.archive.ubuntu.com karmic-updates Release
Hit http://us.archive.ubuntu.com karmic-backports Release
Hit http://security.ubuntu.com karmic-security/restricted Packages
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://security.ubuntu.com karmic-security/universe Sources     
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-proposed Release
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-backports/main Packages
Hit http://us.archive.ubuntu.com karmic-backports/restricted Packages
Hit http://us.archive.ubuntu.com karmic-backports/universe Packages
Hit http://us.archive.ubuntu.com karmic-backports/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-proposed/restricted Packages
Hit http://us.archive.ubuntu.com karmic-proposed/main Packages
Hit http://us.archive.ubuntu.com karmic-proposed/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-proposed/universe Packages
Reading package lists... Done
root@ubuntu:/# apt-get purge grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-common* grub-pc* startupmanager*
0 upgraded, 0 newly installed, 3 to remove and 208 not upgraded.
After this operation, 5,333kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
root@ubuntu:/# sudo mount /dev/sda2 /mnt
sudo: unable to resolve host ubuntu
root@ubuntu:/# for i in dev proc sys dev/pts; do sudo mount --bind  /$i /mnt/$i;done
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
root@ubuntu:/# sudo cp /etc/resolv.conf /mnt/etc
sudo: unable to resolve host ubuntu
cp: `/etc/resolv.conf' and `/mnt/etc/resolv.conf' are the same file
root@ubuntu:/# sudo chroot /mnt
sudo: unable to resolve host ubuntu
root@ubuntu:/# dpkg-divert --local --rename --add /sbin/initctl
Leaving `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@ubuntu:/# ln -s /bin/true /sbin/initctl
ln: creating symbolic link `/sbin/initctl': File exists
root@ubuntu:/# apt-get update
Hit http://us.archive.ubuntu.com karmic Release.gpg
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US      
Hit http://security.ubuntu.com karmic-security Release.gpg          
Hit http://archive.canonical.com karmic Release.gpg                  
Ign http://archive.canonical.com karmic/partner Translation-en_US    
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://archive.canonical.com karmic Release                      
Hit http://security.ubuntu.com karmic-security Release               
Hit http://us.archive.ubuntu.com karmic-backports Release.gpg
Ign http://us.archive.ubuntu.com karmic-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-proposed Release.gpg        
Ign http://us.archive.ubuntu.com karmic-proposed/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-proposed/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-proposed/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com karmic-proposed/universe Translation-en_US
Hit http://archive.canonical.com karmic/partner Packages             
Hit http://security.ubuntu.com karmic-security/main Packages         
Hit http://us.archive.ubuntu.com karmic Release
Hit http://us.archive.ubuntu.com karmic-updates Release
Hit http://us.archive.ubuntu.com karmic-backports Release
Hit http://us.archive.ubuntu.com karmic-proposed Release                       
Hit http://archive.canonical.com karmic/partner Sources              
Hit http://security.ubuntu.com karmic-security/restricted Packages  
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-backports/main Packages
Hit http://us.archive.ubuntu.com karmic-backports/restricted Packages
Hit http://us.archive.ubuntu.com karmic-backports/universe Packages
Hit http://us.archive.ubuntu.com karmic-backports/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-proposed/restricted Packages
Hit http://us.archive.ubuntu.com karmic-proposed/main Packages
Hit http://us.archive.ubuntu.com karmic-proposed/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-proposed/universe Packages
Reading package lists... Done
root@ubuntu:/# apt-get purge grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-common* grub-pc* startupmanager*
0 upgraded, 0 newly installed, 3 to remove and 208 not upgraded.
After this operation, 5,333kB disk space will be freed.
Do you want to continue [Y/n]? Y
Abort.
root@ubuntu:/# sudo mount /dev/sda2 /mnt
sudo: unable to resolve host ubuntu
root@ubuntu:/# for i in dev proc sys dev/pts; do sudo mount --bind  /$i /mnt/$i;done
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
root@ubuntu:/# sudo cp /etc/resolv.conf /mnt/etc
sudo: unable to resolve host ubuntu
cp: `/etc/resolv.conf' and `/mnt/etc/resolv.conf' are the same file
root@ubuntu:/# sudo chroot /mnt
sudo: unable to resolve host ubuntu
root@ubuntu:/# dpkg-divert --local --rename --add /sbin/initctl
Leaving `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@ubuntu:/# ln -s /bin/true /sbin/initctl
ln: creating symbolic link `/sbin/initctl': File exists
root@ubuntu:/# apt-get update
Hit http://archive.canonical.com karmic Release.gpg
Ign http://archive.canonical.com karmic/partner Translation-en_US   
Hit http://us.archive.ubuntu.com karmic Release.gpg                 
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US       
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US 
Hit http://security.ubuntu.com karmic-security Release.gpg           
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Hit http://archive.canonical.com karmic Release                      
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US   
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-security Release             
Hit http://us.archive.ubuntu.com karmic-backports Release.gpg       
Ign http://us.archive.ubuntu.com karmic-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-backports/universe Translation-en_US
Hit http://archive.canonical.com karmic/partner Packages             
Ign http://us.archive.ubuntu.com karmic-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-proposed Release.gpg
Ign http://us.archive.ubuntu.com karmic-proposed/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-proposed/main Translation-en_US
Hit http://security.ubuntu.com karmic-security/main Packages         
Ign http://us.archive.ubuntu.com karmic-proposed/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com karmic-proposed/universe Translation-en_US
Hit http://archive.canonical.com karmic/partner Sources              
Hit http://us.archive.ubuntu.com karmic Release                      
Hit http://us.archive.ubuntu.com karmic-updates Release
Hit http://us.archive.ubuntu.com karmic-backports Release
Hit http://security.ubuntu.com karmic-security/restricted Packages  
Hit http://security.ubuntu.com karmic-security/main Sources         
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://us.archive.ubuntu.com karmic-proposed Release            
Hit http://security.ubuntu.com karmic-security/universe Sources     
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-backports/main Packages
Hit http://us.archive.ubuntu.com karmic-backports/restricted Packages
Hit http://us.archive.ubuntu.com karmic-backports/universe Packages
Hit http://us.archive.ubuntu.com karmic-backports/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-proposed/restricted Packages
Hit http://us.archive.ubuntu.com karmic-proposed/main Packages
Hit http://us.archive.ubuntu.com karmic-proposed/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-proposed/universe Packages
Reading package lists... Done
root@ubuntu:/# apt-get purge grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-common* grub-pc* startupmanager*
0 upgraded, 0 newly installed, 3 to remove and 208 not upgraded.
After this operation, 5,333kB disk space will be freed.
Do you want to continue [Y/n]? Y
Abort.
root@ubuntu:/# apt-get install grub grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-common is already the newest version.
Suggested packages:
  grub-doc mdadm
The following packages will be REMOVED:
  grub-pc
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 1 to remove and 208 not upgraded.
Need to get 903kB of archives.
After this operation, 188kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.
root@ubuntu:/# grub-install --recheck /dev/sda
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found Debian background: Lake_mapourika_NZ.tga
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
root@ubuntu:/# rm /sbin/initctl
root@ubuntu:/# dpkg-divert --local --rename --remove /sbin/initctl
Removing `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@ubuntu:/# exit
exit
root@ubuntu:/# for i in dev/pts dev proc sys /; do sudo umount /mnt/$i;done
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
sudo: unable to resolve host ubuntu
root@ubuntu:/# 


```

---

### Post by lindsay7 on 2010-02-25
Does this look correct to you??

> Do you want to continue [Y/n]? Y
Abort.


---

### Post by lindsay7 on 2010-02-25
One more thought. This computer is mainly my Windows 7 machine which I had dual booted and it is giving me the problems right now.  I have two other computers that only have Ubuntu on them and those are the ones that I use most.  Do you think there would be a way for me to just get windows booting on this machine on this drive. Later I could add another drive and put ubuntu on that if I want, but since I have the other two computers setup with Ubuntu I really do not have to have it on this machine right now.

---

### Post by meierfra. on 2010-02-25
Is where a difference in the two hard drive? Is one of them Sata and the other IDE?  

A couple of more things to try before reinstalling:

See what happens  if  you swap the physical position of the hard drives.  
Check on the setting in your bios (see my last post)
See whether there is a update available for your Bios.


> Let me know what you think about the reinstall
That should work. It should even be enough to create a boot partition on the other drive (let me know if you would like help with creating  boot partition)

> 
Do you want to continue [Y/n]? Y
Abort.


That's weird.  apt-get refused to remove "grub-pc". So you still have Grub 2 installed.    You did mess up at least once:

> sudo cp /etc/resolv.conf /mnt/etc
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# dpkg-divert --local --rename --add /sbin/initctl


> sudo mount /dev/sda2 /mnt
sudo: unable to resolve host ubuntu
root@ubuntu:/# for i in dev proc sys dev/pts; do sudo mount --bind  /$i /mnt/$i;done


The mount commands have to come before the "chroot" command. 

But that does not explain why "grub-pc" did not get removed.
You might try again and make sure to follow the instruction exactly.


> Do you think there would be a way for me to just get windows booting on this machine on this drive.
Maybe.  If that works, it might even be possible to add Ubuntu to the Windows boot loader.

Try this (still with only the Ubuntu drive attached)

```
sudo apt-get install lilo
```
(ignore the warnings, just press enter)

```
sudo lilo -M  /dev/sda mbr
```


Reboot. You should boot right into Window 7.

---

### Post by nikhilbhardwaj on 2010-02-25
> **lindsay7 said:**
> One more thought. This computer is mainly my Windows 7 machine which I had dual booted and it is giving me the problems right now.  I have two other computers that only have Ubuntu on them and those are the ones that I use most.  Do you think there would be a way for me to just get windows booting on this machine on this drive. Later I could add another drive and put ubuntu on that if I want, but since I have the other two computers setup with Ubuntu I really do not have to have it on this machine right now.

do you have the windows 7 install dvd
if so then its possible to get windows 7 running
this thread should give you some additional info 
[http://ubuntuforums.org/showthread.php?t=508927&highlight=restore+windows+bootloader](http://ubuntuforums.org/showthread.php?t=508927&highlight=restore+windows+bootloader)

---

### Post by meierfra. on 2010-02-25
> 208 not upgraded.

Maybe "apt-get" will be happier if you  upgrade those packages before  trying to remove "grub-pc":


```
sudo mount /dev/sda2 /mnt
for i in dev proc sys dev/pts; do sudo mount --bind  /$i /mnt/$i;done
sudo cp /etc/resolv.conf /mnt/etc
sudo chroot /mnt
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl
apt-get update
[COLOR="Red"]apt-get upgrade[/COLOR]
apt-get purge grub-pc grub-common
apt-get install grub grub-common
grub-install --recheck /dev/sda
update-grub
rm /sbin/initctl
dpkg-divert --local --rename --remove /sbin/initctl
exit
for i in dev/pts dev proc sys /; do sudo umount /mnt/$i;done
```[COLOR="Red"][/COLOR]

---

### Post by lindsay7 on 2010-02-25
Thanks meierfra,

I tried everything and the disk will still not be recognized during start up.

I had the drive backed up with Acronis and did a restore and it took all day which seemed odd. It did restore with all the partitions and the original boot loaders, but it still was not being recognized at start up.  So my guess is that the drive has gone bad.  I just put in a new drive and am doing a restore now (taking less than two hours).  

I will post later on how this goes. Hopefully all I will have to do is get the new configuration to boot correctly.

I surely do appreciate all of your effort in helping me with this and wish that I could reciprocate, but you are far better at this than I. I will just try to help the next person in line with the problems that I can solve.

---

### Post by lindsay7 on 2010-02-26
The blue bird of happiness is flying again. The restore worked and I have windows and ubuntu back again.  The last thing you want to think about is a drive that unexpectedly bites the dust but it happens.

Thanks again for the hand holding and support.

---

### Post by roshats on 2010-03-13
I had similar problem: after reinstallation of grub 2 i had only "grub>_". when tried grub-mkconfig had "cannot find a device for /.". But instructions at 7th post ( [http://ubuntuforums.org/showpost.php?p=8878209&postcount=7](http://ubuntuforums.org/showpost.php?p=8878209&postcount=7) ) helped me. Thx lindsay7 for starting this topic and meierfra. for the solution.

---

