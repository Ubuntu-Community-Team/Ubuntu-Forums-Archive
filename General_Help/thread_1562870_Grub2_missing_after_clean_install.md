---
title: "Grub2 missing after clean install"
date: 2010-08-28
forum: General Help
---

### Post by astrostar on 2010-08-28
hello all! :)

recently i had a crush on my computer caused by a power surge, had to reinstall the os since i couldnt boot.

the installation went clean and everything is working very well since but i am having a strange issue with grub - its missing ?

when i boot the computer start with default kernel and no grub menu is visual for me to choose from.

i tried to purge and reinstall grub2 grub-common and grub-pc packages, tried various things found on the grub2 faq pages including booting from livecd and reinstalling.

it appears as grub is installed correctly but its not running at boot ? dunno ?

i'm using ubuntu 10.04.1 LTS x64 on intel E2180 with 2gb ram.

i really dont know what else to try or what can be the cause for this ? please any help is appreciated :)

thanks,
elad

ps: here is fdisk -l

Disk /dev/sda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8e24055d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15017   120624021   83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe7c818a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30060   241449984    7  HPFS/NTFS
/dev/sdb2           30060       30402     2747392   82  Linux swap / Solaris

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x163d163c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        6374    51199123+  83  Linux
/dev/sdc3            6375       36482   241835937+   7  HPFS/NTFS
/dev/sdc4   *       36482       38914    19533824   83  Linux

---

### Post by afrowildo on 2010-08-28
What did you use to install Ubuntu? When I've installed using a USB flash drive, I've noticed that Grub seems to be getting installed on the flash drive by default, rather than the HDD, and that you have to manually specify otherwise.

---

### Post by oldfred on 2010-08-28
Since you have multiple drive, grub may have installed to a different drive than the one you are booting from. Did you use the advanced button to specify where to install grub.
[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)

If you want to see where everything is installed.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by astrostar on 2010-08-28
thank u all for your replys, ):P

1. when i installed ubuntu from usb, i did custom select grub's settings, i dont think that its related to something i selected wrong in the installation since this is not the 1st time im installing ubuntu or the first computer i install unbutu onto.

2. my ubuntu is installed on /dev/sdc4 , the swap is at /dev/sdb2.

3. as i said before, prior to posting here in the forums i already tried to manually purge/re-install grub to /dev/sdc  and to /dev/sdc4, using liveusb session. i actualy think i may tried to reinstall grub with every possible option :lolflag:

my system is configured with samba, a set of softwars and a few other things.. i really wouldnt like to reconfig / reinstall everything :confused: it will take me a day to recover the system if i reinstall.

so what should i do guys ? :( i never tried the support forums before but if its half as good as the actual os then i'm sure that my problems are half solved already hehe :P

ps: now i am getting a strange message from kdesudo after the i login into the xwindows, this may have been caused by my testings to fix grub, hope it wont cause problems other then annoying popup.


thanks


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #4 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #4 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 603949352 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders, total 241254720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   241,248,104   241,248,042  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   482,902,015   482,899,968   7 HPFS/NTFS
/dev/sdb2         482,902,016   488,396,799     5,494,784  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   102,398,309   102,398,247  83 Linux
/dev/sdc3         102,402,048   586,073,922   483,671,875   7 HPFS/NTFS
/dev/sdc4    *    586,074,112   625,141,759    39,067,648  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3d0c9ccc-e5a6-4739-8621-b301f25c5431   ext4       IDE                           
/dev/sda: PTTYPE="dos" 
/dev/sdb1        989E3B449E3B19E8                       ntfs       backup                        
/dev/sdb2        236b639c-9d51-4f0f-8865-cef96f00bcef   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        4235a188-a2bb-42b2-bf5e-f923992caecc   ext4       3dmax                         
/dev/sdc3        50BCF751BCF73058                       ntfs       Emule                         
/dev/sdc4        7276cdad-115f-4aa8-9165-36b0744a4c3a   ext4                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc4        /                        ext4       (rw)
/dev/sda1        /media/IDE               ext4       (rw)
/dev/sdc1        /media/3DMax             ext4       (rw)
/dev/sdb1        /media/Backup            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc3        /media/eMule             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sdc4/boot/grub/grub.cfg: ===========================

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
set root='(hd2,4)'
search --no-floppy --fs-uuid --set 7276cdad-115f-4aa8-9165-36b0744a4c3a
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd2,4)'
search --no-floppy --fs-uuid --set 7276cdad-115f-4aa8-9165-36b0744a4c3a
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
menuentry 'Ubuntu, with Linux 2.6.36-999-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,4)'
	search --no-floppy --fs-uuid --set 7276cdad-115f-4aa8-9165-36b0744a4c3a
	linux	/boot/vmlinuz-2.6.36-999-generic root=UUID=7276cdad-115f-4aa8-9165-36b0744a4c3a ro   quiet splash
	initrd	/boot/initrd.img-2.6.36-999-generic
}
menuentry 'Ubuntu, with Linux 2.6.36-999-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,4)'
	search --no-floppy --fs-uuid --set 7276cdad-115f-4aa8-9165-36b0744a4c3a
	echo	'Loading Linux 2.6.36-999-generic ...'
	linux	/boot/vmlinuz-2.6.36-999-generic root=UUID=7276cdad-115f-4aa8-9165-36b0744a4c3a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.36-999-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,4)'
	search --no-floppy --fs-uuid --set 7276cdad-115f-4aa8-9165-36b0744a4c3a
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=7276cdad-115f-4aa8-9165-36b0744a4c3a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,4)'
	search --no-floppy --fs-uuid --set 7276cdad-115f-4aa8-9165-36b0744a4c3a
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=7276cdad-115f-4aa8-9165-36b0744a4c3a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,4)'
	search --no-floppy --fs-uuid --set 7276cdad-115f-4aa8-9165-36b0744a4c3a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,4)'
	search --no-floppy --fs-uuid --set 7276cdad-115f-4aa8-9165-36b0744a4c3a
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

=============================== sdc4/etc/fstab: ===============================

/dev/sr0 /media/DVD udf,iso9660 ro 0 0
UUID=3d0c9ccc-e5a6-4739-8621-b301f25c5431 /media/IDE ext4 defaults 0 1
UUID=236b639c-9d51-4f0f-8865-cef96f00bcef swap swap sw 0 0
UUID=7276cdad-115f-4aa8-9165-36b0744a4c3a / ext4 defaults 0 1
UUID=989E3B449E3B19E8 /media/Backup ntfs-3g defaults 0 1
UUID=4235a188-a2bb-42b2-bf5e-f923992caecc /media/3DMax ext4 defaults 0 1
UUID=50BCF751BCF73058 /media/eMule ntfs-3g defaults 0 1

=================== sdc4: Location of files loaded by Grub: ===================


 309.3GB: boot/grub/core.img
 300.7GB: boot/grub/grub.cfg
 309.4GB: boot/initrd.img-2.6.32-24-generic
 305.0GB: boot/initrd.img-2.6.36-999-generic
 309.7GB: boot/vmlinuz-2.6.32-24-generic
 310.0GB: boot/vmlinuz-2.6.36-999-generic
 305.0GB: initrd.img
 309.4GB: initrd.img.old
 310.0GB: vmlinuz
 309.7GB: vmlinuz.old

---

### Post by QLee on 2010-08-29
[QUOTE=astrostar]...
1. when i installed ubuntu from usb, i did custom select grub's settings, i dont think that its related to something i selected wrong in the installation since this is not the 1st time im installing ubuntu or the first computer i install unbutu onto.

2. my ubuntu is installed on /dev/sdc4 , the swap is at /dev/sdb2.

3. as i said before, prior to posting here in the forums i already tried to manually purge/re-install grub to /dev/sdc  and to /dev/sdc4, using liveusb session.[/QUOTE]

When we look at the output from the boot info script, we see "
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub."

So, when the system boots (from sda), it looks for sda4 which does not exist. If you want to boot to sdc4, you will have to install GRUB to the MBR of sda pointing to sdc4. 



[QUOTE=astrostar]... i actualy think i may tried to reinstall grub with every possible option 
...
...[/QUOTE]

That's good, with that experience it will be easy to correct the error.

..Or, the way your system is configured currently, you could change the boot order and boot from the drive which is currently sdc.

---

### Post by oldfred on 2010-08-29
There is a bug in either grub or the script that mis report the drive used to boot. I have the same issue when I install a boot loader in sda and boot from sdc. It says same drive but is not. I assume it is correct.

I do not see anything in boot that looks wrong. Since you only have Ubuntu you will not get a menu unless you hold down the shift key from BIOS until menu appears.

You say you get a log in? Then it is not a boot issue but something not starting or a video issue.

let us know if you can get to menu and run recovery mode.

---

### Post by QLee on 2010-08-29
[QUOTE=oldfred]There is a bug in either grub or the script that mis report the drive used to boot. I have the same issue when I install a boot loader in sda and boot from sdc. It says same drive but is not. ...[/QUOTE]
That's not really a bug, oldfred, it's because GRUB also passes the UUID to the system, if the device node notation doesn't work, the system finds it by UUID. Edit: This is badly explained but it is not part of this posters question. When you "boot" from sdc, GRUB thinks it is sda, because that's what the BIOS thinks.

I do agree with you, if aerostar is booting OK, it would be something else but it isn't clear to me that the system is booting correctly but just with no GRUB menu display.

---

### Post by astrostar on 2010-08-29
thank all of you for your answers.

first, yes i can logon, i'm using ubuntu right now and its much better then windows hehe :lolflag: sadly 3dmax dont work well on wine so my workstation has to stay in windows.

back to grub.. i have an option to press F11 on boot and select boot device, i already tried to boot from any of the harddisks and in each case i get the same result - boot right into the ubuntu login screen without an option to select kernel or recovery mode. as u can see from the logs i posted i have a boot flag on all of the disks and i also tried to manually install grub on each of them ? the first solution i tried was to reinstall grub on another harddisk and boot from there but each time i got the same annoying result.

i think that the problem may be in the grub script ? it may be a bug but i dont think so since it worked well with the same versions and setup so the only reasonable difference is in the script or auto-generated settings, is there an option for editing them manually and change where grub look for its whatever ?

this whole thing is strange because i am using this computer as a ubuntu fileserver for more then a year now and ubuntu worked very well with the same exact hardware/bios setup before i had to reinstall due to the power surge.

whats now? any ideas? :confused: its like grub or something is auto booting to default/newest kernel without an option for choosing, a few days ago i updated the kernel to new stable version and when i restart i got the new kernel (again with no grub menu whatsoever).

thank all of you for your time and effort :D =D>

---

### Post by oldfred on 2010-08-29
If you only have Ubuntu installed it will automatically boot into Ubuntu without showning menu to speed up boot. If you want menu you have to hold down shift key from BIOS until menu appears.

General info:
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
drs305's hack to get hidden timeout to work:
[http://ubuntuforums.org/showthread.php?t=1319672](http://ubuntuforums.org/showthread.php?t=1319672)

---

### Post by astrostar on 2010-08-31
Hello everyone and again thank u all for your help,

I tried to boot with shift pressed and as a magic i got grub menu :) so then i knew that it has to be related to a setting issue...

I looked in /etc/defaults/grub and found GRUB_HIDDEN_TIMEOUT=0 string, i added a # before the line and now everything is working well :)

Now i know that the problem was caused by a setting that is different from what i know in previous versions/installations.

Thanks again,
Eald

---

