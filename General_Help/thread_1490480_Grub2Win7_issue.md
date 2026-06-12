---
title: "Grub2/Win7 issue"
date: 2010-05-22
forum: General Help
---

### Post by Whiterin on 2010-05-22
Alright, so the problem started with I updated to 10.04. I had to reinstall Grub because it wouldn't load anything. So, I reinstalled it, and it loaded Ubuntu. It still takes longer then it should to load Ubuntu, but it does load. When I tried to load Windows 7 however, it would just sit with a blinking cursor. So, I completely removed Grub, reinstalled, and made sure it was updated. Ubutnu still loads, still slowly, and now when I select Windows 7, it shows two blinks of the flashing cursor, then goes back to the menu. No matter how many times I try to load it, it just goes back to the menu. I have reinstalled, removed, and updated Grub2 probably half a dozen times with no change. Does anyone know how to get this working again? Not that I use it much, but I would like access to my other partition and the stuff installed there. I know I can access files and such, and a good amount of the programs will load through Wine, but I would still prefer being able to boot into windows. So, any help would be appreciated. Thanks!

---

### Post by arrange on 2010-05-22
Please provide the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/"). (If you don't know how to run the script, [look here]("http://bootinfoscript.sourceforge.net/").)

---

### Post by kansasnoob on 2010-05-22
> **Whiterin said:**
> Alright, so the problem started with I updated to 10.04. I had to reinstall Grub because it wouldn't load anything. So, I reinstalled it, and it loaded Ubuntu. It still takes longer then it should to load Ubuntu, but it does load. When I tried to load Windows 7 however, it would just sit with a blinking cursor. So, I completely removed Grub, reinstalled, and made sure it was updated. Ubutnu still loads, still slowly, and now when I select Windows 7, it shows two blinks of the flashing cursor, then goes back to the menu. No matter how many times I try to load it, it just goes back to the menu. I have reinstalled, removed, and updated Grub2 probably half a dozen times with no change. Does anyone know how to get this working again? Not that I use it much, but I would like access to my other partition and the stuff installed there. I know I can access files and such, and a good amount of the programs will load through Wine, but I would still prefer being able to boot into windows. So, any help would be appreciated. Thanks!

As arrange said it woul be helpful to see the output of the Boot Info Script but what you describe sounds like this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

But, if you have the slightest doubt post that output!

---

### Post by Whiterin on 2010-05-22
Here are the results.

   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 174174143 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 174159431 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 174159431 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 174159431 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    25,173,854    25,173,792  27 Hidden HPFS/NTFS
/dev/sda2    *     25,173,855    25,382,699       208,845   7 HPFS/NTFS
/dev/sda3          25,382,700   173,887,559   148,504,860   7 HPFS/NTFS
/dev/sda4         173,887,560   488,392,064   314,504,505   5 Extended
/dev/sda5         173,887,623   480,584,474   306,696,852  83 Linux
/dev/sda6         480,584,538   488,392,064     7,807,527  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F68C63738C632CF5                       ntfs       PQSERVICE                     
/dev/sda2        70AC63ECAC63AB74                       ntfs       SYSTEM RESERVED               
/dev/sda3        86F464E6F464DA47                       ntfs       Acer                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        acd6a1a2-d5cb-4911-835c-e108c0d4ed77   ext4                                     
/dev/sda6        f80ad1e9-522c-4377-8e56-014f9eb052d5   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set acd6a1a2-d5cb-4911-835c-e108c0d4ed77
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set acd6a1a2-d5cb-4911-835c-e108c0d4ed77
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set acd6a1a2-d5cb-4911-835c-e108c0d4ed77
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=acd6a1a2-d5cb-4911-835c-e108c0d4ed77 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set acd6a1a2-d5cb-4911-835c-e108c0d4ed77
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=acd6a1a2-d5cb-4911-835c-e108c0d4ed77 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f68c63738c632cf5
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 70ac63ecac63ab74
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=acd6a1a2-d5cb-4911-835c-e108c0d4ed77 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f80ad1e9-522c-4377-8e56-014f9eb052d5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  89.1GB: boot/grub/core.img
  99.4GB: boot/grub/grub.cfg
  90.8GB: boot/initrd.img-2.6.31-21-generic
  90.8GB: boot/initrd.img-2.6.32-22-generic
  90.5GB: boot/vmlinuz-2.6.31-21-generic
 122.0GB: boot/vmlinuz-2.6.32-22-generic
  90.8GB: initrd.img
  90.8GB: initrd.img.old
 122.0GB: vmlinuz
  90.5GB: vmlinuz.old

---

### Post by poosietgp on 2010-05-22
have you tried ```
sudo update-grub
```? it should be able to reconfigure your grub.cfg and autodetect other OSes. And if ever you think you've installed other OSes properly and it still doesnt work try this: [HTML]http://ubuntuforums.org/showthread.php?t=1014708[/HTML].

Also, try reading up on this great guide: [HTML]http://ubuntuforums.org/showthread.php?t=1195275[/HTML], this guide has helped me countless of times and i hope you find it useful.

---

### Post by poosietgp on 2010-05-22
just checked your grub.cfg and it looks like grub is seeing your winvista and win7 installation. I think you should try fixing your windows bootrecord, it is possible that grub overwrote the bootrecord for windows 7. to restore bootrecord try this [HTML]http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector[/HTML].

---

### Post by arrange on 2010-05-22
Yes, *kansasnoob* was right, follow his advice. You accidentally installed Grub in the boot sectors of your Win partitions.

AFAIK you can also use the win recovery *fixboot* option.

---

### Post by Whiterin on 2010-05-22
Alright, thanks for the help so far guys, and for the speed of it! Going to grab the testdisk and see what it can do for me. This has been running and dual booting just fine since last November. Just starting having all these boot issues when I upgraded to 10.04. Hopefully this will help. Does anyone see anything in the boot info that would give a reason as to why Ubuntu is taking longer then it should to boot? It hags on the blinking cursor for about a minute. Before 10.04 it only took a second or two.

---

### Post by Whiterin on 2010-05-22
So, uhh... yeah. There is a change... not so sure it's a good one though. Followed the instructions on the link there. Now instead of it just going back to the Grub menu, I get some little symbols in the top left. Looks like = with an extra line, then a heart, then =S

Uhh, help? lol
Going to post the new boot test. Looks like it set the boot type of my Windows 7 to Windows XP. :|

            Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 174174143 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 174159431 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    25,173,854    25,173,792  27 Hidden HPFS/NTFS
/dev/sda2    *     25,173,855    25,382,699       208,845   7 HPFS/NTFS
/dev/sda3          25,382,700   173,887,559   148,504,860   7 HPFS/NTFS
/dev/sda4         173,887,560   488,392,064   314,504,505   5 Extended
/dev/sda5         173,887,623   480,584,474   306,696,852  83 Linux
/dev/sda6         480,584,538   488,392,064     7,807,527  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F68C63738C632CF5                       ntfs       PQSERVICE                     
/dev/sda2        70AC63ECAC63AB74                       ntfs       SYSTEM RESERVED               
/dev/sda3        86F464E6F464DA47                       ntfs       Acer                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        acd6a1a2-d5cb-4911-835c-e108c0d4ed77   ext4                                     
/dev/sda6        f80ad1e9-522c-4377-8e56-014f9eb052d5   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set acd6a1a2-d5cb-4911-835c-e108c0d4ed77
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set acd6a1a2-d5cb-4911-835c-e108c0d4ed77
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set acd6a1a2-d5cb-4911-835c-e108c0d4ed77
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=acd6a1a2-d5cb-4911-835c-e108c0d4ed77 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set acd6a1a2-d5cb-4911-835c-e108c0d4ed77
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=acd6a1a2-d5cb-4911-835c-e108c0d4ed77 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f68c63738c632cf5
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 70ac63ecac63ab74
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=acd6a1a2-d5cb-4911-835c-e108c0d4ed77 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f80ad1e9-522c-4377-8e56-014f9eb052d5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  89.1GB: boot/grub/core.img
 132.2GB: boot/grub/grub.cfg
  90.8GB: boot/initrd.img-2.6.31-21-generic
  90.8GB: boot/initrd.img-2.6.32-22-generic
  90.5GB: boot/vmlinuz-2.6.31-21-generic
 122.0GB: boot/vmlinuz-2.6.32-22-generic
  90.8GB: initrd.img
  90.8GB: initrd.img.old
 122.0GB: vmlinuz
  90.5GB: vmlinuz.old

---

### Post by arrange on 2010-05-22
[COLOR="Silver"]Now instead of it just going back to the Grub menu, I get some little symbols in the top left.[/COLOR]
After you've chosen *sda1* or *sda2* in the Grub menu? Or you don't see a Grub menu at all after reboot? Have you tried booting from both?

2. You haven't repaired the boot sector on *sda1*.

3. If *testdisk* doesn't work for you, you should use a win recovery disc and "fixboot".

---

### Post by oldfred on 2010-05-22
I do not know if the windows repairs work correctly on the separate boot partition. I am not sure I have seen anyone fix this except those who moved boot flag to the main install and repaired that, obsoleting the windows boot partition.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot sector 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

More info on moving boot partition back into the main install:
Win7 system partition info
[http://www.mydigitallife.info/2009/08/20/hack-to-remove-100-mb-system-reserved-partition-when-installing-windows-7/](http://www.mydigitallife.info/2009/08/20/hack-to-remove-100-mb-system-reserved-partition-when-installing-windows-7/)

---

### Post by Whiterin on 2010-05-24
Hmm, well, I tried to boot up the Windows recovery CD, and it errors out. Says something about not being able to connect to a device and won't let me go further. Tells me to make sure any removable devices are connected properly and to restart... even though there is nothing connected... so that's out. Stupid Windows. Anyways, any other ways to fix this or should I just remove the Windows stuff from the partition and use it for storage? lol

---

### Post by wilee-nilee on 2010-05-24
> **Whiterin said:**
> Hmm, well, I tried to boot up the Windows recovery CD, and it errors out. Says something about not being able to connect to a device and won't let me go further. Tells me to make sure any removable devices are connected properly and to restart... even though there is nothing connected... so that's out. Stupid Windows. Anyways, any other ways to fix this or should I just remove the Windows stuff from the partition and use it for storage? lol
 Did you download the neosmart recovery disc or is it a actual install disc.

---

### Post by oldfred on 2010-05-24
Did you move the boot flag to sda3. Windows is pretty dumb and only looks at active partitions (boot flag).

---

### Post by Whiterin on 2010-05-24
> **oldfred said:**
> Did you move the boot flag to sda3. Windows is pretty dumb and only looks at active partitions (boot flag).

Hmm, what does that entail? 

Also, I was using a Windows recovery CD. Well, the recovery CD that came with my laptop anyways.

---

### Post by oldfred on 2010-05-24
to set boot flag - should only be on primary partitions:
You can use gparted, right click on partition & manage flags, disk utility, or command line:
set boot flag on for sda3 (off on others)
sudo sfdisk -A3 /dev/sda

---

### Post by xnicodemusx on 2010-05-24
I also have hte same problem([http://ubuntuforums.org/showthread.php?t=1492251](http://ubuntuforums.org/showthread.php?t=1492251))
and here is my boot info script
```
   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 641328222 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 641321694 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   641,041,694   641,041,632   7 HPFS/NTFS
/dev/sdb2         641,041,695   976,768,064   335,726,370   5 Extended
/dev/sdb5         641,041,758   964,687,184   323,645,427  83 Linux
/dev/sdb6         964,687,248   976,768,064    12,080,817  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B678CF9E78CF5BAD                       ntfs       My Hard Drive                 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        BC449D46449D03F4                       ntfs       New Volume                    
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        3d7f6b30-9590-4608-ad84-6ba2de1e9e55   ext4                                     
/dev/sdb6        3695abf6-868b-4e6f-8892-7a4f4ebbb75e   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/My Hard Drive     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/New_Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 3d7f6b30-9590-4608-ad84-6ba2de1e9e55
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 3d7f6b30-9590-4608-ad84-6ba2de1e9e55
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 3d7f6b30-9590-4608-ad84-6ba2de1e9e55
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=3d7f6b30-9590-4608-ad84-6ba2de1e9e55 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 3d7f6b30-9590-4608-ad84-6ba2de1e9e55
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=3d7f6b30-9590-4608-ad84-6ba2de1e9e55 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 3d7f6b30-9590-4608-ad84-6ba2de1e9e55
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=3d7f6b30-9590-4608-ad84-6ba2de1e9e55 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 3d7f6b30-9590-4608-ad84-6ba2de1e9e55
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=3d7f6b30-9590-4608-ad84-6ba2de1e9e55 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 3d7f6b30-9590-4608-ad84-6ba2de1e9e55
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 3d7f6b30-9590-4608-ad84-6ba2de1e9e55
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b678cf9e78cf5bad
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    defaults    0    0
#Entry for /dev/sdb5 :
UUID=3d7f6b30-9590-4608-ad84-6ba2de1e9e55    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=B678CF9E78CF5BAD    /media/My\040Hard\040Drive    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-8    0    0
#Entry for /dev/sdb1 :
UUID=BC449D46449D03F4    /media/New_Volume    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sdb6 :
UUID=3695abf6-868b-4e6f-8892-7a4f4ebbb75e    none    swap    sw    0    0
/dev/scd0    /media/cdrom0    udf,iso9660    user,noauto,exec,utf8    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0



=================== sdb5: Location of files loaded by Grub: ===================


 328.3GB: boot/grub/core.img
 333.1GB: boot/grub/grub.cfg
 330.4GB: boot/initrd.img-2.6.31-21-generic
 330.4GB: boot/initrd.img-2.6.32-22-generic
 328.6GB: boot/vmlinuz-2.6.31-21-generic
 329.8GB: boot/vmlinuz-2.6.32-22-generic
 330.4GB: initrd.img
 330.4GB: initrd.img.old
 329.8GB: vmlinuz
 328.6GB: vmlinuz.old
```

---

### Post by xnicodemusx on 2010-05-24
Fixed my problem thnx [kansasnoob]("http://ubuntuforums.org/member.php?u=554595")

---

### Post by Whiterin on 2010-05-25
> **oldfred said:**
> to set boot flag - should only be on primary partitions:
You can use gparted, right click on partition & manage flags, disk utility, or command line:
set boot flag on for sda3 (off on others)
sudo sfdisk -A3 /dev/sda

This did nothing for me.

---

### Post by oldfred on 2010-05-25
Now grub should see the correct windows partition and the windows repair disk should see the correct partition to repair.

---

### Post by Whiterin on 2010-05-25
> **oldfred said:**
> Now grub should see the correct windows partition and the windows repair disk should see the correct partition to repair.

It doesn't, I am still getting an error.
[IMG]http://img34.imageshack.us/img34/1232/imag0133j.jpg[/IMG]

---

