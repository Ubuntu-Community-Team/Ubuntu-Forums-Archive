---
title: "grub small issue"
date: 2011-08-19
forum: General Help
---

### Post by raja.genupula on 2011-08-19
```
assassin@genupulas:~$ sudo dpkg-reconfigure grub-pc
[sudo] password for assassin: 
Installation finished. No error reported.
[U][B]/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..[/B][/U]
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu oneiric (development branch) (11.10) on /dev/sda6
Found Ubuntu 11.04 (11.04) on /dev/sda8
done
```
  
i am thinking about those marked lines 
please can any one help me to solve this

---

### Post by raja.genupula on 2011-08-20
please any one , give me a reason for that warning

---

### Post by oldfred on 2011-08-20
When you ran that it gave you a combo box like the manual install combo box listing all drives. But it also shows all partitions. Unless you have another boot loader you should only install to drives (sda, sdb etc) not to partitions (sda1, sda2, sdb1 etc).

---

### Post by raja.genupula on 2011-08-21
is this ignore or a serious issue ?

---

### Post by YesWeCan on 2011-08-21
Grub will work ok at first but will stop working at some point in the future.

---

### Post by raja.genupula on 2011-08-21
oh ! 
how can i clear this before the problem rise  ? 

THANKS IN ADVANCE .

---

### Post by YesWeCan on 2011-08-21
The whole thing is confusing and the error messages are pants. :)

Run dpkg-reconfigure grub-pc again. This time do as oldfred said and select a drive rather than a partition.
sdx with no number means the drive. sdxn means partition n of drive sdx.

Unfortunately, grub is limited in this way.

---

### Post by raja.genupula on 2011-08-21
> **YesWeCan said:**
> The whole thing is confusing and the error messages are pants. :)

Run dpkg-reconfigure grub-pc again. This time do as oldfred said and select a drive rather than a partition.
sdx with no number means the drive. sdxn means partition n of drive sdx.

Unfortunately, grub is limited in this way.

Hey i am really glad for watching this . no errors . thank you very much @oldfred , @YesWeCan

look at this , this what i got , seems positive right 


```
assassin@genupulas:~$ sudo dpkg-reconfigure grub-pc
[sudo] password for assassin: 
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu oneiric (development branch) (11.10) on /dev/sda6
Found Ubuntu 11.04 (11.04) on /dev/sda8
done

```

---

### Post by raja.genupula on 2011-08-21
> **YesWeCan said:**
> 

Unfortunately, grub is limited in this way.

 everything went fine . but i didnt get this . could you please explain me .

---

### Post by oldfred on 2011-08-21
Old grub legacy has not been maintained for years and still boots may standard systems. But for example Ubuntu had to modify its version of grub legacy to work with ext4 when they converted to ext4 as a standard.

Grub2 had more code and loadable modules to accommodate many newer systems and configurations. Since it is larger the full code does not fit into a partition like old grub legacy. It uses blocklists or hard coded addresses to find the rest of its code. If that code gets moved and an update or for any reason the the block list address is wrong and you have to reinstall grub to the partition. 

If you have multiple installs or multiple drives you should for your own documentation run this script. I rerun it as part of my backup even though things may not have changed, but partitically run it before & after any major system change.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by raja.genupula on 2011-08-21
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 4481367 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /boot/burg/burg.cfg /etc/fstab 
                       /boot/grub/core.img /boot/burg/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu oneiric (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   102,398,309   102,398,247  83 Linux
/dev/sda2         102,398,371   379,647,999   277,249,629   f W95 Extended (LBA)
/dev/sda5         102,398,373   216,109,775   113,711,403   7 NTFS / exFAT / HPFS
/dev/sda6         307,194,993   371,647,709    64,452,717  83 Linux
/dev/sda7         371,648,512   379,647,999     7,999,488  82 Linux swap / Solaris
/dev/sda8         216,111,104   307,193,855    91,082,752  83 Linux
/dev/sda3         379,648,080   577,761,659   198,113,580   7 NTFS / exFAT / HPFS
/dev/sda4         577,761,660   976,768,064   399,006,405   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        a97fc479-ab34-4b3e-97da-bea1b90a4588   ext4       
/dev/sda3        061F37EF05F98924                       ntfs       New Volume
/dev/sda4        4CED98D85382CF98                       ntfs       alls
/dev/sda5        2CC08081C080534E                       ntfs       softwares
/dev/sda6        05b5dced-7e03-4afd-a8ec-10fae28baad7   ext4       
/dev/sda7        77fe75eb-8f12-483e-8ed7-5f1f1356b3e0   swap       
/dev/sda8        c0175450-43d4-4fe7-a9e7-f19ffcbd3399   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda4        /media/alls              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-8-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 05b5dced-7e03-4afd-a8ec-10fae28baad7
	linux /boot/vmlinuz-3.0.0-8-generic root=UUID=05b5dced-7e03-4afd-a8ec-10fae28baad7 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-8-generic
}
menuentry "Ubuntu, with Linux 3.0.0-8-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 05b5dced-7e03-4afd-a8ec-10fae28baad7
	linux /boot/vmlinuz-3.0.0-8-generic root=UUID=05b5dced-7e03-4afd-a8ec-10fae28baad7 ro single nomodeset
	initrd /boot/initrd.img-3.0.0-8-generic
}
menuentry "Ubuntu, with Linux 3.0-3-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 05b5dced-7e03-4afd-a8ec-10fae28baad7
	linux /boot/vmlinuz-3.0-3-generic root=UUID=05b5dced-7e03-4afd-a8ec-10fae28baad7 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0-3-generic
}
menuentry "Ubuntu, with Linux 3.0-3-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 05b5dced-7e03-4afd-a8ec-10fae28baad7
	linux /boot/vmlinuz-3.0-3-generic root=UUID=05b5dced-7e03-4afd-a8ec-10fae28baad7 ro single nomodeset
	initrd /boot/initrd.img-3.0-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c0175450-43d4-4fe7-a9e7-f19ffcbd3399
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=c0175450-43d4-4fe7-a9e7-f19ffcbd3399 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c0175450-43d4-4fe7-a9e7-f19ffcbd3399
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=c0175450-43d4-4fe7-a9e7-f19ffcbd3399 ro single
	initrd /boot/initrd.img-2.6.38-8-generic
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

=========================== sda1/boot/burg/burg.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/burg-mkconfig using templates
# from /etc/burg.d and settings from /etc/default/burg
#

### BEGIN /etc/burg.d/00_header ###
set theme_name=ubuntu
set gfxmode=640x480
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
    save_env gfxmode
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set a97fc479-ab34-4b3e-97da-bea1b90a4588
set locale_dir=($root)/boot/burg/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/burg.d/00_header ###

### BEGIN /etc/burg.d/10_linux ###
menuentry 'Ubuntu GNU/Linux, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a97fc479-ab34-4b3e-97da-bea1b90a4588
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro  quiet splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu GNU/Linux, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a97fc479-ab34-4b3e-97da-bea1b90a4588
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
### menuentry 'Ubuntu GNU/Linux, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a97fc479-ab34-4b3e-97da-bea1b90a4588
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro  quiet splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### menuentry 'Ubuntu GNU/Linux, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os --group group_main {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a97fc479-ab34-4b3e-97da-bea1b90a4588
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
} 
### END /etc/burg.d/10_linux ###

### BEGIN /etc/burg.d/30_os-prober ###
### menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sda6)" --class ubuntu --class os --group group_/dev/sda6 {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 2c57b22d-c85c-4b41-8691-49d16ded61f1
	linux /boot/vmlinuz-2.6.35-28-generic root=/dev/sda6 ro quiet splash
}
### menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda6)" --class ubuntu --class os --group group_/dev/sda6 {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 2c57b22d-c85c-4b41-8691-49d16ded61f1
	linux /boot/vmlinuz-2.6.35-28-generic root=/dev/sda6 ro single
} 
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda6)" --class ubuntu --class os --group group_/dev/sda6 {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 2c57b22d-c85c-4b41-8691-49d16ded61f1
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=2c57b22d-c85c-4b41-8691-49d16ded61f1 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda6)" --class ubuntu --class os --group group_/dev/sda6 {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 2c57b22d-c85c-4b41-8691-49d16ded61f1
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=2c57b22d-c85c-4b41-8691-49d16ded61f1 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/burg.d/30_os-prober ###

### BEGIN /etc/burg.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/burg.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 /               ext4    errors=remount-ro 0       1
/dev/sda7       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/burg/burg.cfg                             1
               =                boot/burg/core.img                             1
               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-10-generic              2
               =                boot/initrd.img-2.6.38-11-generic              2
               =                boot/initrd.img-2.6.38-8-generic               2
               =                boot/vmlinuz-2.6.38-10-generic                 2
               =                boot/vmlinuz-2.6.38-11-generic                 2
               =                boot/vmlinuz-2.6.38-8-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        2
               =                vmlinuz.old                                    2

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             initrd.img-2.6.35-22-generic                   2
            ?? = ??             initrd.lz                                      1

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 05b5dced-7e03-4afd-a8ec-10fae28baad7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(/dev/sda,msdos6)'
  search --no-floppy --fs-uuid --set=root 05b5dced-7e03-4afd-a8ec-10fae28baad7
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IN
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
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
menuentry 'Ubuntu, with Linux 3.0.0-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 05b5dced-7e03-4afd-a8ec-10fae28baad7
	linux	/boot/vmlinuz-3.0.0-8-generic root=UUID=05b5dced-7e03-4afd-a8ec-10fae28baad7 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-8-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 05b5dced-7e03-4afd-a8ec-10fae28baad7
	echo	'Loading Linux 3.0.0-8-generic ...'
	linux	/boot/vmlinuz-3.0.0-8-generic root=UUID=05b5dced-7e03-4afd-a8ec-10fae28baad7 ro single nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0-3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 05b5dced-7e03-4afd-a8ec-10fae28baad7
	linux	/boot/vmlinuz-3.0-3-generic root=UUID=05b5dced-7e03-4afd-a8ec-10fae28baad7 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0-3-generic
}
menuentry 'Ubuntu, with Linux 3.0-3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 05b5dced-7e03-4afd-a8ec-10fae28baad7
	echo	'Loading Linux 3.0-3-generic ...'
	linux	/boot/vmlinuz-3.0-3-generic root=UUID=05b5dced-7e03-4afd-a8ec-10fae28baad7 ro single nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0-3-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 05b5dced-7e03-4afd-a8ec-10fae28baad7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 05b5dced-7e03-4afd-a8ec-10fae28baad7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-11-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
	linux /boot/vmlinuz-2.6.38-11-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro single
	initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro single
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro single
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c0175450-43d4-4fe7-a9e7-f19ffcbd3399
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=c0175450-43d4-4fe7-a9e7-f19ffcbd3399 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c0175450-43d4-4fe7-a9e7-f19ffcbd3399
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=c0175450-43d4-4fe7-a9e7-f19ffcbd3399 ro single
	initrd /boot/initrd.img-2.6.38-8-generic
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=05b5dced-7e03-4afd-a8ec-10fae28baad7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=77fe75eb-8f12-483e-8ed7-5f1f1356b3e0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-8-generic                2
               =                boot/initrd.img-3.0-3-generic                  2
               =                boot/vmlinuz-3.0.0-8-generic                   1
               =                boot/vmlinuz-3.0-3-generic                     1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root c0175450-43d4-4fe7-a9e7-f19ffcbd3399
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos8)'
search --no-floppy --fs-uuid --set=root c0175450-43d4-4fe7-a9e7-f19ffcbd3399
set locale_dir=($root)/boot/grub/locale
set lang=en_IN
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c0175450-43d4-4fe7-a9e7-f19ffcbd3399
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=c0175450-43d4-4fe7-a9e7-f19ffcbd3399 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c0175450-43d4-4fe7-a9e7-f19ffcbd3399
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=c0175450-43d4-4fe7-a9e7-f19ffcbd3399 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c0175450-43d4-4fe7-a9e7-f19ffcbd3399
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos8)'
	search --no-floppy --fs-uuid --set=root c0175450-43d4-4fe7-a9e7-f19ffcbd3399
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-10-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
	linux /boot/vmlinuz-2.6.38-10-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro single
	initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root a97fc479-ab34-4b3e-97da-bea1b90a4588
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=a97fc479-ab34-4b3e-97da-bea1b90a4588 ro single
	initrd /boot/initrd.img-2.6.38-8-generic
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

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=c0175450-43d4-4fe7-a9e7-f19ffcbd3399 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=77fe75eb-8f12-483e-8ed7-5f1f1356b3e0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-8-generic               2
               =                boot/vmlinuz-2.6.38-8-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

---

### Post by YesWeCan on 2011-08-21
> **raja.genupula said:**
> everything went fine . but i didnt get this . could you please explain me .
Grub will not function reliably when installed to a partition (except when installed to a bios-grub partition on a GPT formatted disk).

---

### Post by raja.genupula on 2011-08-23
now everything looking good & i do remember what you said. really many many thanks to 
@oldfred , @Yeswecan

---

