---
title: "grub2 sees /dev/sdc1 as (hd0,1) when restarted"
date: 2011-03-16
forum: General Help
---

### Post by bababooey on 2011-03-16
Im running grub2 and have grub2 installed into /dev/sdc1. When grub boots up, it tells me I need to set a root device or load a kernel. I check (hd2,1) and that is not what grub2 see as what suppose to be /dev/sdc1. I have converted my /etc/fstab to UUID but that did not fix it.  

Each time  I reboot, I have to manually edit the lines like 
linux (hd0,1)/vmlinuz-2.6.35-27-generic
initrd (hd0,1)initrd.img-2.6.35-27-generic

to get my system to boot /dev/sdc2 since I have a dedicated boot partition as I have a encrypted swap / and home partitions.

When I run grub-mkconfig I can see grub add set root to hd2,msdos1

menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 43372c0e-496d-4db1-86ee-a17b906b305d
    linux    /vmlinuz-2.6.35-27-generic root=/dev/mapper/sdc5_crypt ro   quiet nosplash
    initrd    /initrd.img-2.6.35-27-generic
}

Wondering anyone else encountered this problem

---

### Post by Krytarik on 2011-03-16
To get more info about your boot environment, please run those script, follow the instructions on the  website:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then post its result here, in code-tags please (the #-button in the editor).

---

### Post by bababooey on 2011-03-16
Hi thanks for helping me out. I ran the script, and just to add to describe my system setup, I installed xubuntu-desktop onto a different drive which is /dev/sda last night so I dont have to keep running a livecd in case I need to chroot into /dev/sdc - the drive im having trouble with grub2. And to note, even after installing xubuntu onto /dev/sda, my manual grub boot today failed to /dev/sdc failed as usual and settting root to (hd0,1) still shows /dev/sdc not /dev/sda which confuses me. 


edit the results to remove default and stuff not useful to reduce the size of it

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for (,msdos1)/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'

sdc1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'
mount: unknown filesystem type ''

sdc3: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'

sdc4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'

sdc6: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       499,711       497,664  83 Linux
/dev/sda2             499,712    12,218,367    11,718,656  82 Linux swap / Solaris
/dev/sda3          12,220,414   160,835,583   148,615,170   5 Extended
/dev/sda5          12,220,416   160,835,583   148,615,168  83 Linux


Drive: sdb ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   145,211,534   145,211,472  83 Linux


Drive: sdc ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63       963,899       963,837  83 Linux
/dev/sdc2             976,896    16,601,087    15,624,192  82 Linux swap / Solaris
/dev/sdc3         294,069,825   781,417,664   487,347,840  83 Linux
/dev/sdc4          16,603,134   294,068,223   277,465,090   5 Extended
/dev/sdc5          16,603,136   129,243,135   112,640,000  83 Linux
/dev/sdc6         129,245,184   294,068,223   164,823,040  83 Linux




blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/sdb1_crypt 296a4cb6-ef3b-49f0-a614-92a70f8cebe2   ext4                                     
/dev/mapper/sdc2_crypt a729dd40-f906-4758-acc1-118e2148b07f   swap                                     
/dev/mapper/sdc3_crypt d5a7eb8d-048b-470e-964e-65c952c8c0ea   ext3                                     
/dev/mapper/sdc5_crypt 7697426a-1b37-4d20-a24d-2cfc6742701c   ext4                                     
/dev/mapper/sdc6_crypt 05d696e9-269e-428a-97e1-7d89594d54df   ext4                                     
/dev/sda1        b1b0716c-dacd-4840-af32-db1c75f355e9   ext3                                     
/dev/sda2        c68220ac-a33b-44e0-9cae-abe341ca498c   swap                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        691bcec8-94bb-4abe-8d2e-675d51dfe912   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        a2e1aaa2-e8cd-4f15-bd05-7117b6987909   crypto_LUKS                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        43372c0e-496d-4db1-86ee-a17b906b305d   ext2                                     
/dev/sdc3        1112949e-67ec-4b84-b39f-a6067c5189ff   crypto_LUKS                               
/dev/sdc4: PTTYPE="dos" 
/dev/sdc5        659b8efd-e0a2-4bac-a3d6-30b901cf6489   crypto_LUKS                               
/dev/sdc6        0e7f321d-4c4c-4d4f-95c5-9f7115e4870f   crypto_LUKS                               
/dev/sdc: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
sdb1_crypt
sdc2_crypt
sdc3_crypt
sdc5_crypt
sdc6_crypt

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/sdc5_crypt /                        ext4       (rw,commit=0)
/dev/sdc1        /boot                    ext2       (rw)
/dev/mapper/sdc6_crypt /home                    ext4       (rw,commit=0)
/dev/mapper/sdc3_crypt /240                     ext3       (rw,commit=0)
/dev/mapper/sdb1_crypt /media/raptor            ext4       (rw)

============================= sda1/grub/grub.cfg: =============================

### BEGIN /etc/grub.d/00_header ###
# deleted the default crap load_env, set saved_entry load vga etc

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 691bcec8-94bb-4abe-8d2e-675d51dfe912
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b1b0716c-dacd-4840-af32-db1c75f355e9
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b1b0716c-dacd-4840-af32-db1c75f355e9
	linux	/vmlinuz-2.6.35-22-generic root=UUID=691bcec8-94bb-4abe-8d2e-675d51dfe912 ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b1b0716c-dacd-4840-af32-db1c75f355e9
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=691bcec8-94bb-4abe-8d2e-675d51dfe912 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b1b0716c-dacd-4840-af32-db1c75f355e9
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b1b0716c-dacd-4840-af32-db1c75f355e9
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: vmlinuz-2.6.35-22-generic

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=691bcec8-94bb-4abe-8d2e-675d51dfe912 /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext3    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=c68220ac-a33b-44e0-9cae-abe341ca498c none            swap    sw              0       0

================================ sdc1/grub.cfg: ================================


### BEGIN /etc/grub.d/00_header ###
# deleted the default crap load_env, set saved_entry load vga etc

insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 43372c0e-496d-4db1-86ee-a17b906b305d
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 43372c0e-496d-4db1-86ee-a17b906b305d
	linux	/vmlinuz-2.6.35-27-generic root=/dev/mapper/sdc5_crypt ro   quiet nosplash
	initrd	/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 43372c0e-496d-4db1-86ee-a17b906b305d
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/vmlinuz-2.6.35-27-generic root=/dev/mapper/sdc5_crypt ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 43372c0e-496d-4db1-86ee-a17b906b305d
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos1)'
	search --no-floppy --fs-uuid --set 43372c0e-496d-4db1-86ee-a17b906b305d
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b1b0716c-dacd-4840-af32-db1c75f355e9
	linux /vmlinuz-2.6.35-22-generic root=UUID=691bcec8-94bb-4abe-8d2e-675d51dfe912 ro quiet splash
	initrd /initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set b1b0716c-dacd-4840-af32-db1c75f355e9
	linux /vmlinuz-2.6.35-22-generic root=UUID=691bcec8-94bb-4abe-8d2e-675d51dfe912 ro single
	initrd /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###
 

============================= sdc1/grub/grub.cfg: =============================


### BEGIN /etc/grub.d/00_header ###
# deleted the default crap load_env, set saved_entry load vga etc

insmod part_msdos
insmod ext2
set root=''
search --no-floppy --fs-uuid --set b2cb2a9c-b2d1-43dc-94f7-54cefd5ba5ad
set locale_dir=($root)
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail

	linux	/boot/vmlinuz-2.6.35-27-generic root=/dev/mapper/sdc5_crypt ro   quiet nosplash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail

	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=/dev/mapper/sdc5_crypt ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {

	linux16	
}
menuentry "Memory test (memtest86+, serial console 115200)" {

	linux16	 console=ttyS0,115200n8
}


=================== sdc1: Location of files loaded by Grub: ===================


    .2GB: boot/grub/core.img
    .1GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-27-generic
    .0GB: vmlinuz-2.6.35-27-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

Unknown BootLoader  on sdb1

Unknown BootLoader  on sdc2


Unknown BootLoader  on sdc3



```

---

### Post by Krytarik on 2011-03-16
Could you please edit your post in that way, that you re-paste the result from the text file, mark it and then press the #-button in the editor (advanced mode), it's really easier to read then, thanks.

---

### Post by bababooey on 2011-03-17
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for (,msdos1)/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'

sdc1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'
mount: unknown filesystem type ''

sdc3: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'
mount: unknown filesystem type ''
mount: unknown filesystem type 'crypto_LUKS'

sdc4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'
mount: unknown filesystem type ''
mount: unknown filesystem type 'crypto_LUKS'
mount: unknown filesystem type 'crypto_LUKS'

sdc6: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'
mount: unknown filesystem type ''
mount: unknown filesystem type 'crypto_LUKS'
mount: unknown filesystem type 'crypto_LUKS'
mount: unknown filesystem type 'crypto_LUKS'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       499,711       497,664  83 Linux
/dev/sda2             499,712    12,218,367    11,718,656  82 Linux swap / Solaris
/dev/sda3          12,220,414   160,835,583   148,615,170   5 Extended
/dev/sda5          12,220,416   160,835,583   148,615,168  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   145,211,534   145,211,472  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63       963,899       963,837  83 Linux
/dev/sdc2             976,896    16,601,087    15,624,192  82 Linux swap / Solaris
/dev/sdc3         294,069,825   781,417,664   487,347,840  83 Linux
/dev/sdc4          16,603,134   294,068,223   277,465,090   5 Extended
/dev/sdc5          16,603,136   129,243,135   112,640,000  83 Linux
/dev/sdc6         129,245,184   294,068,223   164,823,040  83 Linux




blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/sdb1_crypt 296a4cb6-ef3b-49f0-a614-92a70f8cebe2   ext4                                     
/dev/mapper/sdc2_crypt a729dd40-f906-4758-acc1-118e2148b07f   swap                                     
/dev/mapper/sdc3_crypt d5a7eb8d-048b-470e-964e-65c952c8c0ea   ext3                                     
/dev/mapper/sdc5_crypt 7697426a-1b37-4d20-a24d-2cfc6742701c   ext4                                     
/dev/mapper/sdc6_crypt 05d696e9-269e-428a-97e1-7d89594d54df   ext4                                     
/dev/sda1        b1b0716c-dacd-4840-af32-db1c75f355e9   ext3                                     
/dev/sda2        c68220ac-a33b-44e0-9cae-abe341ca498c   swap                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        691bcec8-94bb-4abe-8d2e-675d51dfe912   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        a2e1aaa2-e8cd-4f15-bd05-7117b6987909   crypto_LUKS                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        43372c0e-496d-4db1-86ee-a17b906b305d   ext2                                     
/dev/sdc3        1112949e-67ec-4b84-b39f-a6067c5189ff   crypto_LUKS                               
/dev/sdc4: PTTYPE="dos" 
/dev/sdc5        659b8efd-e0a2-4bac-a3d6-30b901cf6489   crypto_LUKS                               
/dev/sdc6        0e7f321d-4c4c-4d4f-95c5-9f7115e4870f   crypto_LUKS                               
/dev/sdc: PTTYPE="dos" 

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
sdb1_crypt
sdc2_crypt
sdc3_crypt
sdc5_crypt
sdc6_crypt

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/sdc5_crypt /                        ext4       (rw,commit=0)
/dev/sdc1        /boot                    ext2       (rw)
/dev/mapper/sdc6_crypt /home                    ext4       (rw,commit=0)
/dev/mapper/sdc3_crypt /240                     ext3       (rw,commit=0)
/dev/mapper/sdb1_crypt /media/raptor            ext4       (rw)

============================= sda1/grub/grub.cfg: =============================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 691bcec8-94bb-4abe-8d2e-675d51dfe912
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b1b0716c-dacd-4840-af32-db1c75f355e9
set locale_dir=($root)/grub/locale
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
    search --no-floppy --fs-uuid --set b1b0716c-dacd-4840-af32-db1c75f355e9
    linux    /vmlinuz-2.6.35-22-generic root=UUID=691bcec8-94bb-4abe-8d2e-675d51dfe912 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1b0716c-dacd-4840-af32-db1c75f355e9
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=691bcec8-94bb-4abe-8d2e-675d51dfe912 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1b0716c-dacd-4840-af32-db1c75f355e9
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1b0716c-dacd-4840-af32-db1c75f355e9
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: vmlinuz-2.6.35-22-generic

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=691bcec8-94bb-4abe-8d2e-675d51dfe912 /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext3    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=c68220ac-a33b-44e0-9cae-abe341ca498c none            swap    sw              0       0

================================ sdc1/grub.cfg: ================================

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
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set 43372c0e-496d-4db1-86ee-a17b906b305d
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 43372c0e-496d-4db1-86ee-a17b906b305d
    linux    /vmlinuz-2.6.35-27-generic root=/dev/mapper/sdc5_crypt ro   quiet nosplash
    initrd    /initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 43372c0e-496d-4db1-86ee-a17b906b305d
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /vmlinuz-2.6.35-27-generic root=/dev/mapper/sdc5_crypt ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 43372c0e-496d-4db1-86ee-a17b906b305d
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 43372c0e-496d-4db1-86ee-a17b906b305d
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1b0716c-dacd-4840-af32-db1c75f355e9
    linux /vmlinuz-2.6.35-22-generic root=UUID=691bcec8-94bb-4abe-8d2e-675d51dfe912 ro quiet splash
    initrd /initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b1b0716c-dacd-4840-af32-db1c75f355e9
    linux /vmlinuz-2.6.35-22-generic root=UUID=691bcec8-94bb-4abe-8d2e-675d51dfe912 ro single
    initrd /initrd.img-2.6.35-22-generic
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

============================= sdc1/grub/grub.cfg: =============================

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
set default="${saved_entry}"
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
set root=''
search --no-floppy --fs-uuid --set b2cb2a9c-b2d1-43dc-94f7-54cefd5ba5ad
set locale_dir=($root)
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail

    linux    /boot/vmlinuz-2.6.35-27-generic root=/dev/mapper/sdc5_crypt ro   quiet nosplash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail

    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=/dev/mapper/sdc5_crypt ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {

    linux16    
}
menuentry "Memory test (memtest86+, serial console 115200)" {

    linux16     console=ttyS0,115200n8
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

=================== sdc1: Location of files loaded by Grub: ===================


    .2GB: boot/grub/core.img
    .1GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-27-generic
    .0GB: vmlinuz-2.6.35-27-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  96 56 b0 9d f6 4a 65 8d  95 27 b2 26 5e 6d d0 cf  |.V...Je..'.&^m..|
00000010  53 a3 87 0c e4 b5 06 86  eb b3 5b b1 bd a4 53 85  |S.........[...S.|
00000020  c6 d4 fe 96 71 c7 a3 46  8e 11 ca 16 4e 87 03 68  |....q..F....N..h|
00000030  89 ac c8 89 bd 9a 48 de  71 e8 c1 74 4c 2c 35 85  |......H.q..tL,5.|
00000040  2d 24 6c 34 04 79 19 12  40 07 1a 4b 81 de 36 d3  |-$l4.y..@..K..6.|
00000050  9e 37 f1 9e 03 0a d6 22  6a 0c 5a 1c f8 80 d5 87  |.7....."j.Z.....|
00000060  93 34 7c e2 84 38 48 8f  27 dc 93 d9 6a 01 06 4d  |.4|..8H.'...j..M|
00000070  f0 f9 6e 64 ff e3 1a 31  60 47 9f 72 51 1e de 42  |..nd...1`G.rQ..B|
00000080  79 e1 09 88 5a c5 a0 f5  9d 66 eb 52 2f 06 38 f0  |y...Z....f.R/.8.|
00000090  39 22 a0 ce 1a ce cd 01  dd 6c 71 89 31 c5 09 db  |9".......lq.1...|
000000a0  25 ad 59 6d ed 3f f4 7a  0f a8 df 93 9d 03 dd 82  |%.Ym.?.z........|
000000b0  af 18 ed 15 97 5c b4 30  8b be d0 25 d9 04 b3 24  |.....\.0...%...$|
000000c0  d4 dc fc 08 d5 90 15 07  d0 58 3c ee df aa 06 b9  |.........X<.....|
000000d0  89 91 10 14 29 01 e2 d0  f5 0e 98 20 0f dd c4 68  |....)...... ...h|
000000e0  5a c2 6a d1 13 09 c4 73  bf d6 0a df 20 29 2d 6c  |Z.j....s.... )-l|
000000f0  43 a2 96 50 64 46 36 c0  e9 ab 38 dd 15 9a 6e 82  |C..PdF6...8...n.|
00000100  61 4d 33 eb 7a 6e e5 ea  85 9e 97 72 67 a8 7d 33  |aM3.zn.....rg.}3|
00000110  e5 73 6b 90 27 5d bc ed  f1 1e 36 3d fa 08 3a be  |.sk.']....6=..:.|
00000120  ce 58 b4 c7 62 fc 2e a1  1f 55 2b 47 2c 5d 6b 74  |.X..b....U+G,]kt|
00000130  13 32 78 3e 61 3c 33 5f  b7 85 a9 c1 11 40 cc 29  |.2x>a<3_.....@.)|
00000140  a7 93 f2 f3 da dd ff 48  4a 4e c6 6b eb 6a 99 2f  |.......HJN.k.j./|
00000150  3d 3a a2 70 ff 26 3e 12  26 aa 5e b8 66 b4 28 27  |=:.p.&>.&.^.f.('|
00000160  10 dc 03 b0 bc 0e 11 c3  b2 3b dc 92 4a b5 1d ef  |.........;..J...|
00000170  90 df 1d 40 5c 5c b9 4c  af a3 12 99 27 4d 41 56  |...@\\.L....'MAV|
00000180  b4 b0 25 e3 81 64 94 be  12 f9 45 55 f9 2f 47 7b  |..%..d....EU./G{|
00000190  c9 92 3f 88 66 d3 b8 75  a9 12 e2 ba 1f dd d6 61  |..?.f..u.......a|
000001a0  a1 86 10 02 da 96 0c 1b  b9 1f e1 f3 a7 1f e1 97  |................|
000001b0  53 49 13 c7 e4 5b 8b c2  4b 66 ed 84 3e 33 00 ae  |SI...[..Kf..>3..|
000001c0  b7 f8 83 fe ff ff 02 00  00 00 00 b0 db 08 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 32 35 36 00 00  |........sha256..|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 08 08 00 00 00 20  |............... |
00000070  0a ec 6b 4d 94 12 46 d2  2a 22 97 09 71 cd b2 de  |..kM..F.*"..q...|
00000080  39 51 01 ad 4f 5c d4 57  be d3 ef 8c 7c be f5 66  |9Q..O\.W....|..f|
00000090  e2 d7 54 aa e0 18 cd 57  8c 27 3f 3b ea 29 86 ec  |..T....W.'?;.)..|
000000a0  4b 54 82 b5 00 00 75 30  61 32 65 31 61 61 61 32  |KT....u0a2e1aaa2|
000000b0  2d 65 38 63 64 2d 34 66  31 35 2d 62 64 30 35 2d  |-e8cd-4f15-bd05-|
000000c0  37 31 31 37 62 36 39 38  37 39 30 39 00 00 00 00  |7117b6987909....|
000000d0  00 ac 71 f3 00 01 d5 20  2c 5a 53 e0 a4 b9 ad 53  |..q.... ,ZS....S|
000000e0  3a 8d bb b1 17 c2 c6 07  d1 a4 cb 3e bf 8e 1e dc  |:..........>....|
000000f0  6e a9 69 3c f9 24 44 59  00 00 00 08 00 00 0f a0  |n.i<.$DY........|
00000100  00 ac 71 f3 00 01 c8 02  00 74 36 da 8b 35 96 22  |..q......t6..5."|
00000110  c0 f9 8b f0 b8 aa 1a 0f  65 3e 7f a5 e0 19 66 f1  |........e>....f.|
00000120  e5 65 bf 25 cd b1 e2 90  00 00 01 08 00 00 0f a0  |.e.%............|
00000130  00 ac 71 f3 00 01 c6 10  99 d9 db b7 76 ff 0a 7a  |..q.........v..z|
00000140  84 7e 4c 29 5d 8e 49 71  be 46 29 1d 67 bd 81 72  |.~L)].Iq.F).g..r|
00000150  a3 ab d2 5d 4f d9 e3 4e  00 00 02 08 00 00 0f a0  |...]O..N........|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader  on sdc2

00000000  23 c0 3c 78 73 5d 5e 85  97 01 64 16 0a 5f 75 0c  |#.<xs]^...d.._u.|
00000010  d5 51 d2 ab 66 81 03 9d  8e b6 06 8e 60 58 3b db  |.Q..f.......`X;.|
00000020  1d 7b e7 2d f5 5a 2d 8c  15 ee e9 1e a3 1e 6e db  |.{.-.Z-.......n.|
00000030  e9 32 ca ee ac 04 3d 05  0d 57 ec f7 8c f1 68 6f  |.2....=..W....ho|
00000040  86 3f d7 8d b6 b1 54 4a  0e 60 90 c5 aa 66 07 2c  |.?....TJ.`...f.,|
00000050  37 72 06 59 bb 5a 3b 74  1d 13 79 72 ec a2 91 ad  |7r.Y.Z;t..yr....|
00000060  6c 44 8d 4c 3d 0f 74 c0  80 b6 9f c4 12 57 9c ac  |lD.L=.t......W..|
00000070  32 38 dd e9 b1 7b c5 9f  e9 81 98 fd 34 27 e8 db  |28...{......4'..|
00000080  fa a5 6e 7b ba e4 ad e6  4f a3 ce 02 3e 38 76 44  |..n{....O...>8vD|
00000090  4c 22 44 55 47 53 a8 cd  3a fc 8a 8f 95 7f da bb  |L"DUGS..:.......|
000000a0  71 48 a4 0d 0b de 70 f8  5d 54 99 c6 6c d9 6e 10  |qH....p.]T..l.n.|
000000b0  15 83 0d b9 56 a4 ce 30  a8 fd 51 7f ab 14 ec 5f  |....V..0..Q...._|
000000c0  57 37 9c 8f 9a e9 10 9e  18 b3 ea 17 5b dc 36 7f  |W7..........[.6.|
000000d0  0d f9 3f 73 84 55 30 b3  ca 65 f2 05 e2 4b 89 78  |..?s.U0..e...K.x|
000000e0  89 5b fa 4b c5 6a 85 19  79 c0 bd b8 3c ce 33 90  |.[.K.j..y...<.3.|
000000f0  5b f6 18 d3 e0 d0 6e e1  b7 ca ea 6e 52 64 92 36  |[.....n....nRd.6|
00000100  3d 38 7b 28 6c 01 c5 3f  2b 38 a7 ad f9 c6 77 48  |=8{(l..?+8....wH|
00000110  1c e8 a6 bb f8 9c 74 99  ba ea cd 6a eb df 32 f5  |......t....j..2.|
00000120  a0 de 4e 36 0d de a5 2c  0e ba 86 42 da 43 99 d0  |..N6...,...B.C..|
00000130  87 86 7b cc c6 74 08 5a  c6 c2 ce 53 63 53 22 ff  |..{..t.Z...ScS".|
00000140  15 d7 5f 50 62 ba 0f 6f  5d ff 4c c5 ae bf 19 56  |.._Pb..o].L....V|
00000150  7d d9 02 34 29 d4 54 21  91 96 2c 90 17 77 f3 f2  |}..4).T!..,..w..|
00000160  4c ed 1d a3 02 3b 77 0b  ca 7d 98 60 d8 ff a6 13  |L....;w..}.`....|
00000170  09 1b 0c 52 61 ad f4 a7  52 de f0 3b 40 bf 8a 9e  |...Ra...R..;@...|
00000180  56 0e 9a a1 07 90 3b 4c  22 4e bf 16 3e 7a 30 42  |V.....;L"N..>z0B|
00000190  20 04 31 78 93 91 a5 42  ec b0 7b 6c bd f6 51 ba  | .1x...B..{l..Q.|
000001a0  f1 fd 87 64 8f f2 ad 00  cc 92 41 bf d3 7a 96 c2  |...d......A..z..|
000001b0  fc 07 68 84 3f 63 0e 92  0d 9c ec eb fc b3 81 cd  |..h.?c..........|
000001c0  be 11 62 9d 6a af 66 e5  cc 6b 26 bc 98 d8 2e 2b  |..b.j.f..k&....+|
000001d0  06 1e 24 2c da 6f aa d6  ed cd d3 1a a0 95 ba 7d  |..$,.o.........}|
000001e0  0b 4e 0c 31 d4 ca fc 7c  28 46 44 86 7e d6 a3 be  |.N.1...|(FD.~...|
000001f0  65 ca 57 dd 7e cf 16 81  e5 75 6c 23 60 ad 54 3c  |e.W.~....ul#`.T<|
00000200

Unknown BootLoader  on sdc3

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 32 35 36 00 00  |........sha256..|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 08 08 00 00 00 20  |............... |
00000070  99 87 43 0f 8b 2d 8d fe  81 7d 2d 6a be 13 e7 cb  |..C..-...}-j....|
00000080  13 2f 99 3d 67 87 6f 31  66 72 87 ab 04 76 3a 69  |./.=g.o1fr...v:i|
00000090  ba 16 73 ad d7 82 4b 3a  d2 b2 75 fa 27 24 d4 e7  |..s...K:..u.'$..|
000000a0  36 8b 9d b7 00 00 76 a7  31 31 31 32 39 34 39 65  |6.....v.1112949e|
000000b0  2d 36 37 65 63 2d 34 62  38 34 2d 62 33 39 66 2d  |-67ec-4b84-b39f-|
000000c0  61 36 30 36 37 63 35 31  38 39 66 66 00 00 00 00  |a6067c5189ff....|
000000d0  00 ac 71 f3 00 01 db e1  52 28 5b ac 92 f1 b9 76  |..q.....R([....v|
000000e0  01 11 9b 95 4e 7d 38 2d  30 78 36 84 1e a9 e2 87  |....N}8-0x6.....|
000000f0  36 13 c6 10 f3 3e 02 ed  00 00 00 08 00 00 0f a0  |6....>..........|
00000100  00 ac 71 f3 00 01 c5 f0  7f 44 04 4c 3a b1 62 aa  |..q......D.L:.b.|
00000110  58 ce ed 59 8e cc fa ae  24 a4 0e 6a 46 51 b2 06  |X..Y....$..jFQ..|
00000120  42 95 33 6f 50 b3 d3 5a  00 00 01 08 00 00 0f a0  |B.3oP..Z........|
00000130  00 00 de ad 00 01 bb 0b  56 2c ad 24 ba 54 de 85  |........V,.$.T..|
00000140  f0 40 24 fd 55 77 1b 87  e2 15 df 8b 6e c7 88 b4  |.@$.Uw......n...|
00000150  5a 66 d3 df b1 48 34 eb  00 00 02 08 00 00 0f a0  |Zf...H4.........|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader  on sdc4

00000000  f9 61 f8 27 37 d8 e3 a8  b9 50 85 72 10 9e 81 db  |.a.'7....P.r....|
00000010  97 b8 ef 88 0c bc f3 82  56 e8 eb 15 e1 20 39 5e  |........V.... 9^|
00000020  d9 f0 56 24 9e 9d 3a bc  1c 87 4d 37 63 52 47 4c  |..V$..:...M7cRGL|
00000030  35 99 e1 05 da 85 ef 27  c5 e2 c1 85 18 af c4 74  |5......'.......t|
00000040  9e 94 a1 5f 88 1c 6b 35  d5 c5 40 a8 36 4b 77 f8  |..._..k5..@.6Kw.|
00000050  c8 14 4b e2 d4 be eb f8  01 9f 45 4c d2 47 11 86  |..K.......EL.G..|
00000060  3b 82 e6 86 61 aa 58 a6  e2 e1 4c 34 0a e9 fd 45  |;...a.X...L4...E|
00000070  5a 9c b8 c8 50 a8 6e fe  78 f8 2b 47 8d 10 af 64  |Z...P.n.x.+G...d|
00000080  ac 04 ff c8 7b bc e1 cb  95 df 14 98 c5 ef 8a 26  |....{..........&|
00000090  13 08 d4 8b fb de 3d 08  b3 fc 0c 41 39 72 61 3c  |......=....A9ra<|
000000a0  ca 36 00 0b f2 93 22 db  bf 15 ae b1 6d e3 3c aa  |.6....".....m.<.|
000000b0  3d 86 8f 97 77 ce 62 df  d2 8d b4 94 5b 55 b7 93  |=...w.b.....[U..|
000000c0  08 62 7b 96 ed e8 12 df  9b 86 8c ac 90 a7 c8 62  |.b{............b|
000000d0  31 1f c4 f6 20 93 ba 37  7c cd a4 37 32 81 af 86  |1... ..7|..72...|
000000e0  7f 24 fc a1 fe 84 3b 98  bd 4f 01 11 dc 20 72 68  |.$....;..O... rh|
000000f0  f9 88 cf 55 95 74 f1 e5  bb 70 88 51 6f 62 ca c1  |...U.t...p.Qob..|
00000100  90 51 60 4e 9e d4 37 f3  dc 50 58 51 d3 e4 ad f1  |.Q`N..7..PXQ....|
00000110  cb eb bb 11 6c 2e 66 52  11 27 66 ea 1b 89 99 fa  |....l.fR.'f.....|
00000120  42 37 ce 2b 00 d8 24 52  81 7c 00 0c cc 5a 6a 07  |B7.+..$R.|...Zj.|
00000130  17 4b b3 03 6e 3c 73 2d  bf 59 3c 77 9c 9c 07 9e  |.K..n<s-.Y<w....|
00000140  c3 41 01 8b 8c 73 c5 04  ba 07 0f 91 89 35 de 53  |.A...s.......5.S|
00000150  f8 bd 01 f7 9f a2 63 39  c9 fe f4 4b a4 93 ca e6  |......c9...K....|
00000160  9a a3 76 8d 0c fc 6f 51  6e 10 02 c9 ea 8f 21 50  |..v...oQn.....!P|
00000170  d1 af 80 b6 27 77 b0 53  5e 38 83 98 de 5f ae 86  |....'w.S^8..._..|
00000180  8c 8c 6a d8 1e b5 b6 05  24 3d 10 c6 41 81 e3 8e  |..j.....$=..A...|
00000190  95 d9 73 f1 c0 4b 36 89  f0 7f af 9e b3 76 5f a6  |..s..K6......v_.|
000001a0  47 45 6c 9d 10 fb 21 67  dc 30 b1 8c 09 f8 91 a8  |GEl...!g.0......|
000001b0  f8 82 1e 5e a0 04 55 49  25 b2 d5 11 6e 20 00 fe  |...^..UI%...n ..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c0 b6 06 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 c0  b6 06 00 08 d3 09 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc5

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 08 08 00 00 00 20  |............... |
00000070  38 ea ce 75 a7 74 0a 71  14 af f6 bf cf 40 c0 c0  |8..u.t.q.....@..|
00000080  aa 69 3e de d3 2e 06 d6  1b 8b 5e 07 cb a1 c6 27  |.i>.......^....'|
00000090  d4 8f 42 59 57 65 de 5b  9a 03 77 21 f6 ce 29 b7  |..BYWe.[..w!..).|
000000a0  ee b8 81 09 00 00 dd 31  36 35 39 62 38 65 66 64  |.......1659b8efd|
000000b0  2d 65 30 61 32 2d 34 62  61 63 2d 61 33 64 36 2d  |-e0a2-4bac-a3d6-|
000000c0  33 30 62 39 30 31 63 66  36 34 38 39 00 00 00 00  |30b901cf6489....|
000000d0  00 ac 71 f3 00 03 6d 86  30 b9 f6 db 09 b4 c7 89  |..q...m.0.......|
000000e0  0f 2c fc 94 c2 9e b2 ab  48 ec 09 74 9a 9f 21 4d  |.,......H..t..!M|
000000f0  b7 39 e3 cc 97 f7 d3 bd  00 00 00 08 00 00 0f a0  |.9..............|
00000100  00 00 de ad 00 03 4d 6c  5a 48 18 0c df 03 6b 20  |......MlZH....k |
00000110  b0 08 27 63 e7 e1 1b b8  91 dd 82 27 f6 e6 90 6c  |..'c.......'...l|
00000120  5a bc a8 e1 16 60 b7 b5  00 00 01 08 00 00 0f a0  |Z....`..........|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader  on sdc6

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 08 08 00 00 00 20  |............... |
00000070  03 41 c4 61 35 e2 a3 4e  7b 6b 3e 42 b3 61 78 84  |.A.a5..N{k>B.ax.|
00000080  ed 01 21 55 e8 4f 46 52  b5 08 4b 78 36 7e c9 a7  |..!U.OFR..Kx6~..|
00000090  71 3a 9e ea e0 61 85 a1  1c 9b 23 73 67 77 35 4b  |q:...a....#sgw5K|
000000a0  75 f4 fc ca 00 00 e2 13  30 65 37 66 33 32 31 64  |u.......0e7f321d|
000000b0  2d 34 63 34 63 2d 34 64  34 66 2d 39 35 63 35 2d  |-4c4c-4d4f-95c5-|
000000c0  39 66 37 31 31 35 65 34  38 37 30 66 00 00 00 00  |9f7115e4870f....|
000000d0  00 ac 71 f3 00 03 41 88  b6 d5 12 59 f1 f0 e5 00  |..q...A....Y....|
000000e0  c7 78 5f 9d a4 8b 44 2f  7b 02 9f 5f 0a 41 f5 da  |.x_...D/{.._.A..|
000000f0  68 81 21 8b 54 9f 59 44  00 00 00 08 00 00 0f a0  |h.!.T.YD........|
00000100  00 ac 71 f3 00 03 80 f8  b8 13 65 c6 ff 5f 28 30  |..q.......e.._(0|
00000110  24 62 74 33 c5 ed d1 ba  a0 ce e9 e3 f9 38 b4 45  |$bt3.........8.E|
00000120  2e 5c 71 81 e0 82 d5 66  00 00 01 08 00 00 0f a0  |.\q....f........|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 02 08 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 03 08 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 04 08 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 05 08 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200



```

---

### Post by Krytarik on 2011-03-17
Ok then, the current state is:

- there are two Grub boot loaders installed, on sda and sdc
- both are looking for /grub/grub.cfg in the first partition of their respective disks

- there are three (!) grub.cfg:
1.) sda1/grub/grub.cfg - is set up to boot sda
2.) sdc1/grub.cfg - is set up to boot sda and sdc
3.) sdc1/grub/grub.cfg - was generally set up to boot sdc, but is broken

- you have apparently selected "sda" as the boot device in your BIOS

- you have apparently also encrypted the root partition of sdc (sdc5), which may be the reason why those OS is not automatically included in sda1/grub/grub.cfg


So, my initial approach would be that way:
- boot into Xubuntu
- backup sdc1/grub/grub.cfg
- copy sdc1/grub.cfg to sdc1/grub
- reboot
- choose "sdc" as the boot device in your BIOS
- boot hopefully successful into sdc
- run "sudo update-grub"
- check if sdc1/grub/grub.cfg got updated

Good luck!

PS: Please remove the results from post #3 to make the thread more readable, not at least also for others.

Addition: Please check if "sdc1/boot/grub/core.img" is present since it is stated as a Grub boot file, but that would not make sense, since it is a dedicated boot partition. If the file is not there, the boot would imo fail.

---

