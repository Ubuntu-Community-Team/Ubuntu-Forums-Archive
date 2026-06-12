---
title: "Mandriva and PCLinuxOS get KP with grub2"
date: 2010-09-13
forum: General Help
---

### Post by beastrace91 on 2010-09-13
Howdy All,

So I currently have an Ubuntu/Mandriva/PCLinuxOS multiboot setup on my system. After I installed the latter two I setup Ubuntu's grub2 to be my default boot manager. After running my ```
sudo update-grub
``` command it successfully found and added entries for Mandriva and PCLinuxOS, however upon trying to boot into either of these distros (selecting them from the menu) I get some terminal output that ultimately ends in kernel panic. 

Booting into Ubuntu works fine, any suggestions for what I can do to try and resolve the issue?

Regards,
~Jeff

---

### Post by oldfred on 2010-09-13
Post this, so we can see exactly what the issue may be:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

The grub osprober copies entries from the menu.lst of the other installs. I think mandriva was one who prefaced each line with the drive,partition but that is in old grub numbering and from grub2 you need new partition numbering. You can move boot stanzas into 40_custom and edit there.

---

### Post by beastrace91 on 2010-09-13
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 448212520 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu maverick (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 691594536 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #5 for (,gpt5)/boot/grub.
    Operating System:  Linux Mint Debian Edition
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Chakra Linux () ()
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda7 and 
                       looks at sector 793551360 on boot drive #1 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #7 for 
                       /boot/grub/grub.conf.
    Operating System:  Fedora release 13 (Goddard) 
                       Kernel on an ()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda8 and 
                       looks at sector 845164288 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #8 for 
                       /boot/grub/menu.lst.
    Operating System:  Mandriva Linux release 2010.1 
                       (Official) for i586 Kernel 2.6.33.5-desktop586-2mnb on 
                       a Dual-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda9 and 
                       looks at sector 896341088 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #9 for 
                       /boot/grub/menu.lst.
    Operating System:  Welcome to openSUSE 11.3 "Teal" 
                       - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda10 and 
                       looks at sector 985274624 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #10 for 
                       /boot/grub/menu.lst.
    Operating System:  PCLinuxOS release 2010 
                       (PCLinuxOS) for i586 Kernel 2.6.33.5-pclos1.bfs on a 
                       Dual-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda13: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda14: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda15: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 1,250,263,727 1,250,263,727  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1           2,048     8,355,839     8,353,792 Linux Swap
/dev/sda2       8,355,840   431,063,039   422,707,200 Linux or Data
/dev/sda3     431,063,040   635,863,039   204,800,000 Linux or Data
/dev/sda4     635,863,040   687,063,039    51,200,000 Linux or Data
/dev/sda5     687,063,040   738,263,039    51,200,000 Linux or Data
/dev/sda6     738,263,040   789,463,039    51,200,000 Linux or Data
/dev/sda7     789,463,040   840,663,039    51,200,000 System/Boot Partition
/dev/sda8     840,663,040   891,863,039    51,200,000 Linux or Data
/dev/sda9     891,863,040   943,063,039    51,200,000 Linux or Data
/dev/sda10    943,063,040   994,263,039    51,200,000 Linux or Data
/dev/sda11    994,263,040 1,045,463,039    51,200,000 Linux or Data
/dev/sda12  1,045,463,040 1,094,291,455    48,828,416 Linux or Data
/dev/sda13  1,094,291,456 1,143,119,871    48,828,416 Linux or Data
/dev/sda14  1,143,119,872 1,191,948,287    48,828,416 Linux or Data
/dev/sda15  1,191,948,288 1,250,263,039    58,314,752 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/ramzswap0                                          swap                                     
/dev/sda1        0fdf0b6e-2600-493b-b17a-bd653ed1ffe5   swap                                     
/dev/sda10       658db7c4-b01a-40f6-962a-c6d30cad8417   ext4       PCLinuxOS                     
/dev/sda11       4e792fce-8080-4b8c-aeaa-0bb7ee88ad60   ext4       Austrumi                      
/dev/sda12       7b813574-e9a2-4142-8fd3-9c5cd4a621ea   ext4       Lunar                         
/dev/sda13       0ea09ec5-d4ce-4958-8a1e-0ce69423f7fd   ext4                                     
/dev/sda14       22850321-5203-4a70-96f1-42f6a9aefe8c   ext4                                     
/dev/sda15       37e2c7a5-d1b0-4c22-85db-df6fadb8b94a   ext4                                     
/dev/sda2        66b8b69d-d350-4567-87dc-36e4313b0ba8   ext4       Storage                       
/dev/sda3        f4555bd4-29dd-439d-bb3b-0d5e9d521b07   ext4       Pinguy                        
/dev/sda4        70f17fcf-2b30-4a4f-bcd5-a80834943351   ext4       Ubuntu                        
/dev/sda5        34e053f0-2e43-4f01-999b-8070b5057986   ext4       Mint                          
/dev/sda6        fc8f6872-99a2-4236-82bb-2aaf3d4abb22   ext4       Chakra                        
/dev/sda7        d9673816-d0ac-49f7-ad55-4f2920bdd32e   ext4       Fedora                        
/dev/sda8        c36d8965-5da4-4de6-9aaa-523a7c6b3f53   ext4       Mandriva                      
/dev/sda9        b5657be9-3ead-40d0-bb63-2bde42937bc5   ext4       OpenSUSE                      
/dev/sda: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /mnt/Data                ext4       (rw)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set f4555bd4-29dd-439d-bb3b-0d5e9d521b07
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set f4555bd4-29dd-439d-bb3b-0d5e9d521b07
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
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set f4555bd4-29dd-439d-bb3b-0d5e9d521b07
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=f4555bd4-29dd-439d-bb3b-0d5e9d521b07 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set f4555bd4-29dd-439d-bb3b-0d5e9d521b07
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=f4555bd4-29dd-439d-bb3b-0d5e9d521b07 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set f4555bd4-29dd-439d-bb3b-0d5e9d521b07
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set f4555bd4-29dd-439d-bb3b-0d5e9d521b07
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "linux (on /dev/sda10)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 658db7c4-b01a-40f6-962a-c6d30cad8417
	linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=658db7c4-b01a-40f6-962a-c6d30cad8417 vmalloc=256M resume=UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 splash=silent vga=788
	initrd (hd0,9)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda10)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 658db7c4-b01a-40f6-962a-c6d30cad8417
	linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=658db7c4-b01a-40f6-962a-c6d30cad8417 vmalloc=256M resume=UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5
	initrd (hd0,9)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda10)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 658db7c4-b01a-40f6-962a-c6d30cad8417
	linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=658db7c4-b01a-40f6-962a-c6d30cad8417 failsafe vmalloc=256M
	initrd (hd0,9)/boot/initrd.img
}
menuentry "Ubuntu, with Linux 2.6.35-19-generic (on /dev/sda4)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 70f17fcf-2b30-4a4f-bcd5-a80834943351
	linux /boot/vmlinuz-2.6.35-19-generic root=UUID=70f17fcf-2b30-4a4f-bcd5-a80834943351 ro quiet splash
	initrd /boot/initrd.img-2.6.35-19-generic
}
menuentry "Ubuntu, with Linux 2.6.35-19-generic (recovery mode) (on /dev/sda4)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 70f17fcf-2b30-4a4f-bcd5-a80834943351
	linux /boot/vmlinuz-2.6.35-19-generic root=UUID=70f17fcf-2b30-4a4f-bcd5-a80834943351 ro single
	initrd /boot/initrd.img-2.6.35-19-generic
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34e053f0-2e43-4f01-999b-8070b5057986
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=34e053f0-2e43-4f01-999b-8070b5057986 ro quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 34e053f0-2e43-4f01-999b-8070b5057986
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=34e053f0-2e43-4f01-999b-8070b5057986 ro single
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Chakra GNU/Linux (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fc8f6872-99a2-4236-82bb-2aaf3d4abb22
	linux /boot/vmlinuz26 resume=/dev/disk/by-uuid/0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 root=/dev/disk/by-uuid/fc8f6872-99a2-4236-82bb-2aaf3d4abb22 ro
	initrd /boot/kernel26.img
}
menuentry "Chakra GNU/Linux Fallback (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fc8f6872-99a2-4236-82bb-2aaf3d4abb22
	linux /boot/vmlinuz26 resume=/dev/disk/by-uuid/0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 root=/dev/disk/by-uuid/fc8f6872-99a2-4236-82bb-2aaf3d4abb22 ro
	initrd /boot/kernel26-fallback.img
}
menuentry "Fedora (2.6.34.6-54.fc13.i686) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set d9673816-d0ac-49f7-ad55-4f2920bdd32e
	linux /boot/vmlinuz-2.6.34.6-54.fc13.i686 ro root=UUID=d9673816-d0ac-49f7-ad55-4f2920bdd32e rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet nouveau.modeset=0 rdblacklist=nouveau rdblacklist=nouveau
	initrd /boot/initramfs-2.6.34.6-54.fc13.i686.img
}
menuentry "Fedora (2.6.33.3-85.fc13.i686) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set d9673816-d0ac-49f7-ad55-4f2920bdd32e
	linux /boot/vmlinuz-2.6.33.3-85.fc13.i686 ro root=UUID=d9673816-d0ac-49f7-ad55-4f2920bdd32e rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet rdblacklist=nouveau
	initrd /boot/initramfs-2.6.33.3-85.fc13.i686.img
}
menuentry "linux (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set c36d8965-5da4-4de6-9aaa-523a7c6b3f53
	linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=c36d8965-5da4-4de6-9aaa-523a7c6b3f53 resume=UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 splash=silent vga=788
	initrd (hd0,7)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set c36d8965-5da4-4de6-9aaa-523a7c6b3f53
	linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=c36d8965-5da4-4de6-9aaa-523a7c6b3f53 resume=UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5
	initrd (hd0,7)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,8)'
	search --no-floppy --fs-uuid --set c36d8965-5da4-4de6-9aaa-523a7c6b3f53
	linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=c36d8965-5da4-4de6-9aaa-523a7c6b3f53 failsafe
	initrd (hd0,7)/boot/initrd.img
}
menuentry "openSUSE 11.3 (on /dev/sda9)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set b5657be9-3ead-40d0-bb63-2bde42937bc5
	linux /boot/vmlinuz-2.6.34-12-default root=/dev/disk/by-id/ata-WDC_WD6400BEVT-00A0RT0_WD-WX40A99L8069-part9 resume=/dev/disk/by-id/ata-WDC_WD6400BEVT-00A0RT0_WD-WX40A99L8069-part1 splash=silent quiet showopts vga=0x314
	initrd /boot/initrd-2.6.34-12-default
}
menuentry "Failsafe -- openSUSE 11.3 (on /dev/sda9)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set b5657be9-3ead-40d0-bb63-2bde42937bc5
	linux /boot/vmlinuz-2.6.34-12-default root=/dev/disk/by-id/ata-WDC_WD6400BEVT-00A0RT0_WD-WX40A99L8069-part9 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x314
	initrd /boot/initrd-2.6.34-12-default
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=f4555bd4-29dd-439d-bb3b-0d5e9d521b07 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 none            swap    sw              0       0
/dev/sda2	/mnt/Data	ext4	defaults	0	0

=================== sda3: Location of files loaded by Grub: ===================


 229.4GB: boot/grub/core.img
 246.6GB: boot/grub/grub.cfg
 221.8GB: boot/initrd.img-2.6.32-24-generic
 229.4GB: boot/vmlinuz-2.6.32-24-generic
 221.8GB: initrd.img
 229.4GB: vmlinuz

=========================== sda4/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(hd0,gpt4)'
search --no-floppy --fs-uuid --set 70f17fcf-2b30-4a4f-bcd5-a80834943351
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(hd0,gpt4)'
search --no-floppy --fs-uuid --set 70f17fcf-2b30-4a4f-bcd5-a80834943351
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
menuentry 'Ubuntu, with Linux 2.6.35-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt4)'
	search --no-floppy --fs-uuid --set 70f17fcf-2b30-4a4f-bcd5-a80834943351
	linux	/boot/vmlinuz-2.6.35-19-generic root=UUID=70f17fcf-2b30-4a4f-bcd5-a80834943351 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt4)'
	search --no-floppy --fs-uuid --set 70f17fcf-2b30-4a4f-bcd5-a80834943351
	echo	'Loading Linux 2.6.35-19-generic ...'
	linux	/boot/vmlinuz-2.6.35-19-generic root=UUID=70f17fcf-2b30-4a4f-bcd5-a80834943351 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt4)'
	search --no-floppy --fs-uuid --set 70f17fcf-2b30-4a4f-bcd5-a80834943351
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt4)'
	search --no-floppy --fs-uuid --set 70f17fcf-2b30-4a4f-bcd5-a80834943351
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
menuentry "Memory test (memtest86+, experimental multiboot)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt4)'
	search --no-floppy --fs-uuid --set 70f17fcf-2b30-4a4f-bcd5-a80834943351
	multiboot	/boot/memtest86+_multiboot.bin
}
menuentry "Memory test (memtest86+, serial console 115200, experimental multiboot)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt4)'
	search --no-floppy --fs-uuid --set 70f17fcf-2b30-4a4f-bcd5-a80834943351
	multiboot	/boot/memtest86+_multiboot.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (on /dev/sda5)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt5)'
	search --no-floppy --fs-uuid --set 34e053f0-2e43-4f01-999b-8070b5057986
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=34e053f0-2e43-4f01-999b-8070b5057986 ro quiet
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (recovery mode) (on /dev/sda5)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt5)'
	search --no-floppy --fs-uuid --set 34e053f0-2e43-4f01-999b-8070b5057986
	linux /boot/vmlinuz-2.6.32-5-686 root=UUID=34e053f0-2e43-4f01-999b-8070b5057986 ro single
	initrd /boot/initrd.img-2.6.32-5-686
}
menuentry "Chakra GNU/Linux (on /dev/sda6)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt6)'
	search --no-floppy --fs-uuid --set fc8f6872-99a2-4236-82bb-2aaf3d4abb22
	linux /boot/vmlinuz26 resume=/dev/disk/by-uuid/0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 root=/dev/disk/by-uuid/fc8f6872-99a2-4236-82bb-2aaf3d4abb22 ro
	initrd /boot/kernel26.img
}
menuentry "Chakra GNU/Linux Fallback (on /dev/sda6)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt6)'
	search --no-floppy --fs-uuid --set fc8f6872-99a2-4236-82bb-2aaf3d4abb22
	linux /boot/vmlinuz26 resume=/dev/disk/by-uuid/0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 root=/dev/disk/by-uuid/fc8f6872-99a2-4236-82bb-2aaf3d4abb22 ro
	initrd /boot/kernel26-fallback.img
}
menuentry "Fedora (2.6.34.6-54.fc13.i686) (on /dev/sda7)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt7)'
	search --no-floppy --fs-uuid --set d9673816-d0ac-49f7-ad55-4f2920bdd32e
	linux /boot/vmlinuz-2.6.34.6-54.fc13.i686 ro root=UUID=d9673816-d0ac-49f7-ad55-4f2920bdd32e rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet nouveau.modeset=0 rdblacklist=nouveau rdblacklist=nouveau
	initrd /boot/initramfs-2.6.34.6-54.fc13.i686.img
}
menuentry "Fedora (2.6.33.3-85.fc13.i686) (on /dev/sda7)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt7)'
	search --no-floppy --fs-uuid --set d9673816-d0ac-49f7-ad55-4f2920bdd32e
	linux /boot/vmlinuz-2.6.33.3-85.fc13.i686 ro root=UUID=d9673816-d0ac-49f7-ad55-4f2920bdd32e rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet rdblacklist=nouveau
	initrd /boot/initramfs-2.6.33.3-85.fc13.i686.img
}
menuentry "linux (on /dev/sda8)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt8)'
	search --no-floppy --fs-uuid --set c36d8965-5da4-4de6-9aaa-523a7c6b3f53
	linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=c36d8965-5da4-4de6-9aaa-523a7c6b3f53 resume=UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 splash=silent vga=788
	initrd (hd0,7)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda8)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt8)'
	search --no-floppy --fs-uuid --set c36d8965-5da4-4de6-9aaa-523a7c6b3f53
	linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=c36d8965-5da4-4de6-9aaa-523a7c6b3f53 resume=UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5
	initrd (hd0,7)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda8)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt8)'
	search --no-floppy --fs-uuid --set c36d8965-5da4-4de6-9aaa-523a7c6b3f53
	linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=c36d8965-5da4-4de6-9aaa-523a7c6b3f53 failsafe
	initrd (hd0,7)/boot/initrd.img
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

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=70f17fcf-2b30-4a4f-bcd5-a80834943351 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 none            swap    sw              0       0
/dev/sda2 /mnt/Data ext4	defaults	0	0

=================== sda4: Location of files loaded by Grub: ===================


 332.1GB: boot/grub/core.img
 349.4GB: boot/grub/grub.cfg
 349.4GB: boot/initrd.img-2.6.35-19-generic
 325.9GB: boot/vmlinuz-2.6.35-19-generic
 349.4GB: initrd.img
 325.9GB: vmlinuz

=========================== sda5/boot/grub/grub.cfg: ===========================

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

insmod part_gpt
insmod ext2
set root='(hd0,gpt5)'
search --no-floppy --fs-uuid --set 34e053f0-2e43-4f01-999b-8070b5057986
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(hd0,gpt5)'
search --no-floppy --fs-uuid --set 34e053f0-2e43-4f01-999b-8070b5057986
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_gpt
insmod ext2
set root='(hd0,gpt5)'
search --no-floppy --fs-uuid --set 34e053f0-2e43-4f01-999b-8070b5057986
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
menuentry 'LinuxMint GNU/Linux, with Linux 2.6.32-5-686' --class linuxmint --class gnu-linux --class gnu --class os {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt5)'
	search --no-floppy --fs-uuid --set 34e053f0-2e43-4f01-999b-8070b5057986
	echo	'Loading Linux 2.6.32-5-686 ...'
	linux	/boot/vmlinuz-2.6.32-5-686 root=UUID=34e053f0-2e43-4f01-999b-8070b5057986 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-5-686
}
menuentry 'LinuxMint GNU/Linux, with Linux 2.6.32-5-686 (recovery mode)' --class linuxmint --class gnu-linux --class gnu --class os {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt5)'
	search --no-floppy --fs-uuid --set 34e053f0-2e43-4f01-999b-8070b5057986
	echo	'Loading Linux 2.6.32-5-686 ...'
	linux	/boot/vmlinuz-2.6.32-5-686 root=UUID=34e053f0-2e43-4f01-999b-8070b5057986 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-5-686
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-19-generic (on /dev/sda4)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt4)'
	search --no-floppy --fs-uuid --set 70f17fcf-2b30-4a4f-bcd5-a80834943351
	linux /boot/vmlinuz-2.6.35-19-generic root=UUID=70f17fcf-2b30-4a4f-bcd5-a80834943351 ro quiet splash
	initrd /boot/initrd.img-2.6.35-19-generic
}
menuentry "Ubuntu, with Linux 2.6.35-19-generic (recovery mode) (on /dev/sda4)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt4)'
	search --no-floppy --fs-uuid --set 70f17fcf-2b30-4a4f-bcd5-a80834943351
	linux /boot/vmlinuz-2.6.35-19-generic root=UUID=70f17fcf-2b30-4a4f-bcd5-a80834943351 ro single
	initrd /boot/initrd.img-2.6.35-19-generic
}
menuentry "Chakra GNU/Linux (on /dev/sda6)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt6)'
	search --no-floppy --fs-uuid --set fc8f6872-99a2-4236-82bb-2aaf3d4abb22
	linux /boot/vmlinuz26 resume=/dev/disk/by-uuid/0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 root=/dev/disk/by-uuid/fc8f6872-99a2-4236-82bb-2aaf3d4abb22 ro
	initrd /boot/kernel26.img
}
menuentry "Chakra GNU/Linux Fallback (on /dev/sda6)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt6)'
	search --no-floppy --fs-uuid --set fc8f6872-99a2-4236-82bb-2aaf3d4abb22
	linux /boot/vmlinuz26 resume=/dev/disk/by-uuid/0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 root=/dev/disk/by-uuid/fc8f6872-99a2-4236-82bb-2aaf3d4abb22 ro
	initrd /boot/kernel26-fallback.img
}
menuentry "Fedora (2.6.33.3-85.fc13.i686) (on /dev/sda7)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt7)'
	search --no-floppy --fs-uuid --set 063c93e1-3a91-40a0-81df-c5a96d799830
	linux /boot/vmlinuz-2.6.33.3-85.fc13.i686 ro root=UUID=063c93e1-3a91-40a0-81df-c5a96d799830 rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
	initrd /boot/initramfs-2.6.33.3-85.fc13.i686.img
}
menuentry "linux (on /dev/sda8)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt8)'
	search --no-floppy --fs-uuid --set c36d8965-5da4-4de6-9aaa-523a7c6b3f53
	linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=c36d8965-5da4-4de6-9aaa-523a7c6b3f53 resume=UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 splash=silent vga=788
	initrd (hd0,7)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda8)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt8)'
	search --no-floppy --fs-uuid --set c36d8965-5da4-4de6-9aaa-523a7c6b3f53
	linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=c36d8965-5da4-4de6-9aaa-523a7c6b3f53 resume=UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5
	initrd (hd0,7)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda8)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt8)'
	search --no-floppy --fs-uuid --set c36d8965-5da4-4de6-9aaa-523a7c6b3f53
	linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=c36d8965-5da4-4de6-9aaa-523a7c6b3f53 failsafe
	initrd (hd0,7)/boot/initrd.img
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=39dce7bc-28c6-4d48-a3e1-b2d48712856e /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f5355ad1-6de9-497b-a8d4-e2abe7336d4d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda5	/	ext4	rw,errors=remount-ro	0	0
/dev/sda2	/mnt/Data	ext4 	defaults,exec	0	0

=================== sda5: Location of files loaded by Grub: ===================


 354.0GB: boot/grub/core.img
 373.4GB: boot/grub/grub.cfg
 360.7GB: boot/initrd.img-2.6.32-5-686
 354.0GB: boot/vmlinuz-2.6.32-5-686
 360.7GB: initrd.img
 354.0GB: vmlinuz

=========================== sda6/boot/grub/menu.lst: ===========================

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
#
#-*

# (0) Chakra GNU/Linux

# (1) Windows
 
hiddenmenu
default 0
timeout 1
 
# (0) Chakra GNU/Linux
title Chakra GNU/Linux
root (hd0,5)
kernel /boot/vmlinuz26 resume=/dev/disk/by-uuid/0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 root=/dev/disk/by-uuid/fc8f6872-99a2-4236-82bb-2aaf3d4abb22 ro
initrd /boot/kernel26.img
 
# (1) Chakra GNU/Linux Fallback
title Chakra GNU/Linux Fallback
root (hd0,5)
kernel /boot/vmlinuz26 resume=/dev/disk/by-uuid/0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 root=/dev/disk/by-uuid/fc8f6872-99a2-4236-82bb-2aaf3d4abb22 ro
initrd /boot/kernel26-fallback.img

=============================== sda6/etc/fstab: ===============================

# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
devpts                 /dev/pts      devpts    defaults            0      0
shm                    /dev/shm      tmpfs     nodev,nosuid        0      0


UUID=fc8f6872-99a2-4236-82bb-2aaf3d4abb22 / ext4 defaults 0 0
UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 swap swap defaults 0 0
/dev/sda2 /mnt/Data ext4 defaults 0 0

=================== sda6: Location of files loaded by Grub: ===================


 391.1GB: boot/grub/menu.lst
 391.1GB: boot/grub/stage2
 391.2GB: boot/kernel26-fallback.img
 391.1GB: boot/kernel26.img
 391.1GB: boot/vmlinuz26

========================== sda7/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,6)
#          kernel /boot/vmlinuz-version ro root=/dev/sda7 rdblacklist=nouveau
#          initrd /boot/initrd-[generic-]version.img
#boot=/dev/sda7
default=0
timeout=0
splashimage=(hd0,6)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.34.6-54.fc13.i686)
	root (hd0,6)
	kernel /boot/vmlinuz-2.6.34.6-54.fc13.i686 ro root=UUID=d9673816-d0ac-49f7-ad55-4f2920bdd32e rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet nouveau.modeset=0 rdblacklist=nouveau rdblacklist=nouveau
	initrd /boot/initramfs-2.6.34.6-54.fc13.i686.img
title Fedora (2.6.33.3-85.fc13.i686)
	root (hd0,6)
	kernel /boot/vmlinuz-2.6.33.3-85.fc13.i686 ro root=UUID=d9673816-d0ac-49f7-ad55-4f2920bdd32e rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet rdblacklist=nouveau
	initrd /boot/initramfs-2.6.33.3-85.fc13.i686.img

=============================== sda7/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Sat Sep 11 20:09:35 2010
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=d9673816-d0ac-49f7-ad55-4f2920bdd32e /                       ext4    defaults        1 1
UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/sda2 	/mnt/Data	ext4	defaults	0	0

=================== sda7: Location of files loaded by Grub: ===================


 404.3GB: boot/grub/grub.conf
 404.3GB: boot/grub/menu.lst
 406.2GB: boot/grub/stage2
 406.8GB: boot/initramfs-2.6.33.3-85.fc13.i686-nouveau.img
 407.6GB: boot/initramfs-2.6.33.3-85.fc13.i686.img
 406.6GB: boot/initramfs-2.6.34.6-54.fc13.i686.img
 405.8GB: boot/vmlinuz-2.6.33.3-85.fc13.i686
 406.9GB: boot/vmlinuz-2.6.34.6-54.fc13.i686

=========================== sda8/boot/grub/menu.lst: ===========================

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,7)/boot/gfxmenu
default 0

title linux
kernel (hd0,7)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=c36d8965-5da4-4de6-9aaa-523a7c6b3f53  resume=UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 splash=silent vga=788
initrd (hd0,7)/boot/initrd.img

title linux-nonfb
kernel (hd0,7)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=c36d8965-5da4-4de6-9aaa-523a7c6b3f53  resume=UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5
initrd (hd0,7)/boot/initrd.img

title failsafe
kernel (hd0,7)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=c36d8965-5da4-4de6-9aaa-523a7c6b3f53  failsafe
initrd (hd0,7)/boot/initrd.img

title [H[2J
root (hd0,5)
configfile /boot/grub/menu.lst

title Fedora (Goddard)
root (hd0,6)
configfile /boot/grub/menu.lst

=============================== sda8/etc/fstab: ===============================

# Entry for /dev/sda8 :
UUID=c36d8965-5da4-4de6-9aaa-523a7c6b3f53 / ext4 defaults 1 1
none /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 swap swap defaults 0 0

=================== sda8: Location of files loaded by Grub: ===================


 432.7GB: boot/grub/menu.lst
 432.7GB: boot/grub/stage2
 430.8GB: boot/initrd-2.6.33.5-desktop586-2mnb.img
 430.8GB: boot/initrd-desktop586.img
 430.8GB: boot/initrd.img
 432.7GB: boot/vmlinuz
 432.7GB: boot/vmlinuz-2.6.33.5-desktop586-2mnb
 432.7GB: boot/vmlinuz-desktop586

=========================== sda9/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Sun Sep 12 13:26:53 CDT 2010
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,8)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.3
    root (hd0,8)
    kernel /boot/vmlinuz-2.6.34-12-default root=/dev/disk/by-id/ata-WDC_WD6400BEVT-00A0RT0_WD-WX40A99L8069-part9 resume=/dev/disk/by-id/ata-WDC_WD6400BEVT-00A0RT0_WD-WX40A99L8069-part1 splash=silent quiet showopts vga=0x314
    initrd /boot/initrd-2.6.34-12-default

###Don't change this comment - YaST2 identifier: Original name: Linux other 1 (/dev/sda5)###
title Linux other 1 (/dev/sda5)
    rootnoverify (hd0,4)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: Linux other 2 (/dev/sda6)###
title Linux other 2 (/dev/sda6)
    root (hd0,5)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name:  Fedora (2.6.34.6-54.fc13.i686) (/dev/sda7)###
title  Fedora (2.6.34.6-54.fc13.i686) (/dev/sda7)
    rootnoverify (hd0,6)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name:  linux (/dev/sda8)###
title  linux (/dev/sda8)
    rootnoverify (hd0,7)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.3
    root (hd0,8)
    kernel /boot/vmlinuz-2.6.34-12-default root=/dev/disk/by-id/ata-WDC_WD6400BEVT-00A0RT0_WD-WX40A99L8069-part9 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 nomodeset x11failsafe vga=0x314
    initrd /boot/initrd-2.6.34-12-default

=============================== sda9/etc/fstab: ===============================

/dev/disk/by-id/ata-WDC_WD6400BEVT-00A0RT0_WD-WX40A99L8069-part9 /                    ext4       acl,user_xattr        1 1
/dev/disk/by-id/ata-WDC_WD6400BEVT-00A0RT0_WD-WX40A99L8069-part1 swap                 swap       defaults              0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda9: Location of files loaded by Grub: ===================


 458.9GB: boot/grub/menu.lst
 458.9GB: boot/grub/stage2
 459.1GB: boot/initrd
 459.1GB: boot/initrd-2.6.34-12-default
 458.9GB: boot/vmlinuz
 458.9GB: boot/vmlinuz-2.6.34-12-default

========================== sda10/boot/grub/menu.lst: ==========================

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,9)/boot/gfxmenu
default 0

title linux
kernel (hd0,9)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=658db7c4-b01a-40f6-962a-c6d30cad8417  vmalloc=256M resume=UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 splash=silent vga=788
initrd (hd0,9)/boot/initrd.img

title linux-nonfb
kernel (hd0,9)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=658db7c4-b01a-40f6-962a-c6d30cad8417  vmalloc=256M resume=UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5
initrd (hd0,9)/boot/initrd.img

title failsafe
kernel (hd0,9)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=658db7c4-b01a-40f6-962a-c6d30cad8417  failsafe vmalloc=256M
initrd (hd0,9)/boot/initrd.img

title [H[2J
root (hd0,5)
configfile /boot/grub/menu.lst

title Fedora (Goddard)
root (hd0,6)
configfile /boot/grub/menu.lst

title Mandriva Linux (Official)
root (hd0,7)
configfile /boot/grub/menu.lst

title openSUSE 11.3 (i586)
VERSION = 11.3
root (hd0,8)
configfile /boot/grub/menu.lst

=============================== sda10/etc/fstab: ===============================

# Entry for /dev/sda10 :
UUID=658db7c4-b01a-40f6-962a-c6d30cad8417 / ext4 defaults 1 1
none /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 swap swap defaults 0 0
none /dev/pts devpts defaults 0 0

=================== sda10: Location of files loaded by Grub: ===================


 504.4GB: boot/grub/menu.lst
 504.4GB: boot/grub/stage2
 483.1GB: boot/initrd-2.6.33.5-pclos1.bfs.img
 483.1GB: boot/initrd.img
 504.4GB: boot/vmlinuz
 504.4GB: boot/vmlinuz-2.6.33.5-pclos1.bfs
```

As you can see I have a few different distros installed... PCLinuxOS is on /dev/sda10 and Mandriva is on /dev/sda8 (The rest all boot fine from grub2).

Do you see what you are looking for there?

~Jeff

---

### Post by oldfred on 2010-09-13
All the entries in grub2's grub.cfg are the problem.

set root='(hd0,8)'
....
initrd (hd0,7)/boot/initrd.img

Note that the set root is partition 8 per grub2 numbering but hte initrd copied the line from old grub that had (hd0,7) you do not even need that after the set root or you can change it to hd0,8.

You have to copy all the entries into 40_custom and edit there. Once they work then you can turn off osprober so you do not have duplicate entries.

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
Copy the  entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

---

### Post by beastrace91 on 2010-09-13
Are you saying the reason it is not booting into either of these operating systems is because I have too many menu entries? The response wasn't terribly clear to me, sorry.

~Jeff

---

### Post by oldfred on 2010-09-13
No, I have several Ubuntu installs and before grub2 I used chainbooting with old grub as it helped simplify menus.

It is the conflict in partition numbering between grub legacy (partitions start at 0) and grub2 (partitions start at 1). When the Osprober copies a grub legacy entry it has the wrong partition number. Example below with old grub uses hd0,7 but grub2 is hd0,8. Since a set root command is used with grub2 the hd0,7 on the initrd line is not even needed. (And I do not think it was even with old grub).
```

Current entry error in red
menuentry "linux (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set c36d8965-5da4-4de6-9aaa-523a7c6b3f53
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=c36d8965-5da4-4de6-9aaa-523a7c6b3f53 resume=UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 splash=silent vga=788
    initrd [COLOR=Red](hd0,7)[/COLOR]/boot/initrd.img
}

Corrected entry - hd0,7 removed.
menuentry "linux (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set c36d8965-5da4-4de6-9aaa-523a7c6b3f53
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=c36d8965-5da4-4de6-9aaa-523a7c6b3f53 resume=UUID=0fdf0b6e-2600-493b-b17a-bd653ed1ffe5 splash=silent vga=788
    initrd /boot/initrd.img
}

```

I just noticed you have gpt. I tried it on a small drive just to test and it worked but then grub would not see the msdos/MBR drives. I had to add parameters to make it work. I think since you only have gpt you should be ok, not sure if old grub has any issues with gpt or not.

---

### Post by beastrace91 on 2010-09-13
Ahh alrighty, I will give that a try when I get home then. I see you say Chicago burbs, where abouts? Alsip is on the south side :D

~Jeff

---

### Post by oldfred on 2010-09-13
Downers Grove, just up 294 and west on Ogden a ways from Alsip. I worked in Blue Island for a couple of years, but that was a while ago.

---

### Post by beastrace91 on 2010-09-14
Worked like a charm.

Thanks!
~Jeff

---

### Post by oldfred on 2010-09-14
Glad you got it working. :)

---

