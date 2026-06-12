---
title: "Windows 7 boot partition gone.."
date: 2010-11-03
forum: General Help
---

### Post by moster on 2010-11-03
Well, I format that win7 small first partition to ext4 and make it boot partition for ubuntu and now there is no dual boot.

How to can I get windows again. I will deal with ubuntu and dual boot in different way...

---

### Post by Hippytaff on 2010-11-03
Did you format the windows partition to ext4?

download this boot script and follow the instructions...post the results.txt (on your desktop after you run the script) and people will have a better idea of what is going on :-)

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Irony on 2010-11-03
> **moster said:**
> Well, I format that win7 small first partition to ext4 and make it boot partition for ubuntu and now there is no dual boot.
You mean you've just formatted the system files and thus destroyed your Windows 7 install?

---

### Post by Quackers on 2010-11-03
Probably the first 2 boot files are gone.

---

### Post by Mark Phelps on 2010-11-03
> **Irony said:**
> You mean you've just formatted the system files and thus destroyed your Windows 7 install?

No, that would just wipe out the bootloader and its files.

The main Win7 OS partition is a different one and contains the OS, its files, and the rest of the setup.

---

### Post by moster on 2010-11-03
uh, guys I did not format windows partition but that little 200 mb boot partition that windows 7 create automatically.

here is attachment :)

---

### Post by Hippytaff on 2010-11-03
> **Irony said:**
> You mean you've just formatted the system files and thus destroyed your Windows 7 install?
That's what I was afraid of

---

### Post by Hippytaff on 2010-11-03
> **moster said:**
> uh, guys I did not format windows partition but that little 200 mb boot partition that windows 7 create automatically.

here is attachment :)
phew **wipes sweat from forehead**

---

### Post by Quackers on 2010-11-03
Your boot script, in code tags!

```
              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       btrfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       1892081656 sectors, but according to the info from 
                       fdisk, it has 1953523648 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800  83 Linux
/dev/sda2             206,848    61,442,047    61,235,200   7 HPFS/NTFS
/dev/sda3          61,442,048   484,491,263   423,049,216  83 Linux
/dev/sda4         484,491,264   488,394,751     3,903,488  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,523,711 1,953,523,649   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c109de24-21e4-4bbb-a179-e885f42195f5   ext4                                     
/dev/sda2        1C2C90E42C90B9EA                       ntfs                                     
/dev/sda3        95e5ce2b-b4c1-4d2d-8ce2-38c911f6ebc7   btrfs                                    
/dev/sda4        d6d32f5c-b9da-4e88-87ed-bc4e7380bbe5   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A096D4D096D4A854                       ntfs       Mrcina                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        btrfs      (rw)
/dev/sda1        /boot                    ext4       (rw,commit=0)


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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c109de24-21e4-4bbb-a179-e885f42195f5
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
	search --no-floppy --fs-uuid --set c109de24-21e4-4bbb-a179-e885f42195f5
	linux	/vmlinuz-2.6.35-22-generic root=/dev/sda3 ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c109de24-21e4-4bbb-a179-e885f42195f5
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=/dev/sda3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c109de24-21e4-4bbb-a179-e885f42195f5
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c109de24-21e4-4bbb-a179-e885f42195f5
	linux16	/memtest86+.bin console=ttyS0,115200n8
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
UUID=95e5ce2b-b4c1-4d2d-8ce2-38c911f6ebc7 /               btrfs   defaults        0       1
# /boot was on /dev/sda1 during installation
UUID=c109de24-21e4-4bbb-a179-e885f42195f5 /boot           ext4    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=d6d32f5c-b9da-4e88-87ed-bc4e7380bbe5 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  31.5GB: initrd.img
  31.4GB: vmlinuz
```

---

### Post by Hippytaff on 2010-11-03
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       btrfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       1892081656 sectors, but according to the info from 
                       fdisk, it has 1953523648 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800  83 Linux
/dev/sda2             206,848    61,442,047    61,235,200   7 HPFS/NTFS
/dev/sda3          61,442,048   484,491,263   423,049,216  83 Linux
/dev/sda4         484,491,264   488,394,751     3,903,488  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,523,711 1,953,523,649   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c109de24-21e4-4bbb-a179-e885f42195f5   ext4                                     
/dev/sda2        1C2C90E42C90B9EA                       ntfs                                     
/dev/sda3        95e5ce2b-b4c1-4d2d-8ce2-38c911f6ebc7   btrfs                                    
/dev/sda4        d6d32f5c-b9da-4e88-87ed-bc4e7380bbe5   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A096D4D096D4A854                       ntfs       Mrcina                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        btrfs      (rw)
/dev/sda1        /boot                    ext4       (rw,commit=0)


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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c109de24-21e4-4bbb-a179-e885f42195f5
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
    search --no-floppy --fs-uuid --set c109de24-21e4-4bbb-a179-e885f42195f5
    linux    /vmlinuz-2.6.35-22-generic root=/dev/sda3 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c109de24-21e4-4bbb-a179-e885f42195f5
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=/dev/sda3 ro single 
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
    search --no-floppy --fs-uuid --set c109de24-21e4-4bbb-a179-e885f42195f5
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c109de24-21e4-4bbb-a179-e885f42195f5
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
UUID=95e5ce2b-b4c1-4d2d-8ce2-38c911f6ebc7 /               btrfs   defaults        0       1
# /boot was on /dev/sda1 during installation
UUID=c109de24-21e4-4bbb-a179-e885f42195f5 /boot           ext4    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=d6d32f5c-b9da-4e88-87ed-bc4e7380bbe5 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  31.5GB: initrd.img
  31.4GB: vmlinuz

```

---

### Post by moster on 2010-11-03
> **Hippytaff said:**
> phew **wipes sweat from forehead**

Is that mean that windows installation is saved theoretically or what? :)


I did not think too much about installing ubuntu and I forgot about old problem too. I have freezing problem on heavy disk IO. But leave that for now... Lets get back on problem no1. :)

---

### Post by Hippytaff on 2010-11-03
> **moster said:**
> Is that mean that windows installation is saved theoretically or what? :)
:)

Not necessarily :-) but that would be the worst case scenario

---

### Post by moster on 2010-11-03
> **Hippytaff said:**
> Not necessarily :-) but that would be the worst case scenario

If I make it from here I will put buntu on disk 1 and windows on disk 2 without any grub. And in bios switch between them. Is that sounds to you as good idea?

---

### Post by theozzlives on 2010-11-03
The "System" partition is there so you could encrypt your whole "Drive C:" and still boot. If you don't use BitLocker, you don't need it.

---

### Post by Quackers on 2010-11-03
To get Windows booting you need to move the boot flag from partition 1 to partition 2, then run the Windows startup repair program 3 times to fix the mbr.

So boot from the Windows repair disk and choose the repair option and then choose the advanced options (I think it's called) which leads to a screen with several choices. 
Choose the command prompt option then type these commands - pressing enter after each one (but not the stuff after the # sign)
```
diskpart
select disk 0
select partition 2  #  if there is no recovery partition
active
exit
```

then go back to the startup repair option and run that 3 times.

Hopefully Windows will then boot.

---

### Post by Hippytaff on 2010-11-03
> **moster said:**
> If I make it from here I will put buntu on disk 1 and windows on disk 2 without any grub. And in bios switch between them. Is that sounds to you as good idea?
Are you using too seperate hard discs?...If not I think you need grub...I've read that you can use the windows boot loader but I know nothing about that

---

### Post by moster on 2010-11-03
Thanks everybody, I am going to do something I will probably regret. (again) :)

---

### Post by Hippytaff on 2010-11-03
Before you do something you regret follow quckers instructions :-)

---

### Post by moster on 2010-11-13
Let me tell what I did. These seems far bes solution I tried so far.

I went to bios and put HDD maxtor on 1.st place. Then I installed windows.

Then, I went to bios and put other HDD WD on first place. Then I installed ubuntu.

Now, when that second disk is in first place I have grub menu and I can boot both OSs. And when I put first, maxtor disk on first place , windows is booting automatically without any menu. So, whatever happend now with any OS, I can still boot safely that other one :)

---

### Post by Hippytaff on 2010-11-13
Excellent, glad you got it sorted :-)

---

