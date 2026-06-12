---
title: "Need help with Ubuntu dual boot partition"
date: 2011-01-01
forum: General Help
---

### Post by the_family_guy on 2011-01-01
Hi all,

I am having all kinds of grief with booting Ubuntu via Grub2 on a dual boot system (it came with Windows 7, I installed Ubuntu 10.10 on it via USB installer). The install went through without issues (or so it seemed), but when I booted Ubuntu via Grub2, my screen went into "initramfs". At that point, the only thing that seems to work is a force mount of the root partition : "mount -t ntfs-3g /dev/sda1 /root -force" (followed by "exit", sometimes I have to exit multiple times because of the slow mount)

At that command, Ubuntu boots fine, and shows the following on "sudo fdisk -l" :

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           97842      180784   666232711+   7  HPFS/NTFS
/dev/sda3          180784      182365    12701696    7  HPFS/NTFS
/dev/sda4              14       97841   785803265    5  Extended
/dev/sda5              14       91196   732421120   83  Linux
/dev/sda6           93627       94235     4881408   83  Linux
/dev/sda7           94235       97274    24413184   82  Linux swap / Solaris
/dev/sda8           97275       97841     4553728    b  W95 FAT32
/dev/sda9           91196       93626    19523584    b  W95 FAT32

Machine is HP Pavilion Elite (HPE-470f) with AMD64 (3.2GHz) + 8GB RAM + 1.5 TB HDD (which I have split into the above 9 partitions)

Here seems to be the offender (in /boot/grub/grub.cfg) :

menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 29dc5fdb-96d3-4eea-8768-6fa788dbfbac
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=29dc5fdb-96d3-4eea-8768-6fa788dbfbac ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}

So - is my best option to create a custom boot file in /etc/grub.d which overrides the above? What kind of bone-headed moves did I make when doing the original install, and is there any way to correct them? 

I sure hope I don't get used to the force mount (in initramfs) hack ...

Thanks a ton for your help,
-Peter Griffin

---

### Post by the_family_guy on 2011-01-01
I forgot to mention that:

(1) the boot goes into initramfs because it cannot find the device id 29dc5fdb-96d3-4eea-8768-6fa788dbfbac (/dev/sda6) that is set in grub.cfg

(2) my root partition is /dev/sda6 which is ext4 , while the boot seems to only work when /root is set to /dev/sda1 (which is NTFS)

Thanks,
-Peter

---

### Post by Whyzer on 2011-01-01
Just a stab here but...
When you installed when you partitioned, just after  you finished you came to a screen showing you your partitions, I believe it asks if they are correct before beginning to copy files. Right in that screen there is a button above the text saying "advanced" (I'm going from memory here so bear with me) when you hit that button it tells you where it will put the grub loader, it DEFAULTS TO sda(1). Hence why it isn't looking for grub on sda6. 
You may have to reinstall and set that properly, I am not sure if recovery mode will address it. Someone correct me if I am wrong. I had this happen to me as it kept trying to install it on 1 of my two RAID disks, which no longer made them of equal size. I reinstalled a couple of times before seeing that advanced button. Hope it only takes you one more install to fix it!

---

### Post by ajgreeny on 2011-01-01
Using a live CD download and run the Boot-info-script in my signature at the bottom.  The instructions are on the site, but when you copy the RESULTS.txt file back here, please paste it between the CODE tags that appear when you click on the # top right in the reply text box.

---

### Post by the_family_guy on 2011-01-01
```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2       1,571,815,665 2,904,281,087 1,332,465,423   7 HPFS/NTFS
/dev/sda3       2,904,281,088 2,929,684,479    25,403,392   7 HPFS/NTFS
/dev/sda4             208,894 1,571,815,423 1,571,606,530   5 Extended
/dev/sda5             208,896 1,465,051,135 1,464,842,240  83 Linux
/dev/sda6       1,504,114,688 1,513,877,503     9,762,816  83 Linux
/dev/sda7       1,513,879,552 1,562,705,919    48,826,368  82 Linux swap / Solaris
/dev/sda8       1,562,707,968 1,571,815,423     9,107,456   b W95 FAT32
/dev/sda9       1,465,053,184 1,504,100,351    39,047,168   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        60C2A225C2A20000                       ntfs       SYSTEM                        
/dev/sda2        32E2D051E2D01B45                       ntfs       OS                            
/dev/sda3        E2F25938F2591261                       ntfs       HP_RECOVERY                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        2d43f00a-1af6-44f0-ba31-05c8508cb741   ext4                                     
/dev/sda6        29dc5fdb-96d3-4eea-8768-6fa788dbfbac   ext4                                     
/dev/sda7        7d2f3600-fde2-4fe3-b5bc-cf6fd2231e58   swap                                     
/dev/sda8        7BED-F869                              vfat                                     
/dev/sda9        AE58-DDD2                              vfat                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda8        /extra1                  vfat       (rw,utf8,umask=007,gid=46)
/dev/sda9        /extra2                  vfat       (rw,utf8,umask=007,gid=46)
/dev/sda5        /home                    ext4       (rw,commit=0)


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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 29dc5fdb-96d3-4eea-8768-6fa788dbfbac
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 29dc5fdb-96d3-4eea-8768-6fa788dbfbac
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 29dc5fdb-96d3-4eea-8768-6fa788dbfbac
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=29dc5fdb-96d3-4eea-8768-6fa788dbfbac ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 29dc5fdb-96d3-4eea-8768-6fa788dbfbac
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=29dc5fdb-96d3-4eea-8768-6fa788dbfbac ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 29dc5fdb-96d3-4eea-8768-6fa788dbfbac
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=29dc5fdb-96d3-4eea-8768-6fa788dbfbac ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 29dc5fdb-96d3-4eea-8768-6fa788dbfbac
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=29dc5fdb-96d3-4eea-8768-6fa788dbfbac ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 29dc5fdb-96d3-4eea-8768-6fa788dbfbac
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 29dc5fdb-96d3-4eea-8768-6fa788dbfbac
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 60c2a225c2a20000
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set e2f25938f2591261
	chainloader +1
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=29dc5fdb-96d3-4eea-8768-6fa788dbfbac /               ext4    errors=remount-ro 0       1
# /extra1 was on /dev/sda8 during installation
UUID=7BED-F869  /extra1         vfat    utf8,umask=007,gid=46 0       1
# /extra2 was on /dev/sda9 during installation
UUID=AE58-DDD2  /extra2         vfat    utf8,umask=007,gid=46 0       1
/dev/sda5       /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=7d2f3600-fde2-4fe3-b5bc-cf6fd2231e58 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 773.4GB: boot/grub/core.img
 772.6GB: boot/grub/grub.cfg
 771.8GB: boot/initrd.img-2.6.35-22-generic
 771.9GB: boot/initrd.img-2.6.35-24-generic
 773.5GB: boot/vmlinuz-2.6.35-22-generic
 772.6GB: boot/vmlinuz-2.6.35-24-generic
 771.9GB: initrd.img
 771.8GB: initrd.img.old
 772.6GB: vmlinuz
 773.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  25 73 20 2d 20 43 72 65  61 74 65 50 61 72 74 79  |%s - CreateParty|
00000010  49 6e 66 6f 20 66 61 69  6c 65 64 20 25 58 00 00  |Info failed %X..|
00000020  25 73 20 53 74 6f 72 65  48 61 6e 64 53 68 61 6b  |%s StoreHandShak|
00000030  65 49 6e 66 6f 20 66 61  69 6c 65 64 20 25 78 2c  |eInfo failed %x,|
00000040  20 74 68 69 73 20 25 70  00 00 00 00 48 52 45 53  | this %p....HRES|
00000050  55 4c 54 20 66 61 69 6c  65 64 3a 20 25 30 38 78  |ULT failed: %08x|
00000060  20 3d 20 68 72 2e 20 43  72 65 61 74 65 4e 65 77  | = hr. CreateNew|
00000070  43 61 6c 6c 4c 65 67 00  4d 55 4c 54 49 50 41 52  |CallLeg.MULTIPAR|
00000080  54 59 5f 53 45 53 53 49  4f 4e 3a 3a 43 72 65 61  |TY_SESSION::Crea|
00000090  74 65 54 72 69 67 67 65  72 65 64 43 61 6c 6c 4c  |teTriggeredCallL|
000000a0  65 67 00 00 25 73 20 43  72 65 61 74 65 54 72 69  |eg..%s CreateTri|
000000b0  67 67 65 72 65 64 4f 75  74 67 6f 69 6e 67 43 61  |ggeredOutgoingCa|
000000c0  6c 6c 4c 65 67 20 66 6f  72 20 25 2e 2a 73 2c 20  |llLeg for %.*s, |
000000d0  74 68 69 73 20 25 70 00  25 73 20 43 68 65 63 6b  |this %p.%s Check|
000000e0  45 78 69 73 74 69 6e 67  43 61 6c 6c 4c 65 67 41  |ExistingCallLegA|
000000f0  6e 64 4c 6f 63 61 6c 46  6f 72 55 52 49 20 25 2e  |ndLocalForURI %.|
00000100  2a 73 20 66 61 69 6c 65  64 20 25 78 2c 20 74 68  |*s failed %x, th|
00000110  69 73 20 25 70 00 00 00  25 73 20 43 68 65 63 6b  |is %p...%s Check|
00000120  46 6f 72 45 78 69 73 74  69 6e 67 63 61 6c 6c 4c  |ForExistingcallL|
00000130  65 67 46 6f 72 55 52 49  20 25 53 20 66 61 69 6c  |egForURI %S fail|
00000140  65 64 20 25 78 2c 20 74  68 69 73 20 25 70 00 00  |ed %x, this %p..|
00000150  4d 55 4c 54 49 50 41 52  54 59 5f 53 45 53 53 49  |MULTIPARTY_SESSI|
00000160  4f 4e 3a 3a 4e 6f 74 69  66 79 41 6c 6c 41 64 64  |ON::NotifyAllAdd|
00000170  50 61 72 74 79 49 6e 51  75 65 75 65 44 69 73 63  |PartyInQueueDisc|
00000180  6f 6e 6e 65 63 74 00 00  25 73 20 51 75 65 72 79  |onnect..%s Query|
00000190  49 6e 74 65 72 66 61 63  65 20 63 68 69 6c 64 4e  |Interface childN|
000001a0  6f 64 65 20 25 70 20 66  6f 72 20 49 58 4d 4c 44  |ode %p for IXMLD|
000001b0  4f 4d 45 6c 65 6d 65 6e  74 20 66 61 69 6c 00 00  |OMElement fail..|
000001c0  34 0d 83 fe ff ff 02 00  00 00 00 b8 4f 57 00 fe  |4...........OW..|
000001d0  ff ff 05 fe ff ff 3c 95  a3 59 c6 2a 95 00 00 00  |......<..Y.*....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

---

### Post by ajgreeny on 2011-01-01
Well, according to the RESULTS.txt file, you don't have grub installed as the bootloader at all, but the windows MBR instead, so I am surprised that you got Ubuntu to boot at all.

I am assuming you have not used easybcd, which just exteneds the windows bootloader system and lets it boot ubuntu as well as windows, but whichever the case, I think you should restore grub2 to the MBR and thern boot to ubuntu and run sudo update-grub.

To restore grub2 see section 13 of [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by the_family_guy on 2011-01-01
> 
Well, according to the RESULTS.txt file, you don't have grub installed as the bootloader at all, but the windows MBR instead, so I am surprised that you got Ubuntu to boot at all.

I am assuming you have not used easybcd, which just exteneds the windows bootloader system and lets it boot ubuntu as well as windows, but whichever the case, I think you should restore grub2 to the MBR and thern boot to ubuntu and run sudo update-grub.

To restore grub2 see section 13 of Grub 2 Basics


I have actually installed easybcd on Windows 7 partition. This is currently the order in which I get to Ubuntu : 

(1) BIOS loads to EasyBCD which gives me an option between Windows 7 and Ubuntu 10.10

(2) on choosing Ubuntu 10.10, I get the set of options that come from grub.cfg 

(3) on choosing my flavor of the kernel, the system hangs for a few seconds, then gives me an "initramfs" screen complaining it could not find my device ID (UID corresponding to /dev/sda6)

(4) at that point, I do a "mount -t ntfs-3g /dev/sda1 /root -o force" followed by "exit" (on the "initramfs" prompt)

(5) Ubuntu boots normally and I can use it without any issues

So, from what you mention, a re-install of grub2 in /dev/sda6 should solve the issue, right? However, according to the instructions in [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) , the Grub re-install takes only "/dev/sda" as argument (no partition numbers are allowed), so how do I ensure it is installed in /dev/sda6 only? 

Also, I get /dev/sda6 when I do "grub-probe -t device /boot/grub"

Thanks a ton,
-Peter

---

### Post by the_family_guy on 2011-01-01
Quick update: I tried re-installing grub using the instructions on your link (and also using my USB install drive), but grub-setup dies because of missing boot.img file in boot/grub directory in the installation USB. To wit:


sudo grub-setup -d /media/PENDRIVE/boot/grub /dev/sda
grub-setup: error: cannot stat /media/PENDRIVE/boot/grub/boot.img.

Thanks
-Peter

---

### Post by the_family_guy on 2011-01-02
Any ideas on this one?

Also, to add to the last comment, the USB installer was created using Universal USB installer, from an ISO of Ubuntu 10.10 Desktop version (64bit) which was md5sum clean.

Thanks a lot,
-Peter

---

### Post by wilee-nilee on 2011-01-02
So your able to get into Ubuntu with some command entries.

When your in run in the terminal.

sudo grub-install /dev/sda
then run 
sudo update-grub

We are assuming here that esaybcd doesn't get in the way, shouldn't but things happen.

---

### Post by the_family_guy on 2011-01-03
> **wilee-nilee said:**
> So your able to get into Ubuntu with some command entries.

When your in run in the terminal.

sudo grub-install /dev/sda
then run 
sudo update-grub

We are assuming here that esaybcd doesn't get in the way, shouldn't but things happen.

I gave this a shot - but still have the same issues with dual booting (still have to force mount ntfs partition for Ubuntu).

Thanks,
-Peter

---

