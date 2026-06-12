---
title: "Ubuntu 10.10 won't boot into PAE"
date: 2011-01-13
forum: General Help
---

### Post by Belgadro on 2011-01-13
System

asrock p43de
6gb of ram
750 gb hard drive sata-os drive
120gb hard drive ide-storage
intel q8200 quad core 2.33ghz overclocked to 3 ghz
Hawking hwug1 wifi card 

My problem is that I went to this site...
[http://www.cyberciti.biz/faq/ubuntu-...tion-solution/](http://www.cyberciti.biz/faq/ubuntu-...tion-solution/)

I did what was on this site but when the computer went to reboot it just loops and then gets stuck on a gui os chooser...I think you guys call it the grub....usually says generic ubuntu generic pae memtest...etc....

I can not get ubuntu to boot into pae.	

Message:
..

any solutions greatly appreciated or a redirection to another posting would be helpful...

thank you.

---

### Post by wilee-nilee on 2011-01-13
Your link is not working.

---

### Post by Belgadro on 2011-01-13
[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)


try this one...sorry but the link use to work...

---

### Post by Belgadro on 2011-03-17
Has anyone found an answer...sighs....

---

### Post by wilee-nilee on 2011-03-17
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

I wont be able to help you as I'm busy writing a finals paper, but this information will provide others with some good tools the original link is a 404 so more information is needed. I will take a look later if I can.

---

### Post by Belgadro on 2011-03-31
sorry to everyone for taking so long...I have had alot of homework at school...

```

  	 	 	 	pre { font-family: "Liberation Serif"; }p { margin-bottom: 0.08in; }                  Boot Info Script 0.55    dated February 15th, 2010                      ============================= Boot Info Summary: ==============================   => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in      partition #5 for (,msdos5)/boot/grub.  => Windows is installed in the MBR of /dev/sdb  => No boot loader is installed in the MBR of /dev/sdc  sda1: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:   /bootmgr /Boot/BCD /grldr  sda2: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:  Windows 7     Boot files/dirs:   /Windows/System32/winload.exe  sda3: _________________________________________________________________________      File system:       Extended Partition     Boot sector type:  -     Boot sector info:    sda5: _________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:       Operating System:  Ubuntu 10.10     Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img  sda6: _________________________________________________________________________      File system:       swap     Boot sector type:  -     Boot sector info:    sdb1: _________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:     sdc1: _________________________________________________________________________      File system:       vfat     Boot sector type:  Windows XP: Fat32     Boot sector info:  No errors found in the Boot Parameter Block.     Operating System:       Boot files/dirs:     =========================== Drive/Partition Info: =============================  Drive: sda ___________________ _____________________________________________________  Disk /dev/sda: 750.2 GB, 750156374016 bytes 255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot         Start           End          Size  Id System  /dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS /dev/sda2             206,848 1,045,998,635 1,045,791,788   7 HPFS/NTFS /dev/sda3       1,045,999,614 1,465,147,391   419,147,778   5 Extended /dev/sda5       1,045,999,616 1,448,073,215   402,073,600  83 Linux /dev/sda6       1,448,075,264 1,465,147,391    17,072,128  82 Linux swap / Solaris   Drive: sdb ___________________ _____________________________________________________  Disk /dev/sdb: 120.0 GB, 120034123776 bytes 255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot         Start           End          Size  Id System  /dev/sdb1    *             63   234,436,544   234,436,482   7 HPFS/NTFS   Drive: sdc ___________________ _____________________________________________________  Disk /dev/sdc: 4091 MB, 4091543552 bytes 126 heads, 61 sectors/track, 1039 cylinders, total 7991296 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot         Start           End          Size  Id System  /dev/sdc1               8,192     7,991,295     7,983,104   b W95 FAT32   blkid -c /dev/null: ____________________________________________________________  Device           UUID                                   TYPE       LABEL                           /dev/loop0                                              squashfs                                  /dev/sda1        B654FF6254FF2431                       ntfs       System Reserved                /dev/sda2        06481417481407D7                       ntfs                                      /dev/sda3: PTTYPE="dos"  /dev/sda5        9f627621-aa68-4d6d-8d8e-5f480b932e98   ext4                                      /dev/sda6        63279a9e-e455-43d6-a82b-990fded464f7   swap                                      /dev/sda: PTTYPE="dos"  /dev/sdb1        BCF61E29F61DE504                       ntfs                                      /dev/sdb: PTTYPE="dos"  /dev/sdc1        447E-5ECA                              vfat                                      /dev/sdc: PTTYPE="dos"   ============================ "mount | grep ^/dev  output: ===========================  Device           Mount_Point              Type       Options  aufs             /                        aufs       (rw) /dev/sr0         /cdrom                   iso9660    (ro,noatime) /dev/loop0       /rofs                    squashfs   (ro,noatime) /dev/sdc1        /media/447E-5ECA         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)   =================== sda2: Location of files loaded by Grub: ===================       BTGB: boot/initrd.gz     BTGB: boot/vmlinuz  =========================== sda5/boot/grub/grub.cfg: ===========================  # # DO NOT EDIT THIS FILE # # It is automatically generated by grub-mkconfig using templates # from /etc/grub.d and settings from /etc/default/grub #  ### BEGIN /etc/grub.d/00_header ### if [ -s $prefix/grubenv ]; then   set have_grubenv=true   load_env fi set default="0" if [ "${prev_saved_entry}" ]; then   set saved_entry="${prev_saved_entry}"   save_env saved_entry   set prev_saved_entry=   save_env prev_saved_entry   set boot_once=true fi  function savedefault {   if [ -z "${boot_once}" ]; then     saved_entry="${chosen}"     save_env saved_entry   fi }  function recordfail {   set recordfail=1   if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi }  function load_video {   insmod vbe   insmod vga }  insmod part_msdos insmod ext2 set root='(hd0,msdos5)' search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 if loadfont /usr/share/grub/unicode.pf2 ; then   set gfxmode=640x480   load_video   insmod gfxterm fi terminal_output gfxterm insmod part_msdos insmod ext2 set root='(hd0,msdos5)' search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 set locale_dir=($root)/boot/grub/locale set lang=en insmod gettext if [ "${recordfail}" = 1 ]; then   set timeout=-1 else   set timeout=10 fi ### END /etc/grub.d/00_header ###  ### BEGIN /etc/grub.d/05_debian_theme ### set menu_color_normal=white/black set menu_color_highlight=black/light-gray ### END /etc/grub.d/05_debian_theme ###  ### BEGIN /etc/grub.d/10_linux ### menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=9f627621-aa68-4d6d-8d8e-5f480b932e98 ro   quiet splash 	initrd	/boot/initrd.img-2.6.35-28-generic-pae } menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 	echo	'Loading Linux 2.6.35-28-generic-pae ...' 	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=9f627621-aa68-4d6d-8d8e-5f480b932e98 ro single  	echo	'Loading initial ramdisk ...' 	initrd	/boot/initrd.img-2.6.35-28-generic-pae } menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=9f627621-aa68-4d6d-8d8e-5f480b932e98 ro   quiet splash 	initrd	/boot/initrd.img-2.6.35-28-generic } menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 	echo	'Loading Linux 2.6.35-28-generic ...' 	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=9f627621-aa68-4d6d-8d8e-5f480b932e98 ro single  	echo	'Loading initial ramdisk ...' 	initrd	/boot/initrd.img-2.6.35-28-generic } menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=9f627621-aa68-4d6d-8d8e-5f480b932e98 ro   quiet splash 	initrd	/boot/initrd.img-2.6.35-27-generic-pae } menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 	echo	'Loading Linux 2.6.35-27-generic-pae ...' 	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=9f627621-aa68-4d6d-8d8e-5f480b932e98 ro single  	echo	'Loading initial ramdisk ...' 	initrd	/boot/initrd.img-2.6.35-27-generic-pae } menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=9f627621-aa68-4d6d-8d8e-5f480b932e98 ro   quiet splash 	initrd	/boot/initrd.img-2.6.35-25-generic-pae } menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 	echo	'Loading Linux 2.6.35-25-generic-pae ...' 	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=9f627621-aa68-4d6d-8d8e-5f480b932e98 ro single  	echo	'Loading initial ramdisk ...' 	initrd	/boot/initrd.img-2.6.35-25-generic-pae } menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=9f627621-aa68-4d6d-8d8e-5f480b932e98 ro   quiet splash 	initrd	/boot/initrd.img-2.6.35-24-generic-pae } menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 	echo	'Loading Linux 2.6.35-24-generic-pae ...' 	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=9f627621-aa68-4d6d-8d8e-5f480b932e98 ro single  	echo	'Loading initial ramdisk ...' 	initrd	/boot/initrd.img-2.6.35-24-generic-pae } menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=9f627621-aa68-4d6d-8d8e-5f480b932e98 ro   quiet splash 	initrd	/boot/initrd.img-2.6.35-23-generic-pae } menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 	echo	'Loading Linux 2.6.35-23-generic-pae ...' 	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=9f627621-aa68-4d6d-8d8e-5f480b932e98 ro single  	echo	'Loading initial ramdisk ...' 	initrd	/boot/initrd.img-2.6.35-23-generic-pae } menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=9f627621-aa68-4d6d-8d8e-5f480b932e98 ro   quiet splash 	initrd	/boot/initrd.img-2.6.35-22-generic-pae } menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 	echo	'Loading Linux 2.6.35-22-generic-pae ...' 	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=9f627621-aa68-4d6d-8d8e-5f480b932e98 ro single  	echo	'Loading initial ramdisk ...' 	initrd	/boot/initrd.img-2.6.35-22-generic-pae } menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=9f627621-aa68-4d6d-8d8e-5f480b932e98 ro   quiet splash 	initrd	/boot/initrd.img-2.6.35-22-generic } menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { 	recordfail 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 	echo	'Loading Linux 2.6.35-22-generic ...' 	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=9f627621-aa68-4d6d-8d8e-5f480b932e98 ro single  	echo	'Loading initial ramdisk ...' 	initrd	/boot/initrd.img-2.6.35-22-generic } ### END /etc/grub.d/10_linux ###  ### BEGIN /etc/grub.d/20_linux_xen ### ### END /etc/grub.d/20_linux_xen ###  ### BEGIN /etc/grub.d/20_memtest86+ ### menuentry "Memory test (memtest86+)" { 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 	linux16	/boot/memtest86+.bin } menuentry "Memory test (memtest86+, serial console 115200)" { 	insmod part_msdos 	insmod ext2 	set root='(hd0,msdos5)' 	search --no-floppy --fs-uuid --set 9f627621-aa68-4d6d-8d8e-5f480b932e98 	linux16	/boot/memtest86+.bin console=ttyS0,115200n8 } ### END /etc/grub.d/20_memtest86+ ###  ### BEGIN /etc/grub.d/30_os-prober ### menuentry "Windows 7 (loader) (on /dev/sda1)" { 	insmod part_msdos 	insmod ntfs 	set root='(hd0,msdos1)' 	search --no-floppy --fs-uuid --set b654ff6254ff2431 	chainloader +1 } ### END /etc/grub.d/30_os-prober ###  ### BEGIN /etc/grub.d/40_custom ### # This file provides an easy way to add custom menu entries.  Simply type the # menu entries you want to add after this comment.  Be careful not to change # the 'exec tail' line above. ### END /etc/grub.d/40_custom ###  ### BEGIN /etc/grub.d/41_custom ### if [ -f  $prefix/custom.cfg ]; then   source $prefix/custom.cfg; fi ### END /etc/grub.d/41_custom ###  =============================== sda5/etc/fstab: ===============================  # /etc/fstab: static file system information. # # Use 'blkid -o value -s UUID' to print the universally unique identifier # for a device; this may be used with UUID= as a more robust way to name # devices that works even if disks are added and removed. See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    nodev,noexec,nosuid 0       0 # / was on /dev/sda5 during installation UUID=9f627621-aa68-4d6d-8d8e-5f480b932e98 /               ext4    errors=remount-ro 0       1 # swap was on /dev/sda6 during installation UUID=63279a9e-e455-43d6-a82b-990fded464f7 none            swap    sw              0       0  =================== sda5: Location of files loaded by Grub: ===================    625.8GB: boot/grub/core.img  600.2GB: boot/grub/grub.cfg  630.7GB: boot/initrd.img-2.6.35-22-generic  630.8GB: boot/initrd.img-2.6.35-22-generic-pae  630.7GB: boot/initrd.img-2.6.35-23-generic-pae  630.7GB: boot/initrd.img-2.6.35-24-generic-pae  630.7GB: boot/initrd.img-2.6.35-25-generic-pae  630.8GB: boot/initrd.img-2.6.35-27-generic-pae  630.7GB: boot/initrd.img-2.6.35-28-generic  630.8GB: boot/initrd.img-2.6.35-28-generic-pae  626.0GB: boot/vmlinuz-2.6.35-22-generic  625.9GB: boot/vmlinuz-2.6.35-22-generic-pae  625.9GB: boot/vmlinuz-2.6.35-23-generic-pae  625.9GB: boot/vmlinuz-2.6.35-24-generic-pae  625.9GB: boot/vmlinuz-2.6.35-25-generic-pae  625.9GB: boot/vmlinuz-2.6.35-27-generic-pae  626.0GB: boot/vmlinuz-2.6.35-28-generic  625.9GB: boot/vmlinuz-2.6.35-28-generic-pae  630.7GB: initrd.img  630.7GB: initrd.img.old  625.9GB: vmlinuz  625.9GB: vmlinuz.old 


```

---

### Post by Belgadro on 2011-03-31
this is also from that site I was talking about earlier where the link didn't work....



Ubuntu 4GB Ram Limitation and Solution
by VIVEK GITE on DECEMBER 27, 2008 · 93 COMMENTS

Q. I've total 8 GB RAM installed in my dual boot Ubuntu Linux 8.10 (32 bit) version HP workstation. But free -m command only shows 3291 (3G) memory. How do I use 8GB RAM under Ubuntu Linux?

A. You need to install Physical Address Extension (PAE) aware kernel under 32 bit Ubuntu Linux. It is a feature of x86 and x86-64 processors that allows more than 4 Gigabytes of physical memory to be used in 32-bit systems.

Without PAE kernel, you should see something as follows:
$ free -m

Sample output:

             total       used       free     shared    buffers     cached
Mem:          3291        801       2489          0         95        342
-/+ buffers/cache:        363       2927
Swap:         1906          0       1906
You have two options here as follows:

Option # 1: Use 64 bit Ubuntu Linux

64 bit Linux kernel will take care of 4G or more memory. Just grab latest 64 bit version and install it.

Option #2: Install PAE enabled kernel

Open terminal and type the following command if you are using Ubuntu version Ubuntu v9.04 and earlier:
$ sudo apt-get update
$ sudo sudo apt-get install linux-headers-server linux-image-server linux-server

If you are using Ubuntu v9.10 (Karmic Koala) and above, enter:
$ sudo apt-get install linux-generic-pae linux-headers-generic-pae

Once kernel images installed, just reboot your workstation, type:
$ sudo reboot

After reboot, login into your system and type the following command to verify memory usage:
$ free -m

Sample output:

             total       used       free     shared    buffers     cached
Mem:          8105       1292       6812          0         38        483
-/+ buffers/cache:        770       7334
Swap:         1906          0       1906

---

### Post by Belgadro on 2011-03-31
I wonder if ubuntu 11.04 will be better on pae....

---

