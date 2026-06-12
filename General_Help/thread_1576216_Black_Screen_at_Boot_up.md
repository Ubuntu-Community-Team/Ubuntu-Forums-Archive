---
title: "Black Screen at Boot up"
date: 2010-09-16
forum: General Help
---

### Post by cboxhero on 2010-09-16
I've been using Ubuntu on my laptop for sometime now. For a while it was  working fine and one day I went to use it and just showed something  saying:

GNU GRUB Version 1.98-1ubuntu7
Minimal Bach- ect. ect.

grub>

I have no idea how to get out of this. Help? :sad:

All I really know is that I need to put in some kind of code or something.

---

### Post by cboxhero on 2010-09-16
REALLY need help with this.

---

### Post by xenorecor on 2010-09-16
> **cboxhero said:**
> I've been using Ubuntu on my laptop for sometime now. For a while it was  working fine and one day I went to use it and just showed something  saying:

GNU GRUB Version 1.98-1ubuntu7
Minimal Bach- ect. ect.

grub>

I have no idea how to get out of this. Help? :sad:

All I really know is that I need to put in some kind of code or something.

Sounds like your GRUB entries were erased...

What version of Ubuntu were you using?  If they really got erased, you'll have to type where you need to boot from then edit the "menu.lst" file in "/boot/grub/menu.lst"

But first, the version of Ubuntu ;)

---

### Post by drs305 on 2010-09-16
cboxhero, welcome to the Ubuntu forums.

It's hard to tell what your problem is without more information. Please go to this site and run *meierfra's* boot info script after booting the LiveCD. It will gather the information we need to assess the status of your installation.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

Paste the results here, between code tags, which you can generate by pressing the # icon in the post menubar.

---

### Post by cboxhero on 2010-09-16
> **xenorecor said:**
> Sounds like your GRUB entries were erased...

What version of Ubuntu were you using?  If they really got erased, you'll have to type where you need to boot from then edit the "menu.lst" file in "/boot/grub/menu.lst"

But first, the version of Ubuntu ;)
Well, I got it maybe half a year ago. I'm not sure what version it was. How could I know?

---

### Post by drs305 on 2010-09-16
I'm logging off for the night but if you post the script results someone else might happen along that can tell you how to fix it.

Since you are at the grub prompt and using Grub 2, it means that Grub has no idea where your boot files are located. The script will tell us.

If you are comfortable with the command line/terminal (or if you aren't but are willing to try), you can try booting from the Grub prompt following the instructions here. Grub 2 can recover from a lot of situations from the command line if the correct entries are made. They aren't difficult but you have to understand the concept of what you are trying to do or it may be frustrating. 

[https://help.ubuntu.com/community/Grub2#Using CLI to Boot]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot")

I'll check back in the morning.

---

### Post by Bitech on 2010-11-06
Hi, I may not be the same user above but I have th exact same problem he does. 
Here's the info on my computer. I am using Ubuntu 10.04 LTS
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 437009952 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 439769016 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    25,173,854    25,173,792  27 Hidden HPFS/NTFS
/dev/sda2    *     25,173,855    25,382,699       208,845   7 HPFS/NTFS
/dev/sda3          25,382,700   276,366,194   250,983,495   7 HPFS/NTFS
/dev/sda4         276,366,256   488,396,799   212,030,544   f W95 Ext d (LBA)
/dev/sda5         276,366,258   285,812,414     9,446,157   b W95 FAT32
/dev/sda6         285,822,976   389,000,403   103,177,428  83 Linux
/dev/sda7         389,001,216   476,248,063    87,246,848  83 Linux
/dev/sda8         476,250,112   480,069,631     3,819,520  82 Linux swap / Solaris
/dev/sda9         480,073,728   488,396,799     8,323,072  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2087 MB, 2087976960 bytes
28 heads, 27 sectors/track, 5394 cylinders, total 4078080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            237     4,078,079     4,077,843   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        727044F37044BF99                       ntfs       PQSERVICE                     
/dev/sda2        F4F4454FF4451570                       ntfs       SYSTEM RESERVED               
/dev/sda3        7E5C46F85C46AAAB                       ntfs       Acer                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        1C0B-335B                              vfat       MOZ PROFILE                   
/dev/sda6        9f2a049f-f14d-4aa6-927c-93e62dee3ca0   ext4                                     
/dev/sda7        047c520e-cdfe-4f1d-bbff-3246ac322e02   ext4                                     
/dev/sda8        9cc7128b-6711-4024-9525-5dc1436ad709   swap                                     
/dev/sda9        0b024749-ec8a-49fe-879f-36b2ae79a7ad   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        38DC-1F90                              vfat       MYLINUXLIVE                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set default="9"
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
search --no-floppy --fs-uuid --set 9f2a049f-f14d-4aa6-927c-93e62dee3ca0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 9f2a049f-f14d-4aa6-927c-93e62dee3ca0
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=9f2a049f-f14d-4aa6-927c-93e62dee3ca0 ro acpi_backlight=vendor  quiet splash nolapic acpi_backlight=vendor
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 9f2a049f-f14d-4aa6-927c-93e62dee3ca0
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=9f2a049f-f14d-4aa6-927c-93e62dee3ca0 ro single acpi_backlight=vendor
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 9f2a049f-f14d-4aa6-927c-93e62dee3ca0
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=9f2a049f-f14d-4aa6-927c-93e62dee3ca0 ro acpi_backlight=vendor  quiet splash nolapic acpi_backlight=vendor
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 9f2a049f-f14d-4aa6-927c-93e62dee3ca0
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=9f2a049f-f14d-4aa6-927c-93e62dee3ca0 ro single acpi_backlight=vendor
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows 7? {
set root=(hd0,3)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 9f2a049f-f14d-4aa6-927c-93e62dee3ca0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 9f2a049f-f14d-4aa6-927c-93e62dee3ca0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=9f2a049f-f14d-4aa6-927c-93e62dee3ca0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0b024749-ec8a-49fe-879f-36b2ae79a7ad none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 198.0GB: boot/grub/core.img
 165.8GB: boot/grub/grub.cfg
 147.5GB: boot/initrd.img-2.6.32-25-generic
 153.5GB: boot/initrd.img-2.6.35-23-generic
 198.0GB: boot/vmlinuz-2.6.32-25-generic
 198.1GB: boot/vmlinuz-2.6.35-23-generic
 153.5GB: initrd.img
 198.1GB: vmlinuz

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=047c520e-cdfe-4f1d-bbff-3246ac322e02 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=0b024749-ec8a-49fe-879f-36b2ae79a7ad none            swap    sw              0       0
# swap was on /dev/sda9 during installation
UUID=9cc7128b-6711-4024-9525-5dc1436ad709 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 240.3GB: boot/grub/core.img
 240.3GB: boot/initrd.img-2.6.32-25-generic-pae
 240.2GB: boot/vmlinuz-2.6.32-25-generic-pae
 240.3GB: initrd.img
 240.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  73 6e 64 5f 6b 63 6f 6e  74 72 6f 6c 5f 6e 65 77  |snd_kcontrol_new|
00000010  20 77 6d 39 30 38 31 5f  65 71 5f 63 6f 6e 74 72  | wm9081_eq_contr|
00000020  6f 6c 73 5b 5d 20 3d 20  7b 0a 53 4f 43 5f 53 49  |ols[] = {.SOC_SI|
00000030  4e 47 4c 45 5f 54 4c 56  28 22 45 51 31 20 56 6f  |NGLE_TLV("EQ1 Vo|
00000040  6c 75 6d 65 22 2c 20 57  4d 39 30 38 31 5f 45 51  |lume", WM9081_EQ|
00000050  5f 31 2c 20 31 31 2c 20  32 34 2c 20 30 2c 20 65  |_1, 11, 24, 0, e|
00000060  71 5f 74 6c 76 29 2c 0a  53 4f 43 5f 53 49 4e 47  |q_tlv),.SOC_SING|
00000070  4c 45 5f 54 4c 56 28 22  45 51 32 20 56 6f 6c 75  |LE_TLV("EQ2 Volu|
00000080  6d 65 22 2c 20 57 4d 39  30 38 31 5f 45 51 5f 31  |me", WM9081_EQ_1|
00000090  2c 20 36 2c 20 32 34 2c  20 30 2c 20 65 71 5f 74  |, 6, 24, 0, eq_t|
000000a0  6c 76 29 2c 0a 53 4f 43  5f 53 49 4e 47 4c 45 5f  |lv),.SOC_SINGLE_|
000000b0  54 4c 56 28 22 45 51 33  20 56 6f 6c 75 6d 65 22  |TLV("EQ3 Volume"|
000000c0  2c 20 57 4d 39 30 38 31  5f 45 51 5f 31 2c 20 31  |, WM9081_EQ_1, 1|
000000d0  2c 20 32 34 2c 20 30 2c  20 65 71 5f 74 6c 76 29  |, 24, 0, eq_tlv)|
000000e0  2c 0a 53 4f 43 5f 53 49  4e 47 4c 45 5f 54 4c 56  |,.SOC_SINGLE_TLV|
000000f0  28 22 45 51 34 20 56 6f  6c 75 6d 65 22 2c 20 57  |("EQ4 Volume", W|
00000100  4d 39 30 38 31 5f 45 51  5f 32 2c 20 31 31 2c 20  |M9081_EQ_2, 11, |
00000110  32 34 2c 20 30 2c 20 65  71 5f 74 6c 76 29 2c 0a  |24, 0, eq_tlv),.|
00000120  53 4f 43 5f 53 49 4e 47  4c 45 5f 54 4c 56 28 22  |SOC_SINGLE_TLV("|
00000130  45 51 35 20 56 6f 6c 75  6d 65 22 2c 20 57 4d 39  |EQ5 Volume", WM9|
00000140  30 38 31 5f 45 51 5f 32  2c 20 36 2c 20 32 34 2c  |081_EQ_2, 6, 24,|
00000150  20 30 2c 20 65 71 5f 74  6c 76 29 2c 0a 7d 3b 0a  | 0, eq_tlv),.};.|
00000160  0a 73 74 61 74 69 63 20  63 6f 6e 73 74 20 73 74  |.static const st|
00000170  72 75 63 74 20 73 6e 64  5f 6b 63 6f 6e 74 72 6f  |ruct snd_kcontro|
00000180  6c 5f 6e 65 77 20 6d 69  78 65 72 5b 5d 20 3d 20  |l_new mixer[] = |
00000190  7b 0a 53 4f 43 5f 44 41  50 4d 5f 53 49 4e 47 4c  |{.SOC_DAPM_SINGL|
000001a0  45 28 22 49 4e 31 20 53  77 69 74 63 68 22 2c 20  |E("IN1 Switch", |
000001b0  57 4d 39 30 38 31 5f 41  4e 41 4c 4f 47 55 00 fe  |WM9081_ANALOGU..|
000001c0  ff ff 0b fe ff ff 02 00  00 00 0d 23 90 00 00 fe  |...........#....|
000001d0  ff ff 05 fe ff ff 0f 23  90 00 15 86 26 06 00 00  |.......#....&...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```
Thanks

---

### Post by drs305 on 2010-11-06
Bitech,

You have Grub looking for grub.cfg on sda7 (10.04) but it doesn't exist there. There is a grub.cfg on sda6 (10.10). 

So it depends on which one you want to boot. 

If you want to have grub working off of 10.04, and are currently running 10.04, just run:
```
sudo update-grub
```

If you are currently booted to 10.10, and want 10.10's grub to control things, run:
```
sudo grub-install /dev/sda
sudo update-grub
```

If you want to change the one you aren't running or have to boot from a LiveCD tell us which one you want to boot and control.

If you can't boot, at the grub prompt, you may be able to boot into your sda6 install by typing the following and pressing ENTER:
```
configfile (hd0,6)/boot/grub/grub.cfg
```

---

### Post by Bitech on 2010-11-06
> **drs305 said:**
> Bitech,

You have Grub looking for grub.cfg on sda7 (10.04) but it doesn't exist there. There is a grub.cfg on sda6 (10.10). 

So it depends on which one you want to boot. 

If you want to have grub working off of 10.04, and are currently running 10.04, just run:
```
sudo update-grub
```If you are currently booted to 10.10, and want 10.10's grub to control things, run:
```
sudo grub-install /dev/sda
sudo update-grub
```If you want to change the one you aren't running or have to boot from a LiveCD tell us which one you want to boot and control.

If you can't boot, at the grub prompt, you may be able to boot into your sda6 install by typing the following and pressing ENTER:
```
configfile (hd0,6)/boot/grub/grub.cfg
```

Oh yea I forgot to mention I'm trying to do these off my Live CD, so the commands here require to mount dev. I'm also still kind of new to ubuntu so I'm trying to directly follow any commands given from advice. I'm wanting to use 10.04, but I'm going to have to use the boot from ubuntu 10.10

---

### Post by drs305 on 2010-11-06
> **Bitech said:**
> Oh yea I forgot to mention I'm trying to do these off my Live CD, so the commands here require to mount dev. I'm also still kind of new to ubuntu so I'm trying to directly follow any commands given from advice. I'm wanting to use 10.04, but I'm going to have to use the boot from ubuntu 10.10

From the LiveCD, to boot sda6 (10.10)
Note: I've written the commands so you can substitute sda7 if you want to boot 10.04:
```
sudo mkdir /mnt/temp
sudo mount /dev/sda**6** /mnt/temp
for i in /dev /dev/pts /proc /sys ; do sudo mount -B $i /mnt/temp$i; done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp
```
You will now be "root" in sda6 and the following commands will be run on the Ubuntu files in sda**6**. You are already 'root' so you don't use sudo with the commands. The first one just reinstalls Grub2, which shouldn't be required; the second creates /boot/grub/grub.cfg in sda**6**.
```
grub-install /dev/sda
update-grub

```
When you are done, exit:
```
exit
```
Unmount:
```
for i in /dev/pts /dev /proc /sys / ; do sudo umount /mnt/temp$i ; done
```
Reboot to Ubuntu 10.10

---

### Post by sikander3786 on 2010-11-06
^^^ drs305 already has covered it extensively.

---

### Post by Bitech on 2010-11-07
I actually solved my problem by copying the entire text from the grub from 10.10 (the one I don't use) and pasting it into the 10.04's grub. When I attempted to update-grub a partition list not found error came up and only my 10.04 ubuntu came up. So I booted into it and updated grub again and somehow I managed to get Windows 7 and ubuntu 10.10 to appear again in the list along with 10.04. 

So I'm guessing the other ubuntu partition managed to be a backup of grub when my current grub became corrupted. Was I lucky?

And thanks for the effort to help I thought this thread was pretty much dead before I decided to revive it.

---

