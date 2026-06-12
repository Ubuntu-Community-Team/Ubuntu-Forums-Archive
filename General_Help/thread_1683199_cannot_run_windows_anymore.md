---
title: "cannot run windows anymore"
date: 2011-02-07
forum: General Help
---

### Post by patocardo on 2011-02-07
Accidentally, I deleted Windows root files. I do not know why, but I cannot recover them.
The point is that I had installed two versions of Windows XP Pro SP2, so from grub I had other step before starting one Window versions. But now grub does not detect windows, and if it could, I would not be able to start it because of the lack of the files at root.

The result of bootinfo gives:
```

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sdb5 starts at sector 81915498.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

```

I do not know what happened to sdb5.
Is it a way to avoid reinstalling windows?

---

### Post by oldfred on 2011-02-07
Windows only boots from a primary partition with the boot flag. Additional installs of windows move the boot files to the first install with the boot flag. Windows officially will not directly boot from a logical partition, you have to have the boot files in a primary.

That said some here have workarounds.

How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)
Vista Win7 missing boot files meieifra
[http://ubuntuforums.org/showthread.php?t=813628#4](http://ubuntuforums.org/showthread.php?t=813628#4)
meierfra. - How to fix XP when the boot files are missing
How to fix Vista/Window 7 when the boot files are missing post4
[http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4](http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4)

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by patocardo on 2011-02-09
Thank you very much oldfred!
  But I still cannot solve my problem. Perhaps I could not understand the equivaleces between multi(?)disk(?)rdisk(?)partition(?) and /dev/sd??. Or maybe I am not doing the correct tasks with grub, because when I upgrade-grub, Windows launcher appears, but when I boot, Windows does not appear in the grub list.
  Any idea? thank you

---

### Post by oldfred on 2011-02-09
Post the full boot info script. You only posted part before.

rdisk is drive or sda is 1 or first drive. In grub hd0.
Partitions with grub2 are the same numbers as sda1 is partition 1 etc.

---

### Post by patocardo on 2011-02-10
Did you mean that
multi(0)disk(0)rdisk(0)partition(1) = sda1 ?

Here the RESULSTS.TXT complete

```
              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sdb5 starts at sector 81915498.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 41.2 GB, 41174138880 bytes
255 cabezas, 63 sectores/pista, 5005 cilindros, 80418240 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    77,015,609    77,015,547   7 HPFS/NTFS
/dev/sda2          77,015,610    80,405,324     3,389,715   5 Extended
/dev/sda5          77,015,673    80,405,324     3,389,652  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 82.3 GB, 82348277760 bytes
255 cabezas, 63 sectores/pista, 10011 cilindros, 160836480 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sdb2          81,915,496   160,826,714    78,911,219   f W95 Ext d (LBA)
/dev/sdb5          81,915,498   125,483,714    43,568,217   7 HPFS/NTFS
/dev/sdb6         125,483,778   160,087,724    34,603,947  83 Linux
/dev/sdb7         160,087,788   160,826,714       738,927  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9C5014F15014D43C                       ntfs       comunes                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0cd58933-3f2e-489d-b485-1ce4669baaac   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8A80535E80534FB5                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        BC449D50449D0E70                       ntfs                                     
/dev/sdb6        8d9909aa-576f-428c-9f30-bed13fb07b6d   ext4                                     
/dev/sdb7        096da516-bc54-4429-a344-63ae75adf35a   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw)
/dev/sda1        /mnt/comunes             fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/8A80535E80534FB5  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 8d9909aa-576f-428c-9f30-bed13fb07b6d
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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 8d9909aa-576f-428c-9f30-bed13fb07b6d
set locale_dir=($root)/boot/grub/locale
set lang=es
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
menuentry 'Ubuntu, con Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 8d9909aa-576f-428c-9f30-bed13fb07b6d
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=8d9909aa-576f-428c-9f30-bed13fb07b6d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-28-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 8d9909aa-576f-428c-9f30-bed13fb07b6d
	echo	'Cargando Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=8d9909aa-576f-428c-9f30-bed13fb07b6d ro single 
	echo	'Cargando el disco RAM inicial...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 8d9909aa-576f-428c-9f30-bed13fb07b6d
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=8d9909aa-576f-428c-9f30-bed13fb07b6d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-27-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 8d9909aa-576f-428c-9f30-bed13fb07b6d
	echo	'Cargando Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=8d9909aa-576f-428c-9f30-bed13fb07b6d ro single 
	echo	'Cargando el disco RAM inicial...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 8d9909aa-576f-428c-9f30-bed13fb07b6d
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=8d9909aa-576f-428c-9f30-bed13fb07b6d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-26-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 8d9909aa-576f-428c-9f30-bed13fb07b6d
	echo	'Cargando Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=8d9909aa-576f-428c-9f30-bed13fb07b6d ro single 
	echo	'Cargando el disco RAM inicial...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 8d9909aa-576f-428c-9f30-bed13fb07b6d
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=8d9909aa-576f-428c-9f30-bed13fb07b6d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-25-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 8d9909aa-576f-428c-9f30-bed13fb07b6d
	echo	'Cargando Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=8d9909aa-576f-428c-9f30-bed13fb07b6d ro single 
	echo	'Cargando el disco RAM inicial...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 8d9909aa-576f-428c-9f30-bed13fb07b6d
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=8d9909aa-576f-428c-9f30-bed13fb07b6d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-24-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 8d9909aa-576f-428c-9f30-bed13fb07b6d
	echo	'Cargando Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=8d9909aa-576f-428c-9f30-bed13fb07b6d ro single 
	echo	'Cargando el disco RAM inicial...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 8d9909aa-576f-428c-9f30-bed13fb07b6d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=8d9909aa-576f-428c-9f30-bed13fb07b6d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 8d9909aa-576f-428c-9f30-bed13fb07b6d
	echo	'Cargando Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=8d9909aa-576f-428c-9f30-bed13fb07b6d ro single 
	echo	'Cargando el disco RAM inicial...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, con Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 8d9909aa-576f-428c-9f30-bed13fb07b6d
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=8d9909aa-576f-428c-9f30-bed13fb07b6d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, con Linux 2.6.31-14-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 8d9909aa-576f-428c-9f30-bed13fb07b6d
	echo	'Cargando Linux 2.6.31-14-generic ...'
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=8d9909aa-576f-428c-9f30-bed13fb07b6d ro single 
	echo	'Cargando el disco RAM inicial...'
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 8d9909aa-576f-428c-9f30-bed13fb07b6d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 8d9909aa-576f-428c-9f30-bed13fb07b6d
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

=============================== sdb6/etc/fstab: ===============================

LABEL=comunes /mnt/comunes ntfs-3g users 0 0
UUID=0cd58933-3f2e-489d-b485-1ce4669baaac swap swap sw 0 0
UUID=8A80535E80534FB5 /media/8A80535E80534FB5 ntfs-3g defaults 0 0
UUID=8d9909aa-576f-428c-9f30-bed13fb07b6d / ext4 defaults 0 1
UUID=096da516-bc54-4429-a344-63ae75adf35a swap swap sw 0 0

=================== sdb6: Location of files loaded by Grub: ===================


  65.1GB: boot/grub/core.img
  67.4GB: boot/grub/grub.cfg
  66.8GB: boot/initrd.img-2.6.31-14-generic
  64.7GB: boot/initrd.img-2.6.32-21-generic
  70.5GB: boot/initrd.img-2.6.32-24-generic
  74.3GB: boot/initrd.img-2.6.32-25-generic
  70.7GB: boot/initrd.img-2.6.32-26-generic
  76.2GB: boot/initrd.img-2.6.32-27-generic
  76.8GB: boot/initrd.img-2.6.32-28-generic
  66.7GB: boot/vmlinuz-2.6.31-14-generic
  64.5GB: boot/vmlinuz-2.6.32-21-generic
  70.1GB: boot/vmlinuz-2.6.32-24-generic
  69.9GB: boot/vmlinuz-2.6.32-25-generic
  72.9GB: boot/vmlinuz-2.6.32-26-generic
  75.0GB: boot/vmlinuz-2.6.32-27-generic
  76.8GB: boot/vmlinuz-2.6.32-28-generic
  76.8GB: initrd.img
  76.2GB: initrd.img.old
  76.8GB: vmlinuz
  75.0GB: vmlinuz.old

```

---

### Post by oldfred on 2011-02-10
Your windows when installed said BIOS/windows saw the drive as drive 0 or sda. You also had two installs, but now your extended partition is the second partition.

XP need several things to boot. A valid partition NTFS boot sector and three files. You only seem to have two and are missing ntdetect??

Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)

COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

How to fix XP/Vista/7 when the boot files are missing meierfra
[http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4](http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4)
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
[http://ubuntuforums.org/showthread.php?t=1423998](http://ubuntuforums.org/showthread.php?t=1423998)

---

### Post by patocardo on 2011-02-12
I ask because I do not want to have another headache. If I run the console and recover the boot sector, Ubuntu will stay intact?

---

### Post by oldfred on 2011-02-12
If you run any auto repair command (I do not think XP had any) or any commands with fixMBR which then writes the windows boot loader back into the MBR, then you should not cause any problems with Ubuntu. But backups are always recommended.

Also, you need to be working with a full install disk not a recovery disk. The recovery disks are usually just images of the hard drive as purchased, so they erase everything and set windows back up as it was the day you bought computer.

Even if you overwrite the MBR that is easy to repair. But if you overwrite drive then you need a good backup of /home at the minimum. 

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by patocardo on 2011-02-13
I've already restore MBR (after backup), and the Windows console only see one of the two WinXP installations, and it runs very well. But the main problem is that when I reinstall grub as [ubuntu help says]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") It does not recognize it.
I do "update-grub", and it find both Windows installations, but on startup those findings do not appear. In grub.cfg I can see 'menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)"'... So I am lost

---

### Post by oldfred on 2011-02-13
Grub will only boot working windows. And it normally will not boot a second windows install directly. 

Windows deletes the boot files from a second install and moves them to the first install. Grub then cannot boot the second install as it has no boot files.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by RoboticRickJames747 on 2011-02-13
if you have the CD's that your computer came with, I think that the restore option on it will fix this for you

---

### Post by patocardo on 2011-02-14
Well, it is done. Thank you very much **oldfred**!
This is the synthesis of what I've done:

1st Problem:
- deleted windows root files

2nd Problem
- realize that one windows installation was corruped
- windows installer only recognize the corrupted installation

Steps to solution
1. Backup
2. Start with the Windows installer CD
3. Install Windows with the option of recover the existent installation...it takes a time
4. Continue to Win session
5. eject the CD
6. put the Ubuntu installer CD
7. Restart in the Ubuntu installer
8. mount the Ubuntu partition
9. Open terminal
10. Verify the partition's name.
```
mount | tail -1 
```
11. Install grub in disk where Ubuntu is
```
sudo grub-install --root-directory=/media/[name_of_the_partition] /dev/sdb
```
12. Close terminal and restart ubuntu without cd installer
13. (it displays grub menu, but not the Windows menu element so...)
14. Update grubs (I try with the followin options several times, so I do not know wich is the correct)
14.1. In terminal:
```

sudo update-grub

```
14.2. In terminal:
```

sudo update-grub2

```
14.3. Open /boot/grub/menu.lst with gedit and write:
```

title Windows XP
rootnoverify (hd0,0)
makeactive
chainloader +1

```

There is still one Windows Installation that I cannot use, but I can work normally now.

---

