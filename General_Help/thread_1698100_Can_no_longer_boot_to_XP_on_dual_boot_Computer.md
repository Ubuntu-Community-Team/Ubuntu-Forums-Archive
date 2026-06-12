---
title: "Can no longer boot to XP on dual boot Computer"
date: 2011-03-01
forum: General Help
---

### Post by SuperFreak on 2011-03-01
I have (had) a dual boot computer;Win XP and Ubuntu 10.10 64 bit.I decided it was necessary to enlarge my Root and Home Partitions. Using the instructions [http://ubuntuforums.org/showthread.php?t=1676849&highlight=Resizing+Root+Home+Partitions](http://ubuntuforums.org/showthread.php?t=1676849&highlight=Resizing+Root+Home+Partitions) I successfully enlarged the partitions and restored 10.10 (I used the copy command suggested by Irony). However when I boot the computer it boots to Ubuntu but no longer gives me the option of going into XP(it is not listed in Grub menu). Is there a fairly straightforward way of getting XP back on the Grub menu so I can boot to XP again?

Thanks

---

### Post by turtle153 on 2011-03-01
Try ```
sudo update-grub
``` in the terminal

---

### Post by nm_geo on 2011-03-01
Try this:

B00t-info-script

boot_info_script is a bash script which searches all hard drives attached to the computer for information related to booting and displays it in a convenient format. Its primary use is for troubleshooting booting problems.
How to use the boot info script

    * Boot into any Linux based operating system, LiveCD or LiveUSB with an Internet connection.
    * Download the Boot Info Script    [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
    * Open a terminal (Applications>Accessories>Terminal in Gnome) and type

       sudo bash [path/to/the/download_folder]/boot_info_script*.sh

      For example if you downloaded the file to the desktop, use

       sudo bash ~/Desktop/boot_info_script*.sh 

    * If your operation system does not use sudo, use

           su 
           bash ~/Desktop/boot_info_script*.sh
           

    * You will now have the file RESULTS.txt in the same directory as the script. But if the script is inside a system directory (like /usr or /etc) RESULTS.txt will be in the home directory.
    * If you already have an existing RESULTS.txt, subsequent files will be called RESULTS1.txt, RESULTS2.txt,...
    * Open RESULTS.txt in your favorite text editor.
    * If you came here from a Linux forum, paste the content of RESULTS.txt into your next post. Make sure to use the appropriate formating. For example in the Ubuntu forums click on the code tags (the symbol #) before pasting RESULTS.txt.

---

### Post by SuperFreak on 2011-03-01
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for (,msdos8)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

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
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   209,487,599   209,487,537   7 HPFS/NTFS
/dev/sda2         209,489,920 1,953,523,711 1,744,033,792   f W95 Ext d (LBA)
/dev/sda5         375,392,256   384,016,383     8,624,128  82 Linux swap / Solaris
/dev/sda6         384,017,823 1,953,520,064 1,569,502,242   7 HPFS/NTFS
/dev/sda7         260,691,968   371,843,071   111,151,104  83 Linux
/dev/sda8         209,491,968   260,689,919    51,197,952  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
16 heads, 63 sectors/track, 3876021 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb2    *          2,048 3,907,029,167 3,907,027,120   5 Extended
/dev/sdb5               4,096 3,907,028,991 3,907,024,896   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1AF0C12DF0C11045                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        4d6b6326-7d4a-472b-8ce5-5e531c90cd52   swap                                     
/dev/sda6        566C0AE26C0ABD2D                       ntfs       Data                          
/dev/sda7        e577649d-d9a4-42fe-a543-506926095f6d   ext4       HOME                          
/dev/sda8        df316cf9-1a0f-4e4d-8400-612376084b5e   ext4       ROOT                          
/dev/sda: PTTYPE="dos" 
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        01CB1E0382AC3490                       ntfs       Music                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext4       (rw,commit=0)
/dev/sda6        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1        /media/sda1              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5        /media/Music             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=2

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

UnsupportedDebug="do not select this" /debug

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
search --no-floppy --fs-uuid --set df316cf9-1a0f-4e4d-8400-612376084b5e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set df316cf9-1a0f-4e4d-8400-612376084b5e
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set df316cf9-1a0f-4e4d-8400-612376084b5e
insmod png
if background_image /usr/share/images/desktop-base/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set df316cf9-1a0f-4e4d-8400-612376084b5e
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=df316cf9-1a0f-4e4d-8400-612376084b5e ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set df316cf9-1a0f-4e4d-8400-612376084b5e
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=df316cf9-1a0f-4e4d-8400-612376084b5e ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set df316cf9-1a0f-4e4d-8400-612376084b5e
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=df316cf9-1a0f-4e4d-8400-612376084b5e ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set df316cf9-1a0f-4e4d-8400-612376084b5e
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=df316cf9-1a0f-4e4d-8400-612376084b5e ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set df316cf9-1a0f-4e4d-8400-612376084b5e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set df316cf9-1a0f-4e4d-8400-612376084b5e
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda8/etc/fstab: ===============================

proc /proc proc nodev,noexec,nosuid 0 0
UUID=df316cf9-1a0f-4e4d-8400-612376084b5e / ext4 errors=remount-ro 0 1
UUID=e577649d-d9a4-42fe-a543-506926095f6d /home ext4 defaults 0 2
UUID=566C0AE26C0ABD2D /media/Data ntfs-3g defaults,locale=en_CA.utf8 0 0
UUID=01CB1E0382AC3490 /media/Music ntfs-3g defaults,locale=en_CA.utf8 0 0
UUID=1AF0C12DF0C11045 /media/sda1 ntfs-3g defaults,locale=en_CA.utf8 0 0
UUID=4d6b6326-7d4a-472b-8ce5-5e531c90cd52 none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

=================== sda8: Location of files loaded by Grub: ===================


 109.9GB: boot/grub/core.img
 122.4GB: boot/grub/grub.cfg
 107.3GB: boot/initrd.img-2.6.35-24-generic
 107.4GB: boot/initrd.img-2.6.35-25-generic
 109.5GB: boot/vmlinuz-2.6.35-24-generic
 109.5GB: boot/vmlinuz-2.6.35-25-generic
 107.4GB: initrd.img
 107.3GB: initrd.img.old
 109.5GB: vmlinuz
 109.5GB: vmlinuz.old[CODE]
```[/CODE]

---

### Post by nm_geo on 2011-03-01
After reading the link in your first message here, i would ask one question did you reboot into windows immediately after taking the 58 GB from the Windows XP partition?  That would have required you to run the windows chkdisk and it would find the new size of the windows.  In fact if you have a windows recovery disk, I would recommend you boot into the CD and run chkdsk even now.  It should not do anything that would be detrimental. I think I will go run chkdsk on my XP partition right now.

Secondly, oldfred is just about the best help you can get on these problems maybe he will visit your latest message here or even the older solved one.  It is good that boot-info-script saw the WindowsXP in sda1 and it might it fact require you do FIXMBR to get it going again, but I would try the others first sudo update-grub and reinstalling the Grub2 before I did the windows fix. Probably not the help you hoped for but that is about all I can come up with right now.

If you do the FIXMBR, you will then need to reinstall the Grub2 for sure from a live USB/CD.

---

### Post by SuperFreak on 2011-03-02
Thanks nm_geo and turtle153 for your help. I used the sudo update-grub command and all is back to normal.

---

