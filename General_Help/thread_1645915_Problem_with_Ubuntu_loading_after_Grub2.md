---
title: "Problem with Ubuntu loading after Grub2"
date: 2010-12-15
forum: General Help
---

### Post by Axolotl9250 on 2010-12-15
Hi, hoping someone can help with this. I changed the grub2 on  my /dev/sda to Arch's version, instead of Ubuntu's, and now I keep  booting into the initramfs prompt whenever I try to use Ubuntu. The  automatic OS detection won't find it when I run the mkconfig command on  grub2's wiki, and I currently have the following in /etc/grub.d/40_custom:

```
enuentry "Ubuntu Linux" {
set root=(hd0,3)
linux /boot/vmlinuz-2.6.35-23-generic
initrd /boot/initrd.img-2.6.35-23-generic root=dev/sda3 ro quiet
}
```

Which according to my partition layout, and a  double check on gparted, is correct. Do I need to flag it as boot or  something else? I tried putting Ubuntu's grub2 back on with the live cd  but it kept saying /dev/ was busy.
Cheers,
Ben.

---

### Post by sikander3786 on 2010-12-15
Is there some good reason behind changing the Grub2 to Arch's version? And also behind the custom entry?

Linux doesn't need a boot flag to boot.

Boot a Live CD/USB and post the output of Bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would help us better understand your setup.

---

### Post by coffeecat on 2010-12-15
You have "root=dev/sda3 ro quiet" in the initrd line; it should be in the linux line, and you're missing a "splash". I don't know whether "root=dev/sda3" works in grub 2 or whether you need to use the UUID. Whatever, you might find it better to use a stanza like this, in the form of what is generated from autoconfgured entries:

```
menuentry "Ubuntu Linux" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set [COLOR=Red]UUID[/COLOR]
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=[COLOR=Red]UUID[/COLOR] ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
```Change [COLOR=Red]UUID[/COLOR] to the uuid of sda3.

**Edit:** I am assuming Arch's grub2 is very much like Ubuntu, but that may be an unwarranted assumption! Yes, post the output of the bootscript as suggested by sikander3786. Also, what exactly happened when you tried to reinstall grub2 from the Ubuntu CD?

---

### Post by Axolotl9250 on 2010-12-15
Tried your solution, sikander, but it didn't work. Used the bootinfoscript and I've attached the result. Note I used bootinstallscript before I tried using UUID in grub2.

---

### Post by Quackers on 2010-12-15
Your boot script output in code tags

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,070,079    39,070,017  83 Linux
/dev/sda2          39,070,141   207,034,367   167,964,227   5 Extended
/dev/sda5          39,070,143    97,659,134    58,588,992  83 Linux
/dev/sda6          97,659,198   136,729,214    39,070,017  83 Linux
/dev/sda7         136,729,278   148,440,599    11,711,322  82 Linux swap / Solaris
/dev/sda8         148,441,088   187,502,591    39,061,504  83 Linux
/dev/sda9         187,504,640   207,034,367    19,529,728  83 Linux
/dev/sda3         207,034,368   246,095,871    39,061,504  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        e36b1ead-81e6-455e-9984-e47fd9830050   ext4       Archroot                      
/dev/sda2: PTTYPE="dos" 
/dev/sda3        3d444118-b41d-45d0-aef2-eb8949d03f99   ext4                                     
/dev/sda5        0489b920-2618-4d1b-89b2-7ed952f36759   ext4       Archome                       
/dev/sda6        433b5d2b-e06e-4de6-872e-9e823f3be798   ext4       Archvar                       
/dev/sda7        c9ba4505-484f-40c4-b6a9-1442ba56982c   swap                                     
/dev/sda8        616cd520-3921-4e83-b7aa-bf0d51db0625   ext4                                     
/dev/sda9        7b7f5d4f-6d3f-45f8-99e2-8aba3edb80fc   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /sbin/grub-mkconfig using templates
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
set menu_color_normal=light-blue/black
set menu_color_highlight=light-cyan/blue

insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e36b1ead-81e6-455e-9984-e47fd9830050
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set e36b1ead-81e6-455e-9984-e47fd9830050
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Arch Linux, with Linux vmlinuz26" --class archlinux --class gnu-linux --class gnu --class os {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e36b1ead-81e6-455e-9984-e47fd9830050
	echo	Loading Linux vmlinuz26 ...
	linux	/boot/vmlinuz26 root=/dev/disk/by-uuid/e36b1ead-81e6-455e-9984-e47fd9830050 ro  quiet
	echo	Loading initial ramdisk ...
	initrd	/boot/kernel26.img
}
menuentry "Arch Linux, with Linux vmlinuz26 Fallback" --class archlinux --class gnu-linux --class gnu --class os {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e36b1ead-81e6-455e-9984-e47fd9830050
	echo	Loading Linux vmlinuz26 ...Loading Linux Fallback ...
	linux	/boot/vmlinuz26 root=/dev/disk/by-uuid/e36b1ead-81e6-455e-9984-e47fd9830050 ro  quiet
	echo	Loading initial ramdisk ...
	initrd	/boot/kernel26-fallback.img
}
menuentry "Arch Linux, with Linux vmlinuz26 Fallback (recovery mode)" --class archlinux --class gnu-linux --class gnu --class os {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set e36b1ead-81e6-455e-9984-e47fd9830050
	echo	Loading Linux vmlinuz26 ...Loading Linux Fallback ...
	linux	/boot/vmlinuz26 root=/dev/disk/by-uuid/e36b1ead-81e6-455e-9984-e47fd9830050 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/kernel26-fallback.img
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Ubuntu Linux" {
    insmod ext4
    set root=(hd0,3)
    linux /boot/vmlinuz-2.6.35-23-generic root=dev/sda3 ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
devpts                 /dev/pts      devpts    defaults            0      0
shm                    /dev/shm      tmpfs     nodev,nosuid        0      0

#/dev/cdrom             /media/cd   auto    ro,user,noauto,unhide   0      0
#/dev/dvd               /media/dvd  auto    ro,user,noauto,unhide   0      0
#/dev/fd0               /media/fl   auto    user,noauto             0      0

/dev/sda1 / ext4 defaults 0 1
/dev/sda5 /home ext4 defaults 0 1
/dev/sda6 /var ext4 defaults 0 1
/dev/sda7 swap swap defaults 0 0

=================== sda1: Location of files loaded by Grub: ===================


  10.8GB: boot/grub/core.img
   6.6GB: boot/grub/grub.cfg
  11.1GB: boot/grub/stage2
    .1GB: boot/kernel26-fallback.img
    .1GB: boot/kernel26.img
  10.9GB: boot/vmlinuz26

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 3d444118-b41d-45d0-aef2-eb8949d03f99
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 3d444118-b41d-45d0-aef2-eb8949d03f99
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 3d444118-b41d-45d0-aef2-eb8949d03f99
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=3d444118-b41d-45d0-aef2-eb8949d03f99 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 3d444118-b41d-45d0-aef2-eb8949d03f99
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=3d444118-b41d-45d0-aef2-eb8949d03f99 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 3d444118-b41d-45d0-aef2-eb8949d03f99
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3d444118-b41d-45d0-aef2-eb8949d03f99 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 3d444118-b41d-45d0-aef2-eb8949d03f99
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3d444118-b41d-45d0-aef2-eb8949d03f99 ro single 
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
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 3d444118-b41d-45d0-aef2-eb8949d03f99
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 3d444118-b41d-45d0-aef2-eb8949d03f99
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Arch Linux, with Linux vmlinuz26 (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e36b1ead-81e6-455e-9984-e47fd9830050
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/e36b1ead-81e6-455e-9984-e47fd9830050 ro quiet
	initrd /boot/kernel26.img
}
menuentry "Arch Linux, with Linux vmlinuz26 Fallback (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e36b1ead-81e6-455e-9984-e47fd9830050
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/e36b1ead-81e6-455e-9984-e47fd9830050 ro quiet
	initrd /boot/kernel26-fallback.img
}
menuentry "Arch Linux, with Linux vmlinuz26 Fallback (recovery mode) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set e36b1ead-81e6-455e-9984-e47fd9830050
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/e36b1ead-81e6-455e-9984-e47fd9830050 ro single
	initrd /boot/kernel26-fallback.img
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
UUID=3d444118-b41d-45d0-aef2-eb8949d03f99 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=616cd520-3921-4e83-b7aa-bf0d51db0625 /home           ext4    defaults        0       2
# /var was on /dev/sda9 during installation
UUID=7b7f5d4f-6d3f-45f8-99e2-8aba3edb80fc /var            ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=c9ba4505-484f-40c4-b6a9-1442ba56982c none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 121.2GB: boot/grub/core.img
 116.9GB: boot/grub/grub.cfg
 106.7GB: boot/initrd.img-2.6.35-22-generic
 106.8GB: boot/initrd.img-2.6.35-23-generic
 121.2GB: boot/vmlinuz-2.6.35-22-generic
 121.2GB: boot/vmlinuz-2.6.35-23-generic
 106.8GB: initrd.img
 106.7GB: initrd.img.old
 121.2GB: vmlinuz
 121.2GB: vmlinuz.old
```

---

### Post by sikander3786 on 2010-12-15
Did you simply try *update-grub* from Arch? It _should_ detect and add Ubuntu to Grub menu and you shouldn't need a custom entry for Ubuntu.

If there was no specific reason behind changing Grub to Arch instead of Ubuntu, you can re-install Grub for Ubuntu and see if it detects your Arch install.

As *coffeecat* suggested above, my Grub entry for Ubuntu looks the same. So your might be,

```
menuentry 'Ubuntu Linux' {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 3d444118-b41d-45d0-aef2-eb8949d03f99
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=3d444118-b41d-45d0-aef2-eb8949d03f99 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}

```

If you decide to re-install Grub for Ubuntu, from Ubuntu 9.10 or newer Live CD,

```
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```

---

### Post by oldfred on 2010-12-15
You have a mod of ext4 that should be ext2 and are missing a / before the /dev/sda3.

menuentry "Ubuntu Linux" {
    insmod ext[COLOR=Red]2[/COLOR]
    set root=(hd0,3)
    linux /boot/vmlinuz-2.6.35-23-generic root=[COLOR=Red]/[/COLOR]dev/sda3 ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}

But if you update Ubuntu with new kernels you have to edit the entry. This works to boot the most current kernel using the link files in root not /boot.

menuentry "Ubuntu on sda3" {
    set root=(hd0,3)
        linux /vmlinuz root=/dev/sda3 ro quiet splash
        initrd /initrd.img
}

---

### Post by Axolotl9250 on 2010-12-15
> **oldfred said:**
> You have a mod of ext4 that should be ext2 and are missing a / before the /dev/sda3.

menuentry "Ubuntu Linux" {
    insmod ext[COLOR=Red]2[/COLOR]
    set root=(hd0,3)
    linux /boot/vmlinuz-2.6.35-23-generic root=[COLOR=Red]/[/COLOR]dev/sda3 ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}

But if you update Ubuntu with new kernels you have to edit the entry. This works to boot the most current kernel using the link files in root not /boot.

menuentry "Ubuntu on sda3" {
    set root=(hd0,3)
        linux /vmlinuz root=/dev/sda3 ro quiet splash
        initrd /initrd.img
}

Am I supposed to have ext2? My filesystem for all my partitions has been ext4 when I've manually partitioned, which I did for Arch and Ubuntu. Additionally there is no grub-update command with Arch's grub2, merely the grub-mkconfig command. Although they both seem very similar, if not the same.

---

### Post by oldfred on 2010-12-15
The ext2, ext3 & ext4 are a family as all ext3 & ext4 add is journaling and there is only one insmod file for the family, the ext2. If you look in /boot/grub you will see a long list of mod files.

osprober must be something Ubuntu has added. Not sure if it is part of the standard grub2 and Arch just does not offer it or not.

Since there is no update then you you would have to manually update the Arch entry to boot Ubuntu on every kernel update in Ubuntu. The second choice of using the links will let you have a permanent entry and still boot the newest kernel in Ubuntu from Arch.

I prefer to have Ubuntu's grub2 control booting, but that is your choice.

---

### Post by QLee on 2010-12-16
[QUOTE=Axolotl9250]... Additionally there is no grub-update command with Arch's grub2, merely the grub-mkconfig command. Although they both seem very similar, if not the same.[/QUOTE]

There is no, grub-update for Ubuntu either, the command is, update-grub.

What update-grub does is run grub-mkconfig specifying the the output file and path, just running it without specifying an output file only displays in the terminal, in that case grub.cfg is not written.

---

### Post by Axolotl9250 on 2010-12-16
Apologies, QLee, I meant update-grub. I've managed to find the solution! I had to build os-prober again and then upon updating grub.cfg the Ubuntu system was detected.

---

### Post by NibbleG on 2010-12-16
I have a similar problem, but it is a little different.  What commands did you use to update/rebuild os-prober?
I was trying to transfer a movies from my desktop to my laptop and [forgot] that my laptop was in suspend mode when i pulled the hdd from it and plugged it in to my desktop.
Any ideas?

Nibble G

---

### Post by oldfred on 2010-12-16
NibbleG, I think your problem is a lot different. 

Please start a new thread and post this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

Have you tried chkdsk if NTFS or e2fsck if ext3 or ext4 format?

---

### Post by NibbleG on 2010-12-16
Solved it, simply had to move the hdd back in to the desktop and shut it down **without** unmounting it.

---

