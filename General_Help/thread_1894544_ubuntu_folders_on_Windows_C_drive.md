---
title: "ubuntu folders on Windows C: drive"
date: 2011-12-12
forum: General Help
---

### Post by yoramdavid on 2011-12-12
Hello all,

There is a folder called "boot" with burg inside and other folders and some other folders I do knot know what they are, does Ubuntu creates files on the C: drive? What for?

I have a boot partition on the first sector for  /boot

Thank you.

Yoram

---

### Post by grahammechanical on 2011-12-12
What install method did you use to install Ubuntu? If you used Wubi to install Ubuntu inside Windows then the answer is Yes. In the case of a Wubi install all the Ubuntu files would be on the C: drive.

Please provide a screenshot so we can see what you can see.

Regards.

---

### Post by yoramdavid on 2011-12-12
> **grahammechanical said:**
> What install method did you use to install Ubuntu? If you used Wubi to install Ubuntu inside Windows then the answer is Yes. In the case of a Wubi install all the Ubuntu files would be on the C: drive.

Please provide a screenshot so we can see what you can see.

Regards.

Thank you grahammechanical,

No, I have installed Ubuntu as a standalone OS on the / partition with a /boot for the boot.

Partition 1: /boot
Partition 2: /
Partition 3, 4 & 5: Windows XP + 2 other NTFS
Partition 6: /Swap

Please see image below:
[[IMG]http://img210.imageshack.us/img210/577/windowspartition.jpg[/IMG]](http://imageshack.us/photo/my-images/210/windowspartition.jpg/)

The 5 first folder I do not know what or why they are there. Can I safely remove them? I am afraid if I do so, I will not be able to boot into linux anymore.

Thank you.

---

### Post by oldtimer7777 on 2011-12-12
If you delete those folders you may not be able to boot into Windows anymore.

> **yoramdavid said:**
> Thank you grahammechanical,

No, I have installed Ubuntu as a standalone OS on the / partition with a /boot for the boot.

Partition 1: /boot
Partition 2: /
Partition 3, 4 & 5: Windows XP + 2 other NTFS
Partition 6: /Swap

Please see image below:
[[IMG]http://img210.imageshack.us/img210/577/windowspartition.jpg[/IMG]]("http://imageshack.us/photo/my-images/210/windowspartition.jpg/")

The 5 first folder I do not know what or why they are there. Can I safely remove them? I am afraid if I do so, I will not be able to boot into linux anymore.

Thank you.

---

### Post by oldfred on 2011-12-12
The folder clean is usually from running boot-repair which backs up some info and temporarily stores some other data.

Two look like UUIDs and /boot is used by both grub and Windows 7 but not XP. Not sure about first folder.

What is in these folders? It does not look like a lot of items, but may be another folder with lots of data. 

You can always back up these folders and rename & then see if you have issues. Then if no issues, you can delete. If later you do find something you have a backup to restore.

---

### Post by yoramdavid on 2011-12-13
> **oldtimer7777 said:**
> If you delete those folders you may not be able to boot into Windows anymore.

thank you oldtimer7777,

I wonder if I have not deleted something by mistake as I am getting a blue screen of death when trying to boot into windows...

---

### Post by oldtimer7777 on 2011-12-13
> **yoramdavid said:**
> thank you oldtimer7777,

I wonder if I have not deleted something by mistake as I am getting a blue screen of death when trying to boot into windows...

That sounds right. :)

---

### Post by yoramdavid on 2011-12-13
> **oldfred said:**
> The folder clean is usually from running boot-repair which backs up some info and temporarily stores some other data.

Two look like UUIDs and /boot is used by both grub and Windows 7 but not XP. Not sure about first folder.

What is in these folders? It does not look like a lot of items, but may be another folder with lots of data. 

You can always back up these folders and rename & then see if you have issues. Then if no issues, you can delete. If later you do find something you have a backup to restore.

thank you oldfred,

Yes, I had to do a boot repair once.
Another image with the folder expanded might help.
This UUIDs is from linux, right?

What if i cannot get into ubuntu after i rename them? How would I restore them then?

[IMG]http://imageshack.us/f/593/windowspartitionexpande.jpg/[/IMG]

Yoram

---

### Post by mastablasta on 2011-12-13
> **yoramdavid said:**
> thank you oldfred,
 
Yes, I had to do a boot repair once.
Another image with the folder expanded might help.
This UUIDs is from linux, right?
 
What if i cannot get into ubuntu after i rename them? How would I restore them then?
 
[IMG]http://imageshack.us/f/593/windowspartitionexpande.jpg/[/IMG]
 
Yoram
 
 
you can boot Ubuntu live and then access the disk.
 
also why did you create /boot partition?

---

### Post by oldfred on 2011-12-13
Sometimes installing grub to a partition creates the /boot which also has /boot/grub folders.

If you installed grub2's boot loader to the PBR (partition boot sector) of the Windows partition, that destroys windows boot (before blue screen I think) as all NTFS partitions have to have a NTFS signature not grub in the PBR. You can repair that with fixboot and chkdsk normally from a XP repair console.

Not sure how a UUID entry becomes a folder unless you are using some Windows tools to mount it like Linux mounts?? Or did something just copy some data and use that as the name.

---

### Post by zero2xiii on 2011-12-13
+1 ^^

If you install grub to the MBR, then you will have that /boot folder in the windows drive.. 

Why delete random folders? Dont just go like "ah dont think I need this <delete>" If you need the space, get a bigger drive, or delete some unecesary clutter such as temp folders, web cache or even old files you can burn to CD or DVD and clear a few Gig that way.

Happy deleting :)
Cherz

EDIT:

Those "UUID" folders might be residual install file folders. Most (esp online installers) create those type of name folders to store temp install files in, but they cant delete it, since in most cases it IS the installer and requierd files that is in it. So it just stays there. But again, dont delete it, I might be wrong.

---

### Post by yoramdavid on 2011-12-13
> **mastablasta said:**
> you can boot Ubuntu live and then access the disk.
 
also why did you create /boot partition?

Thank you mastablasta

I read somewhere that creating a partition dedicated for Grub2 / BURG (I use BURG) was more relicable / stable, is that no so?

---

### Post by yoramdavid on 2011-12-13
> **oldfred said:**
> Sometimes installing grub to a partition creates the /boot which also has /boot/grub folders.

If you installed grub2's boot loader to the PBR (partition boot sector) of the Windows partition, that destroys windows boot (before blue screen I think) as all NTFS partitions have to have a NTFS signature not grub in the PBR. You can repair that with fixboot and chkdsk normally from a XP repair console.

Not sure how a UUID entry becomes a folder unless you are using some Windows tools to mount it like Linux mounts?? Or did something just copy some data and use that as the name.

Thank you oldfred,

I have installed Grub2 then later BURG on that /boot partition. I have been using this dual boot for years without problems.
I never mounted the Ubuntu partition from windows on this computer.

Do I need the Windows XP CD to do that fixboot or can I do that with a uSB pen-drive or from within Ubuntu?

---

### Post by yoramdavid on 2011-12-13
> **zero2xiii said:**
> +1 ^^

If you install grub to the MBR, then you will have that /boot folder in the windows drive.. 

Why delete random folders? Dont just go like "ah dont think I need this <delete>" If you need the space, get a bigger drive, or delete some unecesary clutter such as temp folders, web cache or even old files you can burn to CD or DVD and clear a few Gig that way.

Happy deleting :)
Cherz

EDIT:

Those "UUID" folders might be residual install file folders. Most (esp online installers) create those type of name folders to store temp install files in, but they cant delete it, since in most cases it IS the installer and requierd files that is in it. So it just stays there. But again, dont delete it, I might be wrong.

Thank you zero2xiii,

Well, since the blue screen of death I am worriyng about Ubuntu placing files on the C: drive.
I would prefer Ubunto to leave the C: drive untouched.

---

### Post by oldfred on 2011-12-13
To see how you are booting post this or run boot-repair and post link as it also can run this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk

---

### Post by yoramdavid on 2011-12-13
> **oldfred said:**
> To see how you are booting post this or run boot-repair and post link as it also can run this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Install these before running script:
sudo apt-get install gawk

Thank you once more, oldfred, here are the results:

Why is the partition "/boot/ called dev/sda4 and not dev/sda1, it that one is at the beginning of the hard drive?
Windows XP is on dev/sda1

Ubuntu is on an extended partition, would in not be better (if possible) to be on a second active partition?

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 4 for /burg.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /boot/burg/burg.cfg /etc/fstab 
                       /boot/grub/core.img /boot/burg/core.img

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 68. But according to the info from fdisk, 
                       sda6 starts at sector 67665848.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /burg/burg.cfg /grub/core.img 
                       /burg/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *        417,693    46,877,669    46,459,977   7 NTFS / exFAT / HPFS
/dev/sda2          46,877,731   223,303,499   176,425,769   5 Extended
/dev/sda5          46,877,733    67,665,779    20,788,047  83 Linux
/dev/sda6          67,665,848   220,733,099   153,067,252   7 NTFS / exFAT / HPFS
/dev/sda7         220,733,163   223,303,499     2,570,337  82 Linux swap / Solaris
/dev/sda3         223,313,920   234,432,511    11,118,592   7 NTFS / exFAT / HPFS
/dev/sda4               2,048       415,743       413,696  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        B6C4C919C4C8DD2D                       ntfs       Windows XP
/dev/sda3        F0A6C30EA6C2D3EE                       ntfs       Trabalhando
/dev/sda4        9817e6cc-396e-480c-a86f-5e043f29a7ea   ext4       
/dev/sda5        2261122c-7b08-4e5b-ba83-161c4f949e27   ext4       
/dev/sda6        01C7F0DDE3954E00                       ntfs       Documentos
/dev/sda7        7ea31e8d-711d-4f06-8558-d5cf1e20a9ea   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /media/Trabalhando       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4        /boot                    ext4       (rw,commit=0)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /media/Documentos        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=AVKIML noguiboot
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=AVKIML-BAK
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/stage2                               0

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 2261122c-7b08-4e5b-ba83-161c4f949e27
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos4)'
  search --no-floppy --fs-uuid --set=root 9817e6cc-396e-480c-a86f-5e043f29a7ea
  set locale_dir=($root)/grub/locale
  set lang=pt_PT
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 2261122c-7b08-4e5b-ba83-161c4f949e27
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 0,71,115; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, com Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 9817e6cc-396e-480c-a86f-5e043f29a7ea
	linux	/vmlinuz-3.0.0-14-generic root=UUID=2261122c-7b08-4e5b-ba83-161c4f949e27 ro   vesafb.invalid=1
	initrd	/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, com Linux 3.0.0-14-generic (modo de recuperação)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 9817e6cc-396e-480c-a86f-5e043f29a7ea
	echo	'A carregar Linux 3.0.0-14-generic ...'
	linux	/vmlinuz-3.0.0-14-generic root=UUID=2261122c-7b08-4e5b-ba83-161c4f949e27 ro recovery nomodeset 
	echo	'A carregar ramdisk inicial ...'
	initrd	/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, com Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 9817e6cc-396e-480c-a86f-5e043f29a7ea
	linux	/vmlinuz-3.0.0-13-generic root=UUID=2261122c-7b08-4e5b-ba83-161c4f949e27 ro   vesafb.invalid=1
	initrd	/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, com Linux 3.0.0-13-generic (modo de recuperação)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 9817e6cc-396e-480c-a86f-5e043f29a7ea
	echo	'A carregar Linux 3.0.0-13-generic ...'
	linux	/vmlinuz-3.0.0-13-generic root=UUID=2261122c-7b08-4e5b-ba83-161c4f949e27 ro recovery nomodeset 
	echo	'A carregar ramdisk inicial ...'
	initrd	/initrd.img-3.0.0-13-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 9817e6cc-396e-480c-a86f-5e043f29a7ea
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 9817e6cc-396e-480c-a86f-5e043f29a7ea
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root B6C4C919C4C8DD2D
	drivemap -s (hd0) ${root}
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
--------------------------------------------------------------------------------

=========================== sda5/boot/burg/burg.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/burg-mkconfig using templates
# from /etc/burg.d and settings from /etc/default/burg
#

### BEGIN /etc/burg.d/00_header ###
set theme_name=ubuntu
if [ -s $prefix/burgenv ]; then
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
set gfxmode=1280x1024
function select_menu {
  if menu_popup -t template_popup theme_menu ; then
    free_config template_popup template_subitem menu class screen
    load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
    save_env theme_name
    menu_refresh
  fi
}
function toggle_fold {
  if test -z $theme_fold ; then
    set theme_fold=1
  else
    set theme_fold=
  fi
  save_env theme_fold
  menu_refresh
}
function select_resolution {
  if menu_popup -t template_popup resolution_menu ; then
    menu_reload_mode
  fi
}
if test -f ${prefix}/themes/${theme_name}/theme ; then
  insmod coreui
  menu_region.text
  load_string '+theme_menu { -arabic_and_freedom { command="set theme_name=arabic_and_freedom" }}'
  load_string '+theme_menu { -black_and_white { command="set theme_name=black_and_white" }}'
  load_string '+theme_menu { -burg { command="set theme_name=burg" }}'
  load_string '+theme_menu { -chiva { command="set theme_name=chiva" }}'
  load_string '+theme_menu { -coffee { command="set theme_name=coffee" }}'
  load_string '+theme_menu { -minimum { command="set theme_name=minimum" }}'
  load_string '+theme_menu { -proto { command="set theme_name=proto" }}'
  load_string '+theme_menu { -radiance { command="set theme_name=radiance" }}'
  load_string '+theme_menu { -radiancetext { command="set theme_name=radiancetext" }}'
  load_string '+theme_menu { -refit { command="set theme_name=refit" }}'
  load_string '+theme_menu { -sora { command="set theme_name=sora" }}'
  load_string '+theme_menu { -sora_clean { command="set theme_name=sora_clean" }}'
  load_string '+theme_menu { -sora_extended { command="set theme_name=sora_extended" }}'
  load_string '+theme_menu { -sunset { command="set theme_name=sunset" }}'
  load_string '+theme_menu { -ubuntu { command="set theme_name=ubuntu" }}'
  load_string '+theme_menu { -ubuntu2 { command="set theme_name=ubuntu2" }}'
  load_string '+theme_menu { -winter { command="set theme_name=winter" }}'
  load_config ${prefix}/themes/conf.d/10_hotkey
  load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
  insmod vbe
  insmod png
  insmod jpeg
  set gfxfont="Unifont Regular 16"
  menu_region.gfx
  vmenu resolution_menu
  controller.ext
fi
insmod ext2
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 9817e6cc-396e-480c-a86f-5e043f29a7ea
set locale_dir=($root)/burg/locale
set lang=pt
insmod gettext
set timeout=5
### END /etc/burg.d/00_header ###

### BEGIN /etc/burg.d/10_linux ###
menuentry 'Ubuntu 11-10 Oneiric Ocelot 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 9817e6cc-396e-480c-a86f-5e043f29a7ea
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/vmlinuz-3.0.0-13-generic root=UUID=2261122c-7b08-4e5b-ba83-161c4f949e27 ro  quiet splash
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.0.0-13-generic
}
### BEGIN /etc/burg.d/30_os-prober (on /dev/sda1)###
menuentry "Windows XP Professional SP3 " --class windows --class os {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b6c4c919c4c8dd2d
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry '                                   ' --class macosx {
	initrd
}
### END /etc/burg.d/30_os-prober ###
menuentry 'Ubuntu 11-10 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 9817e6cc-396e-480c-a86f-5e043f29a7ea
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/vmlinuz-3.0.0-13-generic root=UUID=2261122c-7b08-4e5b-ba83-161c4f949e27 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.0.0-13-generic
}
menuentry "Memory test (memtest86+)" --class linux  {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 0c5bbd96-222d-445f-8bc6-0e5ad821484b
	linux16	/memtest86+.bin
}
### END /etc/burg.d/10_linux ###

### BEGIN /etc/burg.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/burg.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc                proc     nodev,noexec,nosuid                                                           0  0  
#Entry for /dev/sda5 :
UUID=2261122c-7b08-4e5b-ba83-161c4f949e27  /                    ext4     errors=remount-ro                                                             0  1  
#Entry for /dev/sda4 :
UUID=9817e6cc-396e-480c-a86f-5e043f29a7ea  /boot                ext4     defaults                                                                      0  2  
#Entry for /dev/sda6 :
UUID=01C7F0DDE3954E00                      /media/Documentos    ntfs-3g  defaults,locale=pt_PT.UTF-8,windows_names,hide_hid_files                      0  0  
#Entry for /dev/sda3 :
UUID=F0A6C30EA6C2D3EE                      /media/Trabalhando   ntfs-3g  defaults,locale=pt_PT.UTF-8,windows_names,hide_hid_files                      0  0  
#Entry for /dev/sda1 :
#Entry for /dev/sda7 :
UUID=7ea31e8d-711d-4f06-8558-d5cf1e20a9ea  none                 swap     sw                                                                            0  0  
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  22.367699146 = 24.017134080   boot/burg/burg.cfg                             1
  22.361215115 = 24.010171904   boot/burg/core.img                             1
  22.361523151 = 24.010502656   boot/grub/core.img                             1
  22.368189335 = 24.017660416   boot/grub/grub.cfg                             1
  22.508036137 = 24.167819776   boot/initrd.img-3.0.0-13-generic               3
  22.455311298 = 24.111206912   boot/initrd.img-3.0.0-14-generic               4
  22.431605816 = 24.085753344   boot/vmlinuz-3.0.0-13-generic                  1
  22.386683941 = 24.037518848   boot/vmlinuz-3.0.0-14-generic                  3
  22.455311298 = 24.111206912   initrd.img                                     4
  22.508036137 = 24.167819776   initrd.img.old                                 3
  22.386683941 = 24.037518848   vmlinuz                                        3
  22.431605816 = 24.085753344   vmlinuz.old                                    1

============================= sda4/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
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

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 2261122c-7b08-4e5b-ba83-161c4f949e27
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos4)'
  search --no-floppy --fs-uuid --set=root 9817e6cc-396e-480c-a86f-5e043f29a7ea
  set locale_dir=($root)/grub/locale
  set lang=pt_PT
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 2261122c-7b08-4e5b-ba83-161c4f949e27
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 0,71,115; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, com Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 9817e6cc-396e-480c-a86f-5e043f29a7ea
	linux	/vmlinuz-3.0.0-14-generic root=UUID=2261122c-7b08-4e5b-ba83-161c4f949e27 ro   vesafb.invalid=1
	initrd	/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, com Linux 3.0.0-14-generic (modo de recuperação)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 9817e6cc-396e-480c-a86f-5e043f29a7ea
	echo	'A carregar Linux 3.0.0-14-generic ...'
	linux	/vmlinuz-3.0.0-14-generic root=UUID=2261122c-7b08-4e5b-ba83-161c4f949e27 ro recovery nomodeset 
	echo	'A carregar ramdisk inicial ...'
	initrd	/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, com Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 9817e6cc-396e-480c-a86f-5e043f29a7ea
	linux	/vmlinuz-3.0.0-13-generic root=UUID=2261122c-7b08-4e5b-ba83-161c4f949e27 ro   vesafb.invalid=1
	initrd	/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, com Linux 3.0.0-13-generic (modo de recuperação)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 9817e6cc-396e-480c-a86f-5e043f29a7ea
	echo	'A carregar Linux 3.0.0-13-generic ...'
	linux	/vmlinuz-3.0.0-13-generic root=UUID=2261122c-7b08-4e5b-ba83-161c4f949e27 ro recovery nomodeset 
	echo	'A carregar ramdisk inicial ...'
	initrd	/initrd.img-3.0.0-13-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 9817e6cc-396e-480c-a86f-5e043f29a7ea
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root 9817e6cc-396e-480c-a86f-5e043f29a7ea
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root B6C4C919C4C8DD2D
	drivemap -s (hd0) ${root}
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
--------------------------------------------------------------------------------

============================= sda4/burg/burg.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/burg-mkconfig using templates
# from /etc/burg.d and settings from /etc/default/burg
#

### BEGIN /etc/burg.d/00_header ###
set theme_name=ubuntu
if [ -s $prefix/burgenv ]; then
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
set gfxmode=1280x1024
function select_menu {
  if menu_popup -t template_popup theme_menu ; then
    free_config template_popup template_subitem menu class screen
    load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
    save_env theme_name
    menu_refresh
  fi
}
function toggle_fold {
  if test -z $theme_fold ; then
    set theme_fold=1
  else
    set theme_fold=
  fi
  save_env theme_fold
  menu_refresh
}
function select_resolution {
  if menu_popup -t template_popup resolution_menu ; then
    menu_reload_mode
  fi
}
if test -f ${prefix}/themes/${theme_name}/theme ; then
  insmod coreui
  menu_region.text
  load_string '+theme_menu { -arabic_and_freedom { command="set theme_name=arabic_and_freedom" }}'
  load_string '+theme_menu { -black_and_white { command="set theme_name=black_and_white" }}'
  load_string '+theme_menu { -burg { command="set theme_name=burg" }}'
  load_string '+theme_menu { -chiva { command="set theme_name=chiva" }}'
  load_string '+theme_menu { -coffee { command="set theme_name=coffee" }}'
  load_string '+theme_menu { -minimum { command="set theme_name=minimum" }}'
  load_string '+theme_menu { -proto { command="set theme_name=proto" }}'
  load_string '+theme_menu { -radiance { command="set theme_name=radiance" }}'
  load_string '+theme_menu { -radiancetext { command="set theme_name=radiancetext" }}'
  load_string '+theme_menu { -refit { command="set theme_name=refit" }}'
  load_string '+theme_menu { -sora { command="set theme_name=sora" }}'
  load_string '+theme_menu { -sora_clean { command="set theme_name=sora_clean" }}'
  load_string '+theme_menu { -sora_extended { command="set theme_name=sora_extended" }}'
  load_string '+theme_menu { -sunset { command="set theme_name=sunset" }}'
  load_string '+theme_menu { -ubuntu { command="set theme_name=ubuntu" }}'
  load_string '+theme_menu { -ubuntu2 { command="set theme_name=ubuntu2" }}'
  load_string '+theme_menu { -winter { command="set theme_name=winter" }}'
  load_config ${prefix}/themes/conf.d/10_hotkey
  load_config ${prefix}/themes/${theme_name}/theme ${prefix}/themes/custom/theme_${theme_name}
  insmod vbe
  insmod png
  insmod jpeg
  set gfxfont="Unifont Regular 16"
  menu_region.gfx
  vmenu resolution_menu
  controller.ext
fi
insmod ext2
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 9817e6cc-396e-480c-a86f-5e043f29a7ea
set locale_dir=($root)/burg/locale
set lang=pt
insmod gettext
set timeout=5
### END /etc/burg.d/00_header ###

### BEGIN /etc/burg.d/10_linux ###
menuentry 'Ubuntu 11-10 Oneiric Ocelot 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 9817e6cc-396e-480c-a86f-5e043f29a7ea
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/vmlinuz-3.0.0-13-generic root=UUID=2261122c-7b08-4e5b-ba83-161c4f949e27 ro  quiet splash
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.0.0-13-generic
}
### BEGIN /etc/burg.d/30_os-prober (on /dev/sda1)###
menuentry "Windows XP Professional SP3 " --class windows --class os {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b6c4c919c4c8dd2d
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry '                                   ' --class macosx {
	initrd
}
### END /etc/burg.d/30_os-prober ###
menuentry 'Ubuntu 11-10 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 9817e6cc-396e-480c-a86f-5e043f29a7ea
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/vmlinuz-3.0.0-13-generic root=UUID=2261122c-7b08-4e5b-ba83-161c4f949e27 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.0.0-13-generic
}
menuentry "Memory test (memtest86+)" --class linux  {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 0c5bbd96-222d-445f-8bc6-0e5ad821484b
	linux16	/memtest86+.bin
}
### END /etc/burg.d/10_linux ###

### BEGIN /etc/burg.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/burg.d/40_custom ###
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.015630722 = 0.016783360    burg/burg.cfg                                  1
   0.009146690 = 0.009821184    burg/core.img                                  1
   0.009454727 = 0.010151936    grub/core.img                                  1
   0.016120911 = 0.017309696    grub/grub.cfg                                  1
   0.155967712 = 0.167469056    initrd.img-3.0.0-13-generic                    3
   0.103242874 = 0.110856192    initrd.img-3.0.0-14-generic                    4
   0.079537392 = 0.085402624    vmlinuz-3.0.0-13-generic                       1
   0.034615517 = 0.037168128    vmlinuz-3.0.0-14-generic                       3

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  60 61 dd 87 72 73 83 57  2f 5c af 19 67 8f bb 75  |`a..rs.W/\..g..u|
00000010  e8 e8 ec 4b 1e 17 02 36  97 36 be b5 1c 3c ce e6  |...K...6.6...<..|
00000020  5e aa b6 ec 6a 3f 9b cf  87 a7 3a ac e4 c5 30 da  |^...j?....:...0.|
00000030  b5 ab 6e aa 7c e9 5a 98  a3 d5 eb f0 bc d3 1b 2b  |..n.|.Z........+|
00000040  2b 2b a3 42 b5 12 fb 5c  68 73 25 cf 38 e3 f3 ca  |++.B...\hs%.8...|
00000050  a0 c7 e7 44 06 29 c6 c3  4c fa ae fd 94 c4 98 7c  |...D.)..L......||
00000060  b5 db f3 cf 47 ee 74 32  97 b0 a2 63 b6 b3 b4 8b  |....G.t2...c....|
00000070  87 6e 38 bd 6c 68 73 5d  f2 4e 4e ee 9d b1 c2 0b  |.n8.lhs].NN.....|
00000080  47 a4 e9 3b 87 ea db 8c  55 d4 e4 f5 3d b6 a8 2e  |G..;....U...=...|
00000090  bf e1 c5 ce b8 24 ff 13  4b a7 96 d9 fe 31 b6 7c  |.....$..K....1.||
000000a0  c1 d2 eb 8f d3 07 db 86  86 af bc b9 ed 61 1a 80  |.............a..|
000000b0  3b 3d 78 4e 5e b3 62 b2  cd 68 7b c7 19 fe 9f 0f  |;=xN^.b..h{.....|
000000c0  c7 cc 77 ce ca 58 93 d3  b4 e0 62 d5 8c b0 90 07  |..w..X....b.....|
000000d0  1f 32 1e 9c 49 d9 50 70  e2 8b cf 56 eb 57 05 6f  |.2..I.Pp...V.W.o|
000000e0  06 5c 73 72 4c 38 70 78  fe ec 3d af c7 9f af 66  |.\srL8px..=....f|
000000f0  2f 1a 6b 59 fc aa cc 69  64 d3 fb a2 33 c7 43 fc  |/.kY...id...3.C.|
00000100  56 b7 ff ec c6 6c b7 81  91 f6 e8 46 f4 b7 45 f5  |V....l.....F..E.|
00000110  e7 0f 75 5c 54 b0 c5 ff  95 77 dc e8 1b 37 6e fd  |..u\T....w...7n.|
00000120  76 b5 c7 fa 49 cb 18 f9  9b 8f 8c 3e ae e7 ee e1  |v...I......>....|
00000130  1a f2 f5 93 d1 a6 7b f7  6c e2 a7 ed ed 13 d0 be  |......{.l.......|
00000140  70 f7 f4 49 86 49 57 7d  ec 5e ec 36 ee 76 3b 70  |p..I.IW}.^.6.v;p|
00000150  cc 63 87 27 cf 36 38 d4  8d 2a f4 5f fc 8b d3 08  |.c.'.68..*._....|
00000160  de 63 f9 8b 51 fc cd d9  c6 5f d6 dd af 7f 90 1d  |.c..Q...._......|
00000170  b1 79 66 f0 9c 4b 8b aa  57 1a 6f 30 d8 3f 88 69  |.yf..K..W.o0.?.i|
00000180  bc ae d6 74 92 c7 a0 2d  cf 5f 37 3b 35 98 f7 0e  |...t...-._7;5...|
00000190  8a 08 2f e8 18 9f ac ff  cb b3 2f cd 84 f9 97 23  |../......./....#|
000001a0  f9 f5 bb 1b 8f e2 51 cf  bb 67 d7 de 31 0f 11 3c  |......Q..g..1..<|
000001b0  f4 7c 6b 5a 79 81 21 49  1d ae fd f9 86 de 00 01  |.|kZy.!I........|
000001c0  c1 ff 83 fe ff ff 02 00  00 00 4f 33 3d 01 00 fe  |..........O3=...|
000001d0  ff ff 05 fe ff ff 51 33  3d 01 38 9f 1f 09 00 00  |......Q3=.8.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




```

---

### Post by oldfred on 2011-12-13
You have a separate /boot partition in sda4 with both grub & burg. Your main install is in sda5. Windows XP is in sda1. 

The boot flag is only used by Windows boot loader to know which partition has the additional boot code in the PBR (partition boot sector) to continue to boot Windows. Grub finds the Windows boot files and chain loads to the PBR without knowing about the boot flag.

For most desktops a separate /boot partition is not necessary. Servers, RAID, LVM, some other formats for partitions may require a separate /boot but those are not common for desktops and average users.

I do not know about burg but understand it has not had much development lately.

If having boot issues you have to read the extra instructions on mounting both / (root) and /boot to reinstall grub2's boot loader to the MBR.

---

### Post by yoramdavid on 2011-12-14
> **oldfred said:**
> You have a separate /boot partition in sda4 with both grub & burg. Your main install is in sda5. Windows XP is in sda1. 

The boot flag is only used by Windows boot loader to know which partition has the additional boot code in the PBR (partition boot sector) to continue to boot Windows. Grub finds the Windows boot files and chain loads to the PBR without knowing about the boot flag.

For most desktops a separate /boot partition is not necessary. Servers, RAID, LVM, some other formats for partitions may require a separate /boot but those are not common for desktops and average users.

I do not know about burg but understand it has not had much development lately.

If having boot issues you have to read the extra instructions on mounting both / (root) and /boot to reinstall grub2's boot loader to the MBR.

Thanks you once more oldfred,

I have no problems booting into Ubuntu (it takes a long time and the system sometimes freezes up). BURG is working fine.
The problem is booting into windows where I get the blue screen of death.

---

### Post by oldfred on 2011-12-14
Then that is just Windows. Often the fixBoot & chkdsk from a XP disk will fix it.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

---

### Post by yoramdavid on 2011-12-14
> **oldfred said:**
> Then that is just Windows. Often the fixBoot & chkdsk from a XP disk will fix it.

Thank you once more oldfred, I will check all that. I am limited with internet downloads where I am now, so I probably will only do it later and find a USB pen-drive solution rather than a CD if it is possible.

Yoram

---

