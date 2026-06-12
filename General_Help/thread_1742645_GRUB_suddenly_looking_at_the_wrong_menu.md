---
title: "GRUB suddenly looking at the wrong menu?"
date: 2011-04-29
forum: General Help
---

### Post by feffer on 2011-04-29
I had my machine set up to use grub-pc to initially show the grub-menu from sdb1 where Ubuntu was installed. I have a custom entry there with the various OSes in the order I prefer set before the automagic ones. This worked fine for several weeks, but now suddenly the grub entries and splash screen from sdb3 are showing up at boot time. I can still boot all OSes from here, but it is not my preferred start screen. I ran the boot_info_script with the following results:```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for Zi.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for 1e.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.

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

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint Debian Edition
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   250,066,943   249,860,096   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
32 heads, 32 sectors/track, 122114 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               1,024    20,482,047    20,481,024  83 Linux
/dev/sdb2          20,482,048    40,963,071    20,481,024  83 Linux
/dev/sdb3          40,963,072    61,444,095    20,481,024  83 Linux
/dev/sdb4          61,444,096   125,044,735    63,600,640   5 Extended
/dev/sdb5          61,444,128   125,044,735    63,600,608  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    20,980,889    20,980,827  82 Linux swap / Solaris
/dev/sdc2          20,980,890 1,069,559,504 1,048,578,615  83 Linux
/dev/sdc3       1,069,559,505 1,488,984,524   419,425,020  83 Linux
/dev/sdc4       1,488,984,525 1,953,520,064   464,535,540   5 Extended
/dev/sdc5       1,488,984,588 1,803,553,289   314,568,702   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D698095B98093C0D                       ntfs       System Reserved               
/dev/sda2        10E00BD4E00BBECA                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        f03511fe-548e-4816-a1fb-760adee0812a   ext4                                     
/dev/sdb3        9003d86b-e083-4835-8289-7fbf028bfc8b   ext4                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        d757dca6-79ca-4860-bf2d-9c1864330791   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        cd0e75e0-88d2-4beb-aa94-404c8569a416   swap                                     
/dev/sdc2        ceefa01b-cebf-4ebb-a110-12a763aa84f2   ext4                                     
/dev/sdc3        2a03e149-2813-4949-8fef-1fe54738bac0   ext4                                     
/dev/sdc4: PTTYPE="dos" 
/dev/sdc5        4FC5827C01361020                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,noatime,errors=remount-ro)
/dev/sdc2        /home/ron/data           ext4       (rw)
/dev/sdc3        /media/vm                ext4       (rw,nosuid,nodev,noatime)
/dev/sdb5        /media/vmssd             ext4       (rw,nosuid,nodev,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set f03511fe-548e-4816-a1fb-760adee0812a
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set f03511fe-548e-4816-a1fb-760adee0812a
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/07_sdb1 ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

## from /etc/grub.d on ubunxps /dev/sdb1

## Tested and works 
#menuentry "Ubuntu 10.04 UUID" {
#set root=(hd1,1)
#linux /vmlinuz root=UUID=f03511fe-548e-4816-a1fb-760adee0812a ro quiet splash
#initrd /initrd.img
#}

menuentry "Ubuntu 10.04 LTS" {
set root=(hd1,1)
linux /vmlinuz root=/dev/sdb1 ro # quiet splash
initrd /initrd.img
}

menuentry "LMDE-64-bit" {
set root=(hd1,3)
linux /vmlinuz root=/dev/sdb3 ro #quiet splash
initrd /initrd.img
}

menuentry "Windows_7" {
insmod ntfs
set root=(hd0,1)
chainloader +1
}

### END /etc/grub.d/07_sdb1 ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set f03511fe-548e-4816-a1fb-760adee0812a
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=f03511fe-548e-4816-a1fb-760adee0812a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set f03511fe-548e-4816-a1fb-760adee0812a
	echo	'Loading Linux 2.6.32-31-generic ...'
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=f03511fe-548e-4816-a1fb-760adee0812a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set f03511fe-548e-4816-a1fb-760adee0812a
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=f03511fe-548e-4816-a1fb-760adee0812a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set f03511fe-548e-4816-a1fb-760adee0812a
	echo	'Loading Linux 2.6.32-30-generic ...'
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=f03511fe-548e-4816-a1fb-760adee0812a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set f03511fe-548e-4816-a1fb-760adee0812a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set f03511fe-548e-4816-a1fb-760adee0812a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d698095b98093c0d
	chainloader +1
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-amd64 (on /dev/sdb3)" {
	insmod ext2
	set root='(hd1,3)'
	search --no-floppy --fs-uuid --set 9003d86b-e083-4835-8289-7fbf028bfc8b
	linux /boot/vmlinuz-2.6.32-5-amd64 root=UUID=9003d86b-e083-4835-8289-7fbf028bfc8b ro
	initrd /boot/initrd.img-2.6.32-5-amd64
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-amd64 (recovery mode) (on /dev/sdb3)" {
	insmod ext2
	set root='(hd1,3)'
	search --no-floppy --fs-uuid --set 9003d86b-e083-4835-8289-7fbf028bfc8b
	linux /boot/vmlinuz-2.6.32-5-amd64 root=UUID=9003d86b-e083-4835-8289-7fbf028bfc8b ro single
	initrd /boot/initrd.img-2.6.32-5-amd64
}
### END /etc/grub.d/30_os-prober ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information for Ubuntu 10.04 LTS on SSD /dev/sdb1
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc      /proc       proc       nodev,noexec,nosuid       0       0

# Root for ubunxps on SSD /dev/sdb1
UUID=f03511fe-548e-4816-a1fb-760adee0812a     /     ext4     errors=remount-ro,noatime     0     1

### No Swap on this 64GB SSD -- maybe not needed with 12GB of ram?? ###
# swap was on /dev/sdc1 == maybe issues w/o it? -- this is swap on 1TB hdd
#UUID=cd0e75e0-88d2-4beb-aa94-404c8569a416     none     swap     sw     0     0

# Common ext4 data partition for linux only on /dev/sdc2
UUID=ceefa01b-cebf-4ebb-a110-12a763aa84f2     /home/ron/data     ext4    defaults     0     0

# Common data partition for linux and windows -- this is an ntfs partition on /dev/sdc5 -- 1TB hdd
UUID=4FC5827C01361020    /media/ntfs_data     ntfs-3g     noauto,defaults,uid=1000,gid=1200,fmask=0113,dmask=0022,locale=US.utf8     0     0 
# dmask=027 removes "x" for others, or world can't open dir

# Common vm partition (and other stuff) on /dev/sdc3
UUID=2a03e149-2813-4949-8fef-1fe54738bac0     /media/vm   ext4     auto,users,rw,exec,noatime     0     0

# VM partition on SSD /dev/sdb5 
UUID=d757dca6-79ca-4860-bf2d-9c1864330791     /media/vmssd   ext4     auto,users,rw,exec,noatime     0     0

# mintxps on /dev/sdb3 on SSD
UUID=9003d86b-e083-4835-8289-7fbf028bfc8b    /media/mintxps    ext4     noauto,defaults,noatime     0     0

# CIFS share for Sheeva backups etc
//sheeva/data-srv          /media/data-srv  cifs     noauto,defaults,rw,credentials=/root/.cifs_creds 

## Depreciated and disabled
# CIFS share for Sheeva backups on winbak -- the ntfs partition
#//sheeva/win_bak          /media/win_bak  cifs     noauto,defaults,rw,credentials=/root/.cifs_creds 

## Windows_7 partitons -- generally don't use -- if really needed, uncomment and mount
## Change options as needed. IE to give ron ownership add: ,uid=1000,gid=1000
# Win7 OS on /dev/sda2  128GB-SSD
UUID=10E00BD4E00BBECA    /media/win7   ntfs-3g   noauto,users,errors=remount-ro,dmask=0022,fmask=0133,locale=US.utf8,noatime,uid=1000,gid=1000    0     0





=================== sdb1: Location of files loaded by Grub: ===================


   6.6GB: boot/grub/core.img
   6.9GB: boot/grub/grub.cfg
   3.6GB: boot/initrd.img-2.6.32-30-generic
   4.2GB: boot/initrd.img-2.6.32-31-generic
   6.9GB: boot/vmlinuz-2.6.32-30-generic
   7.1GB: boot/vmlinuz-2.6.32-31-generic
   4.2GB: initrd.img
   3.6GB: initrd.img.old
   7.1GB: vmlinuz
   6.9GB: vmlinuz.old

=========================== sdb3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos3)'
search --no-floppy --fs-uuid --set=root 9003d86b-e083-4835-8289-7fbf028bfc8b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos3)'
search --no-floppy --fs-uuid --set=root 9003d86b-e083-4835-8289-7fbf028bfc8b
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos3)'
search --no-floppy --fs-uuid --set=root 9003d86b-e083-4835-8289-7fbf028bfc8b
insmod png
if background_image /boot/grub/linuxmint.png; then
  true
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos3)'
search --no-floppy --fs-uuid --set=root 9003d86b-e083-4835-8289-7fbf028bfc8b
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'LinuxMint GNU/Linux, with Linux 2.6.32-5-amd64' --class linuxmint --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos3)'
	search --no-floppy --fs-uuid --set=root 9003d86b-e083-4835-8289-7fbf028bfc8b
	echo	'Loading Linux 2.6.32-5-amd64 ...'
	linux	/boot/vmlinuz-2.6.32-5-amd64 root=UUID=9003d86b-e083-4835-8289-7fbf028bfc8b ro  
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-5-amd64
}
menuentry 'LinuxMint GNU/Linux, with Linux 2.6.32-5-amd64 (recovery mode)' --class linuxmint --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos3)'
	search --no-floppy --fs-uuid --set=root 9003d86b-e083-4835-8289-7fbf028bfc8b
	echo	'Loading Linux 2.6.32-5-amd64 ...'
	linux	/boot/vmlinuz-2.6.32-5-amd64 root=UUID=9003d86b-e083-4835-8289-7fbf028bfc8b ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-5-amd64
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root D698095B98093C0D
	chainloader +1
}
menuentry "Ubuntu 10.04 LTS (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f03511fe-548e-4816-a1fb-760adee0812a
	linux /vmlinuz root=/dev/sdb1 ro # quiet splash
	initrd /initrd.img
}
menuentry "LMDE-64-bit (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f03511fe-548e-4816-a1fb-760adee0812a
	linux /vmlinuz root=/dev/sdb3 ro #quiet splash
	initrd /initrd.img
}
menuentry "Ubuntu, with Linux 2.6.32-31-generic (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f03511fe-548e-4816-a1fb-760adee0812a
	linux /boot/vmlinuz-2.6.32-31-generic root=UUID=f03511fe-548e-4816-a1fb-760adee0812a ro quiet splash
	initrd /boot/initrd.img-2.6.32-31-generic
}
menuentry "Ubuntu, with Linux 2.6.32-31-generic (recovery mode) (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f03511fe-548e-4816-a1fb-760adee0812a
	linux /boot/vmlinuz-2.6.32-31-generic root=UUID=f03511fe-548e-4816-a1fb-760adee0812a ro single
	initrd /boot/initrd.img-2.6.32-31-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f03511fe-548e-4816-a1fb-760adee0812a
	linux /boot/vmlinuz-2.6.32-30-generic root=UUID=f03511fe-548e-4816-a1fb-760adee0812a ro quiet splash
	initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (recovery mode) (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root f03511fe-548e-4816-a1fb-760adee0812a
	linux /boot/vmlinuz-2.6.32-30-generic root=UUID=f03511fe-548e-4816-a1fb-760adee0812a ro single
	initrd /boot/initrd.img-2.6.32-30-generic
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

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information. on /dev/sdb3 SSD  LMDE 10 
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc      /proc       proc       nodev,noexec,nosuid       0       0

# Root for mintxps on SSD /dev/sdb3
UUID=9003d86b-e083-4835-8289-7fbf028bfc8b	/	ext4	rw,errors=remount-ro,noatime	0	0

### No Swap on this 64GB SSD -- maybe not needed with 12GB of ram?? ###
# swap was on /dev/sdc1 == maybe issues w/o it? -- this is swap on 1TB hdd
#UUID=cd0e75e0-88d2-4beb-aa94-404c8569a416     none     swap     sw     0     0

# Common ext4 data partition for linux only on /dev/sdc2
UUID=ceefa01b-cebf-4ebb-a110-12a763aa84f2     /home/ron/data     ext4    defaults     0     0

# Common data partition for linux and windows -- this is an ntfs partition on /dev/sdc5
UUID=4FC5827C01361020    /media/ntfs_data     ntfs-3g     noauto,defaults,uid=1000,gid=1200,fmask=0113,dmask=0022,locale=US.utf8     0     0 
# dmask=027 removes "x" for others, or world can't open dir

# Common vm partition (and other stuff) on /dev/sdc3
UUID=2a03e149-2813-4949-8fef-1fe54738bac0     /media/vm   ext4     auto,users,rw,exec,noatime     0     0

# VM partition on SSD /dev/sdb5 
UUID=d757dca6-79ca-4860-bf2d-9c1864330791     /media/vmssd   ext4     auto,users,rw,exec,noatime     0     0

# ubunxps on /dev/sdb1 on SSD
UUID=f03511fe-548e-4816-a1fb-760adee0812a    /media/ubunxps    ext4     noauto,defaults,noatime     0     0

# CIFS share for Sheeva backups etc
//sheeva/data-srv          /media/data-srv  cifs     noauto,defaults,rw,credentials=/root/.cifs_creds 

## Depreciated and disabled
# CIFS share for Sheeva backups on winbak -- the ntfs partition
#//sheeva/winbak          /media/winbak  cifs     noauto,defaults,rw,credentials=/root/.cifs_creds 

## Windows_7 partitons -- generally don't use -- if really needed, uncomment and mount
## Change options as needed. IE to give ron ownership add: ,uid=1000,gid=1000
# Win7 OS on /dev/sda2  128GB-SSD
UUID=10E00BD4E00BBECA    /media/win7   ntfs-3g   noauto,users,errors=remount-ro,dmask=0022,fmask=0133,locale=US.utf8,noatime,uid=1000,gid=1000    0     0

 

=================== sdb3: Location of files loaded by Grub: ===================


  27.6GB: boot/grub/core.img
  23.7GB: boot/grub/grub.cfg
  30.3GB: boot/initrd.img-2.6.32-5-amd64
  24.3GB: boot/vmlinuz-2.6.32-5-amd64
  30.3GB: initrd.img
  24.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc4

00000000  49 49 49 49 49 49 49 49  49 49 49 49 49 48 48 48  |IIIIIIIIIIIIIHHH|
00000010  48 48 48 48 48 48 48 48  48 48 48 48 48 48 48 48  |HHHHHHHHHHHHHHHH|
00000020  48 48 48 48 48 49 48 48  48 4a 44 3b 32 34 2b 2b  |HHHHHIHHHJD;24++|
00000030  35 3d 50 41 4a 49 52 57  53 53 53 53 52 52 52 52  |5=PAJIRWSSSSRRRR|
00000040  52 52 52 52 58 49 49 48  48 48 48 48 48 48 48 48  |RRRRXIIHHHHHHHHH|
00000050  48 54 54 4b 4b 4a 4a 4a  4a 55 4c 4c 4c 4c 4e 42  |HTTKKJJJJULLLLNB|
00000060  41 41 41 4f 44 43 43 43  3a 3a 39 39 39 45 45 3b  |AAAODCCC::999EE;|
00000070  3b 3b 3b 46 3d 3d 33 32  35 34 34 34 34 35 2a 29  |;;;F==32544445*)|
00000080  1d 12 12 12 12 12 12 12  12 12 12 12 12 12 12 12  |................|
00000090  12 12 12 12 12 12 12 12  12 12 12 12 12 12 12 12  |................|
000000a0  12 12 12 12 12 12 13 14  2f 24 2d 34 3b 43 41 4f  |......../$-4;CAO|
000000b0  4f 41 3a 3d 34 2b 36 2e  36 36 36 36 36 36 2b 36  |OA:=4+6.666666+6|
000000c0  2d 2d 37 2d 36 3f 44 52  08 59 51 51 51 51 51 51  |--7-6?DR.YQQQQQQ|
000000d0  51 51 51 51 51 51 51 51  51 51 57 57 57 57 57 57  |QQQQQQQQQQWWWWWW|
000000e0  57 57 57 57 57 57 57 57  57 57 57 57 57 57 57 53  |WWWWWWWWWWWWWWWS|
000000f0  53 53 52 52 52 52 52 52  52 52 52 52 52 52 52 52  |SSRRRRRRRRRRRRRR|
00000100  52 52 52 52 52 52 52 52  52 52 52 52 52 52 52 52  |RRRRRRRRRRRRRRRR|
00000110  52 52 52 52 52 49 4c 46  2c 2b 34 34 34 34 34 34  |RRRRRILF,+444444|
00000120  2b 32 39 4c 48 49 52 49  49 49 49 49 49 49 49 49  |+29LHIRIIIIIIIII|
00000130  49 49 49 49 49 49 49 49  49 49 48 48 48 48 48 48  |IIIIIIIIIIHHHHHH|
00000140  48 48 48 48 48 48 48 48  48 48 48 48 48 48 48 48  |HHHHHHHHHHHHHHHH|
00000150  49 49 58 58 52 48 42 3c  35 36 2d 2e 2b 35 3d 3b  |IIXXRHB<56-.+5=;|
00000160  39 43 41 55 48 53 51 59  07 51 53 52 52 52 52 52  |9CAUHSQY.QSRRRRR|
00000170  52 52 58 49 49 49 49 48  48 48 48 48 48 48 48 54  |RRXIIIIHHHHHHHHT|
00000180  54 54 4b 4b 4a 4a 4a 55  4d 4c 4c 4c 4c 4e 41 41  |TTKKJJJUMLLLLNAA|
00000190  41 4f 44 43 43 43 50 3a  39 39 39 45 45 3c 3b 3b  |AODCCCP:999EE<;;|
000001a0  3b 46 3d 3d 33 32 32 32  35 34 34 2a 2a 1f 20 1d  |;F==3222544**. .|
000001b0  1d 12 12 12 12 12 12 12  12 12 12 12 12 12 00 fe  |................|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 fe ef bf 12 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```I tried reinstalling grub to sdb1, but no change. How can I get my original setup back, and what could have happened to change it.

thx,
feffer

---

### Post by wilee-nilee on 2011-04-29
Take a look at this thread for a persistent fix.
[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

---

### Post by feffer on 2011-04-29
> Take a look at this thread for a persistent fix.
[http://ubuntuforums.org/showthread.p...3#post10340183](http://ubuntuforums.org/showthread.p...3#post10340183)I looked this over pretty well and I'm not sure it solves my issue. 

In a nutshell, grub on ubuntu, sdb1 WAS the controlling one, but now grub on linux2, sdb3 IS controlling the boot. Perhaps an update caused it to switch, I don't know, but something did. If the script mentioned above can revert to making ubuntu, sdb1 the controller that would be a fix. Can it?

thx,
feffer

---

### Post by wilee-nilee on 2011-04-29
> **feffer said:**
> I looked this over pretty well and I'm not sure it solves my issue. 

In a nutshell, grub on ubuntu, sdb1 WAS the controlling one, but now grub on linux2, sdb3 IS controlling the boot. Perhaps an update caused it to switch, I don't know, but something did. If the script mentioned above can revert to making ubuntu, sdb1 the controller that would be a fix. Can it?

thx,
feffer

Oh yes lets give sdb1 control again boot into the sdb1 OS then in the terminal run 
```
sudo grub-install /dev/sdb
```
then 
```
sudo update-grub
```

If your original modifications are there you should see them.

Notice the sdb only in the command we are just loading the MBR.

---

### Post by feffer on 2011-04-30
OK, thx wilee-nilee, that did the trick.

---

