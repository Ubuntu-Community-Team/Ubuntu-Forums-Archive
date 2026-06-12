---
title: "Manual boot to hard drive required every time, unable to make it automatic."
date: 2010-11-02
forum: General Help
---

### Post by Th3Professor on 2010-11-02
I have to press F8 to load the Boot Menu every time I boot or restart the computer, and I have to manually tell it to boot.

I am running raid5 (softraid).

I don't know if that is part of the problem.

How do I get it to boot without having to manually select a hard drive for it to boot to?

---

### Post by Th3Professor on 2010-11-03
Bump. This hasn't always been a problem. I made no changes to the boot order or how it is supposed to auto-boot to the system. Now days, if I try to boot without pressing the F8/boot-menu key, it locks up when attempting to load Linux. I think it actually is stopping when the kernel attempts to load.

---

### Post by Hippytaff on 2010-11-03
Do you have to change the boot order everytime? even HDD is not at the top of the boot list, once the bios has checked the top entries, and found nothing, it would boot from HDD.

---

### Post by oldfred on 2010-11-03
I do not know RAID and script does not parse RAID quite as well but usually sees most of the important info:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Th3Professor on 2010-11-03
> **Hippytaff said:**
> Do you have to change the boot order everytime? even HDD is not at the top of the boot list, once the bios has checked the top entries, and found nothing, it would boot from HDD.
I don't have to mess with the BIOS if that's what you mean. The BIOS' actual boot order is fine. I have gone in to double-check and it is still set to correctly boot.

The motherboard knows how to boot, and it goes to GRUB, and after I select Linux to boot, while it tries to boot it gets stuck. I haven't been able to save the actual text output while it tries to load Linux, I don't know if there's a way to copy/paste that info.

It's weird because while the mobo can boot, and grub and load, the kernel no longer seems to auto-recognize where to load from or how to load. And yet, if I use the bios boot menu and select one of the hard drives (of the raid set-up) to boot from, suddenly the kernel knows how to load.

> **oldfred said:**
> I do not know RAID and script does not parse RAID quite as well but usually sees most of the important info:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.
I'll give that boot info script a try, thanks. I'll post an update with that info when I get a chance.

In the mean time, is there any logical reason why bios and grub would work, yet the kernel wouldn't load unless I manually tell the bios to boot from a hard drive?

I'm confused as to why it's behaving like that.

---

### Post by Th3Professor on 2010-11-04
Okay here is the output from that boot info script. That's a nifty script.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda8: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

vg0-vault: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

vg0-zone: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

vg0-nomad: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

md0: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     1,959,929     1,959,867  83 Linux
/dev/sda2           1,959,930   392,580,404   390,620,475   7 HPFS/NTFS
/dev/sda3         392,580,405   421,882,964    29,302,560  be Solaris boot
/dev/sda4         421,882,965   976,768,064   554,885,100   5 Extended
/dev/sda5         421,883,028   460,953,044    39,070,017  83 Linux
/dev/sda6         460,953,108   919,930,094   458,976,987  83 Linux
/dev/sda7         919,930,158   923,833,889     3,903,732  82 Linux swap / Solaris
/dev/sda8         923,833,953   927,737,684     3,903,732  82 Linux swap / Solaris
/dev/sda9         927,737,748   931,641,479     3,903,732  bf Solaris
/dev/sda10        931,641,543   976,768,064    45,126,522  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002  fd Linux raid autodetect


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   976,768,064   976,768,002  fd Linux raid autodetect


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63 1,953,520,064 1,953,520,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/cryptswap1 <<removed UUID from results.txt file>>   swap                                     
/dev/mapper/cryptswap2 <<removed>>   swap                                     
/dev/mapper/vg0-nomad <<removed>>   ext3                                     
/dev/mapper/vg0-vault <<removed>>   xfs                                      
/dev/mapper/vg0-zone <<removed>>   ext3                                     
/dev/md0         <<removed>> LVM2_member                               
/dev/sda10       <<removed>>   ext3                                     
/dev/sda1        <<removed>>   ext3                                     
/dev/sda2        <<removed>>                       ntfs                                     
/dev/sda3        <<removed>>   ext3                                     
/dev/sda5        <<removed>>   ext3                                     
/dev/sda6        <<removed>>   ext3                                     
/dev/sda9        <<removed>>   ext3                                     
/dev/sdb1        <<removed>>   linux_raid_member                               
/dev/sdc1        <<removed>>   linux_raid_member                               
/dev/sdd1        <<removed>>   linux_raid_member                               
/dev/sde1        <<removed>>                              vfat       My Book                       

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
cryptswap1
cryptswap1_unformatted
cryptswap2
cryptswap2_unformatted
vg0-nomad
vg0-vault
vg0-zone

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro)
/dev/sda1        /boot                    ext3       (rw)
/dev/mapper/vg0-vault /studio/vault            xfs        (rw)
/dev/sda2        /windows                 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/mapper/vg0-zone /zone                    ext3       (rw)
/dev/sda6        /studio/workspace        ext3       (rw)
/dev/mapper/vg0-nomad /nomad                   ext3       (rw)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=user)
/dev/sde1        /media/My Book           vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/fuse        /home/user/.gvfs         fuse       (rw,nosuid,nodev,user=user)


============================= sda1/grub/grub.cfg: =============================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set <<removed>>
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
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed from results.txt file>>
	linux	/vmlinuz-2.6.31-22-generic root=UUID=<<removed>> ro   quiet splash
	initrd	/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux	/vmlinuz-2.6.31-22-generic root=UUID=<<removed>> ro single 
	initrd	/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux	/vmlinuz-2.6.31-21-generic root=UUID=<<removed>> ro   quiet splash
	initrd	/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux	/vmlinuz-2.6.31-21-generic root=UUID=<<removed>> ro single 
	initrd	/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux	/vmlinuz-2.6.31-20-generic root=UUID=<<removed>> ro   quiet splash
	initrd	/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux	/vmlinuz-2.6.31-20-generic root=UUID=<<removed>> ro single 
	initrd	/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux	/vmlinuz-2.6.31-19-generic root=UUID=<<removed>> ro   quiet splash
	initrd	/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux	/vmlinuz-2.6.31-19-generic root=UUID=<<removed>> ro single 
	initrd	/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux	/vmlinuz-2.6.31-17-generic root=UUID=<<removed>> ro   quiet splash
	initrd	/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux	/vmlinuz-2.6.31-17-generic root=UUID=<<removed>> ro single 
	initrd	/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-9-rt" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux	/vmlinuz-2.6.31-9-rt root=UUID=<<removed>> ro   quiet splash
	initrd	/initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu, Linux 2.6.31-9-rt (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux	/vmlinuz-2.6.31-9-rt root=UUID=<<removed>> ro single 
	initrd	/initrd.img-2.6.31-9-rt
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-22-generic (on /dev/sda10)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux /vmlinuz-2.6.31-22-generic root=UUID=<<removed>> ro quiet splash
	initrd /initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode) (on /dev/sda10)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux /vmlinuz-2.6.31-22-generic root=UUID=<<removed>> ro single
	initrd /initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (on /dev/sda10)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux /vmlinuz-2.6.31-21-generic root=UUID=<<removed>> ro quiet splash
	initrd /initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode) (on /dev/sda10)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux /vmlinuz-2.6.31-21-generic root=UUID=<<removed>> ro single
	initrd /initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (on /dev/sda10)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux /vmlinuz-2.6.31-20-generic root=UUID=<<removed>> ro quiet splash
	initrd /initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode) (on /dev/sda10)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux /vmlinuz-2.6.31-20-generic root=UUID=<<removed>> ro single
	initrd /initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (on /dev/sda10)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux /vmlinuz-2.6.31-19-generic root=UUID=<<removed>> ro quiet splash
	initrd /initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode) (on /dev/sda10)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux /vmlinuz-2.6.31-19-generic root=UUID=<<removed>> ro single
	initrd /initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (on /dev/sda10)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux /vmlinuz-2.6.31-17-generic root=UUID=<<removed>> ro quiet splash
	initrd /initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda10)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux /vmlinuz-2.6.31-17-generic root=UUID=<<removed>> ro single
	initrd /initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-9-rt (on /dev/sda10)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux /vmlinuz-2.6.31-9-rt root=UUID=<<removed>> ro quiet splash
	initrd /initrd.img-2.6.31-9-rt
}
menuentry "Ubuntu, Linux 2.6.31-9-rt (recovery mode) (on /dev/sda10)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set <<removed>>
	linux /vmlinuz-2.6.31-9-rt root=UUID=<<removed>> ro single
	initrd /initrd.img-2.6.31-9-rt
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set <<removed>>
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    .6GB: grub/core.img
    .7GB: grub/grub.cfg
    .0GB: initrd.img-2.6.31-17-generic
    .0GB: initrd.img-2.6.31-19-generic
    .0GB: initrd.img-2.6.31-20-generic
    .0GB: initrd.img-2.6.31-21-generic
    .1GB: initrd.img-2.6.31-22-generic
    .0GB: initrd.img-2.6.31-9-rt
    .0GB: vmlinuz-2.6.31-17-generic
    .0GB: vmlinuz-2.6.31-19-generic
    .0GB: vmlinuz-2.6.31-20-generic
    .1GB: vmlinuz-2.6.31-21-generic
    .1GB: vmlinuz-2.6.31-22-generic
    .0GB: vmlinuz-2.6.31-9-rt

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=<<removed>> /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=<<removed>> /boot           ext3    defaults        0       2
/dev/mapper/vg0-nomad /nomad          ext3    defaults        0       2
/dev/mapper/vg0-vault /studio/vault   xfs     defaults        0       2
# /studio/workspace was on /dev/sda6 during installation
UUID=<<removed>> /studio/workspace ext3    defaults        0       2
# /windows was on /dev/sda2 during installation
UUID=<<removed>> /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
/dev/mapper/vg0-zone /zone           ext3    defaults        0       2
# swap was on /dev/sda7 during installation
#UUID=<<removed>> none            swap    sw              0       0
# swap was on /dev/sda8 during installation
#UUID=<<removed>> none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/mapper/cryptswap2 none swap sw 0 0

=================== sda5: Location of files loaded by Grub: ===================


 216.1GB: initrd.img
 216.0GB: initrd.img.old
 216.1GB: vmlinuz
 216.1GB: vmlinuz.old

=============================== sda10/etc/fstab: ===============================

proc            /proc           proc    defaults        0       0
/dev/sda1	/boot           ext3    defaults        0       2
/dev/ROOT	/               ext3    errors=remount-ro 0       1
/dev/mapper/vg0-nomad /nomad          ext3    defaults        0       2
/dev/mapper/vg0-vault /studio/vault   xfs     defaults        0       2
/dev/mapper/vg0-zone /zone           ext3    defaults        0       2
/dev/sda6	/studio/workspace ext3    defaults        0       2
/dev/sda7   none         swap    sw                   0 0
/dev/sda8   none         swap    sw                   0 0
/windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/mapper/cryptswap2 none swap sw 0 0


```

---

### Post by oldfred on 2010-11-05
I do not know enough about RAID to really help. Is it Solaris that you also have? I have heard it does not play nice with other systems.

---

### Post by Th3Professor on 2010-11-05
I set up part of the hdd space for solaris but I haven't gotten around to installing it, so there's nothing for it to mess with the boot process. :-?

---

### Post by Th3Professor on 2010-11-09
Okay this is very weird. I tried rebooting the other day and didn't press F8/manual-boot and, suddenly, it just out of the blue booted okay. However, I know it's possible that it will end up requiring F8 on boot-up/reboot in the future, at some point. It's like an intermittent thing, sometimes needing it, sometimes not. Any ideas as to why that might be the case?

---

