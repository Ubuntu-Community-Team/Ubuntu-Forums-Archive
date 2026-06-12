---
title: "Serious Boot problems."
date: 2010-08-15
forum: General Help
---

### Post by Aterruit on 2010-08-15
Hi, I recently installed ubuntu UE onto my computer. It is a ASUS G73 GX  and now I cannot boot windows, or linux, without first using the  SUPERGRUB Cd. Below is my information from my results.txt PLEASE help  me. Having a sweet computer is useless when you can't use it to it's  full potential. I am using Winblows Enterprise, and Ubuntu UE, what I want to do is Dual boot between them both. Can anyone one walk me through how to do this please ? Any help would be greatly appreciated.

---

### Post by Aterruit on 2010-08-15
I forgot to post the attachment, my apologies. Here it is.

---

### Post by oldfred on 2010-08-15
You get better help if you post the results.txt in code tags per the instructions. Then we can read it inside you post easily.

YOu still have lilo installed in  your MBR.

You have a windows type boot loader (lilo) in the MBR. Lilo like windows  then jumps to the active partition (boot flag). If you want to boot  windows move the boot flag back to sda3.

If you want to boot Ubuntu you have to reinstall grub2. Yours is in  sda1. So from liveCD you should only have to run the red commands below.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Gr...0from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Install MBR from LiveCD, Ubuntu install on sda1 and want grub2 in drive sda's MBR:
Find linux partition, change sda1 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
[COLOR=DarkRed]sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

You grub.cfg does not show windows yet. So after rebooting into Ubuntu. This should add windows:

sudo update-grub

---

### Post by Aterruit on 2010-08-15
I don't know how to post the file in code tags. How do i uninstall lilo? I can boot ubuntu already, what i'd like to do is be able to dual boot. That's what i'm trying to do. It boots ubuntu just fine.

---

### Post by Aterruit on 2010-08-15
How do I remove lilo, and move the boot flag?

---

### Post by oldfred on 2010-08-15
Code tags are auto created when you click on the # sign in the edit panel as you create a post. Copy the text from results.txt into your post. You can highlight with the mouse and click and it will put code tags around whatever you have highlighted. Or you can click on the # and paste the results.txt contents between the tags.

Is your post of results.txt not current. Have you installed grub to the MBR? Post the results of your sudo update-grub.

---

### Post by Aterruit on 2010-08-15
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    78,125,055    78,123,008  83 Linux
/dev/sda2          78,127,102   167,968,767    89,841,666   5 Extended
/dev/sda5          78,127,104   156,250,111    78,123,008   b W95 FAT32
/dev/sda6         156,252,160   167,968,767    11,716,608  82 Linux swap / Solaris
/dev/sda3         167,968,768   168,173,567       204,800   7 HPFS/NTFS
/dev/sda4         168,173,568   312,578,047   144,404,480   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        b50c37ab-4eec-4b57-b0e6-52269b3a43f1   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        F47E5F087E5EC2D2                       ntfs       System Reserved               
/dev/sda4        425A625A5A624B2D                       ntfs                                     
/dev/sda5        173B-AD11                              vfat                                     
/dev/sda6        e7606524-8bbe-4daf-98d3-5a22d121c577   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /windows                 vfat       (rw,utf8,umask=007,gid=46)
/dev/sda3        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /media/CDROM             iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set b50c37ab-4eec-4b57-b0e6-52269b3a43f1
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set b50c37ab-4eec-4b57-b0e6-52269b3a43f1
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
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b50c37ab-4eec-4b57-b0e6-52269b3a43f1
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=b50c37ab-4eec-4b57-b0e6-52269b3a43f1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b50c37ab-4eec-4b57-b0e6-52269b3a43f1
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=b50c37ab-4eec-4b57-b0e6-52269b3a43f1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b50c37ab-4eec-4b57-b0e6-52269b3a43f1
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b50c37ab-4eec-4b57-b0e6-52269b3a43f1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b50c37ab-4eec-4b57-b0e6-52269b3a43f1
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b50c37ab-4eec-4b57-b0e6-52269b3a43f1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b50c37ab-4eec-4b57-b0e6-52269b3a43f1
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b50c37ab-4eec-4b57-b0e6-52269b3a43f1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b50c37ab-4eec-4b57-b0e6-52269b3a43f1
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b50c37ab-4eec-4b57-b0e6-52269b3a43f1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b50c37ab-4eec-4b57-b0e6-52269b3a43f1
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b50c37ab-4eec-4b57-b0e6-52269b3a43f1
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda6 during installation
UUID=e7606524-8bbe-4daf-98d3-5a22d121c577 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  10.8GB: boot/grub/core.img
  12.2GB: boot/grub/grub.cfg
  13.8GB: boot/initrd.img-2.6.32-21-generic
  12.3GB: boot/initrd.img-2.6.32-22-generic
  12.4GB: boot/initrd.img-2.6.32-24-generic
  11.6GB: boot/vmlinuz-2.6.32-21-generic
  12.2GB: boot/vmlinuz-2.6.32-22-generic
   1.8GB: boot/vmlinuz-2.6.32-24-generic
  12.4GB: initrd.img
  13.8GB: initrd.img.old
   1.8GB: vmlinuz
  11.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  4c 0b 00 00 00 00 00 00  5c 0b 00 00 00 00 00 00  |L.......\.......|
00000010  5d 0b 00 00 00 00 00 00  94 0b 00 00 00 00 00 00  |]...............|
00000020  ca 0b 00 00 00 00 00 00  cb 0b 00 00 00 00 00 00  |................|
00000030  cc 0b 00 00 00 00 00 00  48 0c 00 00 00 00 00 00  |........H.......|
00000040  c0 0c 00 00 00 00 00 00  c7 0c 00 00 00 00 00 00  |................|
00000050  c8 0c 00 00 00 00 00 00  ca 0c 00 00 00 00 00 00  |................|
00000060  cb 0c 00 00 00 00 00 00  4a 0d 00 00 00 00 00 00  |........J.......|
00000070  4b 0d 00 00 00 00 00 00  4c 0d 00 00 00 00 00 00  |K.......L.......|
00000080  da 0d 00 00 00 00 00 00  dc 0d 00 00 00 00 00 00  |................|
00000090  dd 0d 00 00 00 00 00 00  de 0d 00 00 00 00 00 00  |................|
000000a0  33 0e 00 00 00 00 00 00  b3 0e 00 00 00 00 00 00  |3...............|
000000b0  dc 0e 00 00 00 00 00 00  dd 0e 00 00 00 00 00 00  |................|
000000c0  43 0f 00 00 00 00 00 00  4d 0f 00 00 00 00 00 00  |C.......M.......|
000000d0  52 0f 00 00 00 00 00 00  57 0f 00 00 00 00 00 00  |R.......W.......|
000000e0  5c 0f 00 00 00 00 00 00  69 0f 00 00 00 00 00 00  |\.......i.......|
000000f0  73 0f 00 00 00 00 00 00  75 0f 00 00 00 00 00 00  |s.......u.......|
00000100  76 0f 00 00 00 00 00 00  77 0f 00 00 00 00 00 00  |v.......w.......|
00000110  78 0f 00 00 00 00 00 00  79 0f 00 00 00 00 00 00  |x.......y.......|
00000120  81 0f 00 00 00 00 00 00  93 0f 00 00 00 00 00 00  |................|
00000130  9d 0f 00 00 00 00 00 00  a2 0f 00 00 00 00 00 00  |................|
00000140  a7 0f 00 00 00 00 00 00  ac 0f 00 00 00 00 00 00  |................|
00000150  b9 0f 00 00 00 00 00 00  26 10 00 00 00 00 00 00  |........&.......|
00000160  00 1e 00 00 00 00 00 00  01 1e 00 00 00 00 00 00  |................|
00000170  02 1e 00 00 00 00 00 00  03 1e 00 00 00 00 00 00  |................|
00000180  04 1e 00 00 00 00 00 00  05 1e 00 00 00 00 00 00  |................|
00000190  06 1e 00 00 00 00 00 00  07 1e 00 00 00 00 00 00  |................|
000001a0  08 1e 00 00 00 00 00 00  09 1e 00 00 00 00 00 00  |................|
000001b0  0a 1e 00 00 00 00 00 00  0b 1e 00 00 00 00 00 fe  |................|
000001c0  ff ff 0b fe ff ff 02 00  00 00 00 10 a8 04 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 10  a8 04 00 d0 b2 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

there you go! I hope I did that right. and no that's not the latest text file. 

here are the results of my grub update:  ```
josh@WARMACHINE:~$ sudo update-grub
[sudo] password for josh: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-24-generic
Found kernel: /boot/vmlinuz-2.6.32-22-generic
Found kernel: /boot/vmlinuz-2.6.32-21-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

Thank you again for everything.

---

### Post by oldfred on 2010-08-15
The update you have shown is for grub legacy's menu.lst  which is not good at finding other operating systems. The boot script does not even show a grub legacy installed anywhere?

But you have grub2 per boot info script?????

You have to reinstall grub2 to the MBR per post #3 from a liveCD.

---

### Post by Aterruit on 2010-08-16
How do I fix that? I lost the link that showed me the application to use. If you tell me what needs to be done and how to do it I can do it. how do I reinstall grub2 to the mbr?

---

### Post by oldfred on 2010-08-16
Did you run the commands in Post #3 which installs grub2 to the MBR. 

But where is grub legacy's menu.lst on a grub update coming from. Do you have an external drive that was not plugged in when you ran the boot info script?

---

### Post by Aterruit on 2010-08-17
I can't even begin to explain how many different commands I've run. I have run every command you've given me so far, along with other commands i've found in other threads. You tell me what is wrong with the situation, and how to correct it, and I will fix it.  What do I do next? My windows is still operational, but only if I force it to boot using the supergrub Cd. ubuntu boots just fine. How do I run that testdisk program again that way I can update my results.txt?

---

### Post by oldfred on 2010-08-17
Just rerun the downloaded copy of boot_info script if you downloaded it into your working system. It will automatically name the second copy results2.txt If you downloaded into liveCD, you will have to redownload it.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

