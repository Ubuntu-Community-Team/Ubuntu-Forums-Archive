---
title: "General error mounting file system"
date: 2011-04-13
forum: General Help
---

### Post by suduntu on 2011-04-13
Hi,

I have a dual boot Xp and Ubuntu 10.10.

Recently I was downloading some upgrades in Ubuntu and unfortunately the power to the system got off.

Thereafter on booting it comes to the Grub menu and I'm able to select the OS from the list but if I choose Ubuntu it comes up with a message "General error mounting file system" and the terminal is activated. However, if XP is selected it boots with no issues.

/dev/sda6 is ubuntu installation
/dev/sda7 is swap partition

I went through lot of threads over the net and tried fsck, e2fsck and other variations of that command but at the end all I get the message as 

it says sda6 is clean but for sda7 it says :

Superblock invalid trying backup blocks....
Bad magic number in super-block while trying to open /dev/sda7
at the end it suggests
 "u might try running e2fsck with an alternate superblock:  e2fsck -b 8193 <device>"

refering some threads here I tried my luck with live CD and the command : sudo e2fsck -C0 -p -f -v /dev/sda7

but the issue is not getting sorted, please help. I'm a novice user just begun with Ubuntu.

Thanks

---

### Post by kiyop on 2011-04-13
"e2fsck" does not checks swap partition, but checks ext2/ext3/ext4 filesystem.
If you can boot with ubuntu via CLI, you can log in and format swap partition (all data in swap partition will be destroyed).
If you want to format swap partition (/dev/sda7), log in and type 
```
sudo blkid
```
to confirm that /dev/sda7 is swap partition.
If /dev/sda7 is not swap partition, you should not go ahead.
If /dev/sda7 is swap partition, type
```
sudo swapoff -a
sudo mkswap -c /dev/sda7
```
The UUID will be shown.
You should manually change the configuration of UUID of the swap partition (/dev/sda7) in /etc/fstab and /etc/initramfs-tools/conf.d/resume.
```
sudo nano /etc/fstab
sudo nano /etc/initramfs-tools/conf.d/resume
```

---

### Post by suduntu on 2011-04-13
Hi, thanks for your kind help
  > sudo mkswap -c /dev/sda7 It displayed the UUID after the above command

Sorry i didn't get this > You should manually change the configuration of UUID of the swap  partition (/dev/sda7) in /etc/fstab and  /etc/initramfs-tools/conf.d/resume. as in? to replace the UUID with the new one or anything else?

I tried to replace the UUID but it gave me read-only access and I was not able to save the changes
I did all these from the maintenance shell where I was automatically getting landed after the filesystem mounting error.
Is it same as CLI? May be I don't know how to boot via CLI. Please shed some light. Thank You.

---

### Post by danjahner on 2011-04-13
If you run `blkid`it will show the UUID of your newly created swap partition. Make note of it, then open /etc/fstab in a text editor. Update the UUID listed for the swap partition with the new UUID you copied from `blkid`.

---

### Post by suduntu on 2011-04-13
> **danjahner said:**
> If you run `blkid`it will show the UUID of your newly created swap partition. Make note of it, then open /etc/fstab in a text editor. Update the UUID listed for the swap partition with the new UUID you copied from `blkid`. danjahner, I was not able to save changes to those files as I'm getting "read only" access to them.

Pls do let me know hw do I boot via CLI so that I may get the read-write permissions.

---

### Post by Rubi1200 on 2011-04-13
To edit system files, you need to escalate privileges.

Thus, for non-graphical applications, preface commands with sudo.

For graphical applications, such as a text editor that opens a file, use either gksudo or gksu.

In this case, to edit the fstab file:

```
gksudo gedit /etc/fstab
```

Hope this helps.

---

### Post by suduntu on 2011-04-14
> **Rubi1200 said:**
> To edit system files, you need to escalate privileges.

Thus, for non-graphical applications, preface commands with sudo.

For graphical applications, such as a text editor that opens a file, use either gksudo or gksu.

In this case, to edit the fstab file:

```
gksudo gedit /etc/fstab
```Hope this helps.

Hi Rubi1200, Thanks for your inputs.


[LIST=1]
[*]Ubuntu was going in the maintenance shell and it said it couldn't display graphics for the gk commands
[*]Tried from an Ubuntu installed pen-drive and was able to save changes in the respective files after mounting the sda6 with slight modification of the command given by you. ```
gksudo gedit /media/UUID/etc/fstab
``` similarly, updated the new UUID in the "resume" file.
[*]Nothing seemed to work, on booting it kept on giving the same error "General error mounting filesystem"
[*]I tried to format the swap partition but with no luck had to ultimately delete it and got it freshly formatted. Did the step no. 2 again for the new UUID this time with sda8
[*]Now things have got more complicated. sda7 is no longer my swap partition but sda8 is the new swap.
[/LIST]
Attaching the output of Boot Info Script for your kind reference.

pls be informed that it shows sda3 mount failed. well sda3 was as it is now even before installing Ubuntu and ubuntu used to boot fine back then. so I don't think sda3 is the one causing this issue. sdb is the pendrive with ubuntu installed on it.

pls help me out.
 ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

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

/dev/sda1                  63   112,631,714   112,631,652   7 HPFS/NTFS
/dev/sda2         112,642,048   154,626,047    41,984,000   7 HPFS/NTFS
/dev/sda3         154,626,048   196,610,047    41,984,000   6 FAT16
/dev/sda4         196,612,094   620,550,143   423,938,050   f W95 Ext d (LBA)
/dev/sda5         196,612,096   301,060,095   104,448,000   7 HPFS/NTFS
/dev/sda6         301,074,228   332,304,524    31,230,297  83 Linux
/dev/sda7         514,054,144   620,550,143   106,496,000   7 HPFS/NTFS
/dev/sda8    *    332,304,588   336,208,319     3,903,732  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8032 MB, 8032092160 bytes
64 heads, 32 sectors/track, 7660 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048     6,836,223     6,834,176  83 Linux
/dev/sdb2           6,836,224    15,687,679     8,851,456  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4C5C0AEF5C0AD41C                       ntfs                                     
/dev/sda2        62F846ABF8467D73                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        DA46A80A46A7E58B                       ntfs       Movies                        
/dev/sda6        474f4b57-d71e-41a5-b38f-8bd5e2add4a3   ext4                                     
/dev/sda7        14FE90EAFE90C580                       ntfs       Songs                         
/dev/sda8        11b838d2-7ea0-4e55-b34d-6698c47495d2   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        a33eed56-4115-4495-b70b-d15297b88224   ext4                                     
/dev/sdb2        aa3b32b9-2f8d-45b0-8b81-d6490541ec6f   ext4       XP                            
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb2        /media/XP                ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /media/Ubuntu 10.10 i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda6        /media/474f4b57-d71e-41a5-b38f-8bd5e2add4a3 ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
search --no-floppy --fs-uuid --set 474f4b57-d71e-41a5-b38f-8bd5e2add4a3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 474f4b57-d71e-41a5-b38f-8bd5e2add4a3
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 474f4b57-d71e-41a5-b38f-8bd5e2add4a3
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=474f4b57-d71e-41a5-b38f-8bd5e2add4a3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 474f4b57-d71e-41a5-b38f-8bd5e2add4a3
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=474f4b57-d71e-41a5-b38f-8bd5e2add4a3 ro single 
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
    search --no-floppy --fs-uuid --set 474f4b57-d71e-41a5-b38f-8bd5e2add4a3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 474f4b57-d71e-41a5-b38f-8bd5e2add4a3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 40d8ca60d8ca5436
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
/dev/sda8    swap        swap    defaults    0    0

=================== sda6: Location of files loaded by Grub: ===================


 161.1GB: boot/grub/core.img
 158.7GB: boot/grub/grub.cfg
 156.8GB: boot/initrd.img-2.6.35-22-generic
 154.5GB: boot/vmlinuz-2.6.35-22-generic
 156.8GB: initrd.img
 154.5GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set a33eed56-4115-4495-b70b-d15297b88224
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set a33eed56-4115-4495-b70b-d15297b88224
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a33eed56-4115-4495-b70b-d15297b88224
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a33eed56-4115-4495-b70b-d15297b88224 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a33eed56-4115-4495-b70b-d15297b88224
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a33eed56-4115-4495-b70b-d15297b88224 ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a33eed56-4115-4495-b70b-d15297b88224
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a33eed56-4115-4495-b70b-d15297b88224
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1

=================== sdb1: Location of files loaded by Grub: ===================


   1.3GB: boot/grub/core.img
   1.4GB: boot/grub/grub.cfg
   1.4GB: boot/initrd.img-2.6.35-22-generic
   1.4GB: boot/vmlinuz-2.6.35-22-generic
   1.4GB: initrd.img
   1.4GB: vmlinuz
```

---

### Post by kiyop on 2011-04-14
The information on /dev/sda3 given by boot info script:
> sda3: _________________________________________________________________________

    File system:      
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''seems strange to me.

/dev/sda3 is reported to be FAT16, starting just at the next sector(?) of the end of /dev/sda2 and /dev/sda8 has boot flag, which seems strange.
> Drive: sda ___________________
Partition  Boot         Start           End          Size  Id System

/dev/sda2         112,642,048   154,626,047    41,984,000   7 HPFS/NTFS
/dev/sda3         154,626,048   196,610,047    41,984,000   6 FAT16

/dev/sda8    *    332,304,588   336,208,319     3,903,732  82 Linux swap / Solaris"blkid -c /dev/null:"
gives no information on /dev/sda3

And it is very strange that /boot/grub/grub.cfg on /dev/sda6 has:
> insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 474f4b57-d71e-41a5-b38f-8bd5e2add4a3This UUID is /dev/sda6's.

[COLOR=red]set root='(hd0,msdos7)'[/COLOR]
should be changed to:
[COLOR=blue]set root='(hd0,msdos6)'[/COLOR]

By default, /boot/grub/grub.cfg is not writable.
Although you can make it writable and edit it, you had better update it by the following method.

Boot with live pendrive and open terminal, type
```
sudo mount -t ext4 /dev/sda6 /mnt -o rw
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt /bin/bash
```If success, the prompt changes to "root(hogehoge):/#". Then, type
```
grub-mkdevicemap
update-grub
```You may remove the line concerning /dev/sda8 from /etc/fstab and /etc/initramfs-tools/conf.d/resume, in order to check whether the line is the cause of the problem or not.
```
nano /etc/fstab
nano /etc/initramfs-tools/conf.d/resume
```To exit from the chroot circumstance, type
```
exit
sudo umount -l /mnt/proc
sudo umount -l /mnt/sys
sudo umount -l /mnt/dev
sudo umount -l /mnt
```Reboot and remove pendrive.

---

### Post by drs305 on 2011-04-14
I'd agree with what has been proposed. 

If it still doesn't boot, the next step I think is to simplify things a bit and just disable swap for the moment. You can do this by mounting the Ubuntu partition.

```
sudo mount /dev/sda6 /mnt
gksu gedit /mnt/etc/fstab
```
Place a # symbol at the start of the swap line. Then save the file.


Reboot, making sure your BIOS is booting sda first. At the Grub menu press 'c' to get to the grub prompt. Type
```

ls (hd0,6)/boot/grub
```
and confirm you see lots of *.mod files. Besides confirming that the correct partition is being used, it will also confirm that your BIOS is capable of seeing the grub files.

Press ESC back to the main menu and press 'e' to edit the first entry. Change the 'set root=(hd0,7)' to 'set root=(hd0,6)', then CTRL-x to boot.

If it boots, run "sudo update-grub". We can then clear up the swap issue.

---

### Post by suduntu on 2011-04-14
many thanks to all of you for guiding me.

drs305, great idea, I do favor keeping the swap aside for the time being if possible.

It displayed lot of mod files and at the end grub.cfg as well. As per your instructions, I changed 'set root=(hd0,7)' to 'set root=(hd0,6)', then CTRL-x to boot. But sadly same outcome - > General error mounting filesystemsHowever, I went ahead with "sudo update-grub" but at the end it said it is a Read Only filesystem.

Gave one more try. after hitting 'e' to edit the grub entry it showed - ```
[COLOR=Red]record fail[/COLOR]
isnmod part_msdos
insmod [COLOR=Red]ext2[/COLOR]
set root='(hd0,msdos[COLOR=Red]7[/COLOR])'
search --no floppy --fs-uuid--set 474f4b57-d71e-41a5-b38f-8bd5e2add4a3
linux/boot/vmlinuz - 2.6.35-22 generic root=uuid=474f4b57-d71e-41a5-b38f-8bd5e2add4a3 [COLOR=Red]ro[/COLOR] _quiet splash_
initrd/boot/initrd.img-2.6.35-22-generic
``` here I made change "set root='(hd0,msdos[COLOR=Blue]6[/COLOR])'" and "[COLOR=Blue]rw[/COLOR]" for granting write permissions. This done and it again came up with the same annoying msg. But fortunately I ran sudo update-grub and for the first time it saved the new grub file.

But the issue still persists after rebooting. One more thing to note is it says ext2 in code above but sda6 is ext4 if I'm not mistaken. And what about "record fail" and quiet splash modes? are they valid

kjyop, I think the boot flag was put up on sda8 by me mistakenly while I created this new swap partition. and for [COLOR=red]set root='(hd0,msdos7)' instead of 06[COLOR=Black], I'm not sure. but may this could be an explanation - I installed xp and had reinstalled grub by method2 (copying grub files from root)

as for the commands suggested by you, I ran them and it came up as - Floating point exception (core dumped)
this happened both times ie., before and after removing /dev/sd8 from the respective files```
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda6 /mnt -o rw
mount: /dev/sda6 already mounted or /mnt busy
mount: according to mtab, /dev/sda6 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
Floating point exception (core dumped)
ubuntu@ubuntu:~$ 

```thanks
[/COLOR] [/COLOR]

---

### Post by drs305 on 2011-04-14
I don't think the problem is with Grub any longer, now that you have swap disabled and root as sda6 (although you may still have to manually change these in the Grub menu for now).  It's looking more likely to be with the partition and/or drive. As I was going through the thread the first time I noted you had run e2fsck, which is what I was thinking about at the time. However, re-reading the thread, I see you ran it on sda7 (your swap partition) when you were concentrating on that aspect.

If you haven't already done so, run the same command on sda6. Use the command you already posted, or "sudo e2fsck -f -y -v /dev/sda6"

---

### Post by kiyop on 2011-04-14
Thanks drs305.

I am not familiar with:
> Floating point exception (core dumped)I agree with drs305's idea of checking /dev/sda6 again by booting with Live Pendrive and type in terminal,
```
sudo e2fsck -f -y -v /dev/sda6
```I do not know well what "sda6 is clean" means exactly.
> **suduntu said:**
> /dev/sda6 is ubuntu installation
/dev/sda7 is swap partition

I went through lot of threads over the net and tried fsck, e2fsck and other variations of that command but at the end all I get the message as 

it says sda6 is clean ...

---

### Post by suduntu on 2011-04-14
drs305, this what I got for sda6
> ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda6
e2fsck 1.41.12 (17-May-2010)
Superblock last mount time is in the future.
    (by less than a day, probably due to the hardware clock being incorrectly set)  Fix? yes

Superblock last write time is in the future.
    (by less than a day, probably due to the hardware clock being incorrectly set).  Fix? yes

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda6: ***** FILE SYSTEM WAS MODIFIED *****

  164050 inodes used (16.79%)
     168 non-contiguous files (0.1%)
     114 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 138189/31
 2336515 blocks used (59.85%)
       0 bad blocks
       1 large file

  115395 regular files
   17292 directories
      59 character device files
      26 block device files
       0 fifos
       0 links
   31223 symbolic links (25689 fast symbolic links)
      46 sockets
--------
  164041 files
ubuntu@ubuntu:~$rebooted but still found the error.:confused:

Out of curiosity I would like to know if there is any way of overwriting or repairing an existing installation similar to what Windows offers? If so, will it fix this issue?
Although, at the same time I'm genuinely interested in troubleshooting this issue without having to re-install, unless we run out of options.

---

### Post by suduntu on 2011-04-15
Hey people, pls find the attached new boot script info if it could be of any help.
sdb=pendrive and can be ignored.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

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

/dev/sda1                  63   112,631,714   112,631,652   7 HPFS/NTFS
/dev/sda2         112,642,048   154,626,047    41,984,000   7 HPFS/NTFS
/dev/sda3         154,626,048   196,610,047    41,984,000   6 FAT16
/dev/sda4         196,612,094   620,550,143   423,938,050   f W95 Ext d (LBA)
/dev/sda5         196,612,096   301,060,095   104,448,000   7 HPFS/NTFS
/dev/sda6    *    301,074,228   332,304,524    31,230,297  83 Linux
/dev/sda7         514,054,144   620,550,143   106,496,000   7 HPFS/NTFS
/dev/sda8         332,304,588   336,208,319     3,903,732  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8032 MB, 8032092160 bytes
64 heads, 32 sectors/track, 7660 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048     6,836,223     6,834,176  83 Linux
/dev/sdb2           6,836,224    15,687,679     8,851,456  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4C5C0AEF5C0AD41C                       ntfs                                     
/dev/sda2        62F846ABF8467D73                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        DA46A80A46A7E58B                       ntfs       Movies                        
/dev/sda6        474f4b57-d71e-41a5-b38f-8bd5e2add4a3   ext4                                     
/dev/sda7        14FE90EAFE90C580                       ntfs       Songs                         
/dev/sda8        11b838d2-7ea0-4e55-b34d-6698c47495d2   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        a33eed56-4115-4495-b70b-d15297b88224   ext4                                     
/dev/sdb2        aa3b32b9-2f8d-45b0-8b81-d6490541ec6f   ext4       XP                            
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb2        /media/XP                ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /media/Ubuntu 10.10 i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 474f4b57-d71e-41a5-b38f-8bd5e2add4a3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 474f4b57-d71e-41a5-b38f-8bd5e2add4a3
set locale_dir=($root)/boot/grub/locale
set lang=
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 474f4b57-d71e-41a5-b38f-8bd5e2add4a3
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=474f4b57-d71e-41a5-b38f-8bd5e2add4a3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 474f4b57-d71e-41a5-b38f-8bd5e2add4a3
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=474f4b57-d71e-41a5-b38f-8bd5e2add4a3 ro single 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 474f4b57-d71e-41a5-b38f-8bd5e2add4a3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 474f4b57-d71e-41a5-b38f-8bd5e2add4a3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4c5c0aef5c0ad41c
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a33eed56-4115-4495-b70b-d15297b88224
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=a33eed56-4115-4495-b70b-d15297b88224 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a33eed56-4115-4495-b70b-d15297b88224
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=a33eed56-4115-4495-b70b-d15297b88224 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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
/dev/sda6       /               ext4    errors=remount-ro 0       1
#/dev/sda8    swap        swap    defaults    0    0

=================== sda6: Location of files loaded by Grub: ===================


 161.1GB: boot/grub/core.img
 161.2GB: boot/grub/grub.cfg
 156.8GB: boot/initrd.img-2.6.35-22-generic
 154.5GB: boot/vmlinuz-2.6.35-22-generic
 156.8GB: initrd.img
 154.5GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set a33eed56-4115-4495-b70b-d15297b88224
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set a33eed56-4115-4495-b70b-d15297b88224
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a33eed56-4115-4495-b70b-d15297b88224
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a33eed56-4115-4495-b70b-d15297b88224 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a33eed56-4115-4495-b70b-d15297b88224
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a33eed56-4115-4495-b70b-d15297b88224 ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a33eed56-4115-4495-b70b-d15297b88224
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set a33eed56-4115-4495-b70b-d15297b88224
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4c5c0aef5c0ad41c
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 474f4b57-d71e-41a5-b38f-8bd5e2add4a3
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=474f4b57-d71e-41a5-b38f-8bd5e2add4a3 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 474f4b57-d71e-41a5-b38f-8bd5e2add4a3
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=474f4b57-d71e-41a5-b38f-8bd5e2add4a3 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1

=================== sdb1: Location of files loaded by Grub: ===================


   1.3GB: boot/grub/core.img
   1.5GB: boot/grub/grub.cfg
   1.4GB: boot/initrd.img-2.6.35-22-generic
   1.4GB: boot/vmlinuz-2.6.35-22-generic
   1.4GB: initrd.img
   1.4GB: vmlinuz
```

---

### Post by suduntu on 2011-04-16
[COLOR=black]drs305, "sudo e2fsck -f -y -v /dev/sda6" from LiveCD didn't work out. So I booted from hdd and pressed 'e' in the grub menu and [/COLOR][COLOR=black]granted write permissions by changing the highlighted text in the code below to "[COLOR=Blue]rw[/COLOR]"[/COLOR]
```
[COLOR=black]record fail
isnmod part_msdos
insmod [/COLOR][COLOR=black]ext2
set root='(hd0,msdos[/COLOR][COLOR=black]6)'
search --no floppy --fs-uuid--set 474f4b57-d71e-41a5-b38f-8bd5e2add4a3
linux/boot/vmlinuz - 2.6.35-22 generic root=uuid=474f4b57-d71e-41a5-b38f-8bd5e2add4a3 [/COLOR][COLOR=black]**[COLOR=Red]ro[/COLOR]** quiet splash
initrd/boot/initrd.img-2.6.35-22-generic[/COLOR]
```[COLOR=black]

Having done this, it again took me to the maintenance shell where I ran [/COLOR][COLOR=black]"sudo e2fsck -f -y -v /dev/sda6" followed by "sudo update-grub". Following reboot I landed up with same error.

Not giving up I booted again with write permissions (rw) from grub menu and Ubuntu got finally loaded.  I had to manually grant write permission (rw) on every boot so I edited grub.cfg with ```
gksudo gedit /boot/grub/grub.cfg
``` and granted write permission. Now Ubuntu loads without any problems.

Please let me know whether I would land up in any trouble with these steps taken.
Also, can we proceed with the swap issue now?

Thank you all for your expert guidance, much appreciated.
[/COLOR]

---

### Post by kiyop on 2011-04-16
The result of "$ sudo e2fsck -f -y -v /dev/sda6" reported in [#13]("http://ubuntuforums.org/showpost.php?p=10678096&postcount=13") shows only two errors apparently:
> Superblock last mount time is in the future.
    (by less than a day, probably due to the hardware clock being incorrectly set)  Fix? yes

Superblock last write time is in the future.
    (by less than a day, probably due to the hardware clock being incorrectly set).  Fix? yesSimilar errors appeared when coin battery on motherboard was dead or when UTC time configuration was strange or when ubuntu installed on USB-HDD was booted in different computer (with different clock) than the former one.

/boot/grub/grub.cfg is automatically modified when update-grub is executed, for example, when new kernel is installed.

kernel option "ro" (read-only) is usually set, to make filesystem to be mounted to be able to be checked in booting (not read-only but read-write after booting).

I am not sure whether filesystem check (e2fsck) runs at boot time even when kernel option is "rw" instead of "ro" or not.

```
$ grep -n " ro " /etc/grub.d/*
```gives in my running Ubuntu 10.10,
> /etc/grub.d/10_linux:99:    linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
/etc/grub.d/10_linux.dpkg-old:71:    linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro $2
/etc/grub.d/20_linux_xen:82:    module    ${rel_dirname}/${basename} placeholder root=${linux_root_device_thisversion} ro ${args}So you can change 99th line in /etc/grub.d/10_linux to 
>     linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} r[COLOR=red]w[/COLOR] ${args}in order to keep "rw" instead of "ro" in /boot/grub/grub.cfg even after update-grub is executed.

But, the above-mentioned method is not default one. Use at your own risk.

---

### Post by suduntu on 2011-04-17
kiyop, I very much agree with you. "$ sudo e2fsck -f -y -v /dev/sda6" when ran from the LiveCD, must have  rectified the issue and I mistakenly presumed that when I ran it from shell maintenance it fixed the file system on sda6. Regarding the time difference, I guess you are right. The set time zone under ubuntu on pendrive and that on the sda6 were different. the motherboard battery seems still alive and kicking as I do not encounter any time lag in windows.

Ok thanks, I got the point why it is "ro" initially and "rw" after booting.
I guess setting it to "rw" may give an opportunity to some virus related activity during boot, but I ain't sure about it. If some how we can make it load Ubuntu without setting it to "rw" it will be great.

Any inputs regarding the swap partition sda8. will this the right time for resuming sda8?

---

