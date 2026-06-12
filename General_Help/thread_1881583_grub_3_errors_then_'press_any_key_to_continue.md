---
title: "grub: 3 errors then 'press any key to continue"
date: 2011-11-15
forum: General Help
---

### Post by DougieFresh4U on 2011-11-15
A triple boot system:  Debian - Windows 7 -Ubuntu
When I start machine and I am presented with grub, my choices are 
in this order:
Debian
Win7
Ubuntu
Debian and Win7 boot just fine. When I scroll down through grub and
select 'Ubunu' it goes to a screen with the following messege:
[B]Error: no argument specified
Error: file not found
Error: you need to load the kernel first
Press any key to continue[/B]
So I press any key and it takes me back to grub menu
Any advice on how to get past this would be great. Everything has been working great but I do recall a grub update a couple of days ago

---

### Post by drs305 on 2011-11-15
It looks like Debian is controlling your Grub menu. Was it a Debian update that caused the problems to start? If you did an update while in Ubuntu your Debian Grub may not be up to date. Run "sudo update-grub" so it can reread your Ubuntu partition.

If you download and run the boot info script and post the contents of RESULTS.txt we can take a look at your boot status.

You can get to the script page by clicking the "BIS" link in my signature line.

---

### Post by DougieFresh4U on 2011-11-15
```

If you download and run the boot info script and post the contents of RESULTS.txt we can take a look at your boot status.
```
When I try to run boot info script, I am getting this:

```
dougie@debian:~$ bash ~/Desktop/boot_info_script.sh

boot_info_script version: 0.60        [17 May 2011]

"blkid" could not be found.
"fdisk" could not be found.
"filefrag" could not be found.
"losetup" could not be found.

"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.


Please install the missing program(s) and run boot_info_script again.
```

Oh, and thanks for your reply
I am using my Debian install for this

---

### Post by drs305 on 2011-11-15
Run the script as root. I'm not familiar with how Debian uses 'blkid', etc, but try running the script this way: 
```
sudo bash ~/Desktop/boot_info_script.sh
```

You might also install 'gawk' before running the script, although it will run with awk but will complain a bit.

---

### Post by DougieFresh4U on 2011-11-15
> **drs305 said:**
> Run the script as root. I'm not familiar with how Debian uses 'blkid', etc, but try running the script this way: 
```
sudo bash ~/Desktop/boot_info_script.sh
```

You might also install 'gawk' before running the script, although it will run with awk but will complain a bit.
Thanks for your help. It's still telling me it can't find directory no matter where I extract it to.
I am gonna do  a little checking @ Debian but I don't like the way some respond over there

---

### Post by Cyclane on 2011-11-15
I think the most important thing to do is run:
```
sudo update-grub
```
drs305 suggested this already but I can't read you've actually done this, can you confirm this?

If that doesn't help the boot-script becomes more important.

---

### Post by DougieFresh4U on 2011-11-15
> **Cyclane said:**
> I think the most important thing to do is run:
```
sudo update-grub
```
drs305 suggested this already but I can't read you've actually done this, can you confirm this?

If that doesn't help the boot-script becomes more important.
Sorry I failed to mention that I had updated grub before I came to the forum for assistance. 
I have learned that Debian has a .deb file for boot info script, but I am having 
no luck installing it. Some sort of GTK errors showing in the terminal.
I wonder is it possible to chroot into my Ubuntu from my Debian partition and update my Ubuntu and grub?

---

### Post by Cyclane on 2011-11-15
Strange because this should be easily fixed by updating grub.
chrooting to your ubuntu install probably won't help because grub uses the /boot directory of your debian install.

One of the things grub does is link to the kernel you want to use (in this case the kernel on the ubuntu install). Somehow it points to the wrong direction. When you run 'sudo update-grub' it would remap all the links, including the link to your kernel.

For us to help you, we would need some more information. The boot-script collects a lot of this data by running pretty basic commands. Commands I would imagine also begin present on a debian install, but that's a whole other problem.

Could you start by posting your grub config and fdisk -l?

---

### Post by DougieFresh4U on 2011-11-15
> **Cyclane said:**
> Could you start by posting your grub config and fdisk -l?
Thanks for taking the time to help me.
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
160 heads, 6 sectors/track, 651190 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d06a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           6   326738234   163369114+   7  HPFS/NTFS/exFAT
/dev/sda2       326739966   625141759   149200897    5  Extended
/dev/sda5       612945920   625141759     6097920   82  Linux swap / Solaris
/dev/sda6       607039488   612943871     2952192   82  Linux swap / Solaris
/dev/sda7       326739968   470245375    71752704   83  Linux
/dev/sda8       470247424   607037439    68395008   83  Linux

Partition table entries are not in disk order

```

---

### Post by Cyclane on 2011-11-15
No problem, but could I get the contents of /boot/grub/grub.cfg?

and also the following command so I can see what you're currently booting to:
```
mount | egrep 'ext|xfs'
```

---

### Post by DougieFresh4U on 2011-11-15
> **Cyclane said:**
> No problem, but could I get the contents of /boot/grub/grub.cfg?

and also the following command so I can see what you're currently booting to:
```
mount | egrep 'ext|xfs'
```
```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Debian GNU/Linux, with Linux 3.1.0-1-amd64' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 3.1.0-1-amd64 ...'
	linux	/boot/vmlinuz-3.1.0-1-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.1.0-1-amd64
}
menuentry 'Debian GNU/Linux, with Linux 3.1.0-1-amd64 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 3.1.0-1-amd64 ...'
	linux	/boot/vmlinuz-3.1.0-1-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.1.0-1-amd64
}
menuentry 'Debian GNU/Linux, with Linux 3.0.0-2-amd64' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 3.0.0-2-amd64 ...'
	linux	/boot/vmlinuz-3.0.0-2-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-2-amd64
}
menuentry 'Debian GNU/Linux, with Linux 3.0.0-2-amd64 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 3.0.0-2-amd64 ...'
	linux	/boot/vmlinuz-3.0.0-2-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-2-amd64
}
menuentry 'Debian GNU/Linux, with Linux 3.0.0-1-amd64' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 3.0.0-1-amd64 ...'
	linux	/boot/vmlinuz-3.0.0-1-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-1-amd64
}
menuentry 'Debian GNU/Linux, with Linux 3.0.0-1-amd64 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 3.0.0-1-amd64 ...'
	linux	/boot/vmlinuz-3.0.0-1-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-1-amd64
}
menuentry 'Debian GNU/Linux, with Linux 2.6.39-2-amd64' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 2.6.39-2-amd64 ...'
	linux	/boot/vmlinuz-2.6.39-2-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.39-2-amd64
}
menuentry 'Debian GNU/Linux, with Linux 2.6.39-2-amd64 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 2.6.39-2-amd64 ...'
	linux	/boot/vmlinuz-2.6.39-2-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.39-2-amd64
}
menuentry 'Debian GNU/Linux, with Linux 2.6.32-5-amd64' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 2.6.32-5-amd64 ...'
	linux	/boot/vmlinuz-2.6.32-5-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-5-amd64
}
menuentry 'Debian GNU/Linux, with Linux 2.6.32-5-amd64 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 2.6.32-5-amd64 ...'
	linux	/boot/vmlinuz-2.6.32-5-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-5-amd64
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_otheros ###

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
menuentry "Windows Vista (loader)" {
	set root=(hd0,msdos1)
	search --no-floppy --fs-uuid --set 34c025f5c025bdcc
	chainloader +1
}

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
menuentry "Ubuntu, with Linux 2.6.39-020639rc4-generic (on /dev/sda7)" {
	set root=(hd0,msdos7)
	search --no-floppy --fs-uuid --set c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	linux /boot/vmlinuz-2.6.39-020639rc4-generic root=UUID=c5ced1b2-42dd-4895-9a29-8c0d57a63fba ro quiet splash vt.handoff=7 
	initrd /boot/initrd.img-2.6.39-020639rc4-generic
}


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
menuentry "Ubuntu, with Linux 2.6.39-020639rc4-generic (recovery mode) (on /dev/sda7)" {
	set root=(hd0,msdos7)
	search --no-floppy --fs-uuid --set c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	linux /boot/vmlinuz-2.6.39-020639rc4-generic root=UUID=c5ced1b2-42dd-4895-9a29-8c0d57a63fba ro single 
	initrd /boot/initrd.img-2.6.39-020639rc4-generic
}


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
menuentry "Ubuntu, with Linux 2.6.38-9-generic (on /dev/sda7)" {
	set root=(hd0,msdos7)
	search --no-floppy --fs-uuid --set c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	linux /boot/vmlinuz-2.6.38-9-generic root=UUID=c5ced1b2-42dd-4895-9a29-8c0d57a63fba ro quiet splash vt.handoff=7 
	initrd /boot/initrd.img-2.6.38-9-generic
}


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
menuentry "Ubuntu, with Linux 2.6.38-9-generic (recovery mode) (on /dev/sda7)" {
	set root=(hd0,msdos7)
	search --no-floppy --fs-uuid --set c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	linux /boot/vmlinuz-2.6.38-9-generic root=UUID=c5ced1b2-42dd-4895-9a29-8c0d57a63fba ro single 
	initrd /boot/initrd.img-2.6.38-9-generic
}

### END /etc/grub.d/30_otheros ###

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
```
```
mount | egrep 'ext|xfs'
/dev/sda7 on / type ext3 (rw,errors=remount-ro,commit=0)
```

---

### Post by drs305 on 2011-11-16
The menuentry shows Ubuntu on sda7 and multiple kernels. The first one is a release candidate kernel. It seems a bit odd that the older kernel is listed first.  Have you tried every Ubuntu entry?

From the Grub menu, you can check the existing kernels available by pressing 'c' to get to the Grub command line. Run the following command to inspect the available kernels in the Ubuntu /boot/grub partition. 
```
ls (hd0,7)/boot
```

Method 1:
Note the exact name of one or two of the kernels. Then press ESC and highlight the Ubuntu entry on the Grub menu.

Press 'e' to edit the entry and use the cursors to edit the 'linux' and 'initrd' lines to match the existing kernel/initrd designations. Once you have made the changes to both lines, press CTRL-x to see if it boots.

Method 2:
Use this command instead:
```
ls (hd0,7)/
```

Check for the presence of "vmlinuz" and "initrd.img". If they exist, press ESC and highlight the Ubuntu entry on the Grub menu.

Press 'e' to edit the entry and use the cursors to edit the 'linux' and 'initrd' lines to 
> linux (hd0,7)/vmlinuz ......<leave the rest>
initrd (hd0,7)/initrd.img

Once you have made the changes to both lines, press CTRL-x to see if it boots.

If Ubuntu boots, run "sudo update-grub". This will only update the Ubuntu Grub menu; however when Debian updates it's Grub the next time you run it in Debian the update will import the Ubuntu Grub items if found.

---

### Post by goofey24 on 2011-11-24
If your Ubuntu testing partition isn't all that important, you could just do a fresh install over your Ubuntu that will not boot and let grub 'fix itself up'

---

### Post by utnubuuser on 2011-11-25
I'm not sure what you're trying to get at here...   are you unable to boot into any of the OSs, or you're just locked out of Ubuntu?

To get into Ubuntu, if you can get as far as a grub> prompt is fairly easy.  If you can get as far as the grub menu list, then you'll be able to manually boot Ubuntu by pressing c while at the grub menu. 

for instructions on booting a kernel manually, try [http://sazeit.com/articles/boot-ubuntu-from-grub-prompt]("http://sazeit.com/articles/boot-ubuntu-from-grub-prompt")

---

### Post by DougieFresh4U on 2011-11-26
> **drs305 said:**
> Run the script as root. I'm not familiar with how Debian uses 'blkid', etc, but try running the script this way: 
```
sudo bash ~/Desktop/boot_info_script.sh
```

You might also install 'gawk' before running the script, although it will run with awk but will complain a bit.
I was able to run the boot info using a live-cd
```
     Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    346160648 of the same hard drive for core.img. core.img is at this 
    location and looks for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux wheezy/sid
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu precise (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
160 heads, 6 sectors/track, 651190 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *              6   326,738,234   326,738,229   7 NTFS / exFAT / HPFS
/dev/sda2         326,739,966   625,141,759   298,401,794   5 Extended
/dev/sda5         612,945,920   625,141,759    12,195,840  82 Linux swap / Solaris
/dev/sda6         607,039,488   612,943,871     5,904,384  82 Linux swap / Solaris
/dev/sda7         326,739,968   470,245,375   143,505,408  83 Linux
/dev/sda8         470,247,424   607,037,439   136,790,016  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        34C025F5C025BDCC                       ntfs       
/dev/sda5        744aa943-a15d-4976-92b6-f8450417978e   swap       
/dev/sda6        d140d821-4971-4969-bfd1-ececc86c7ced   swap       
/dev/sda7        20927c0e-36b9-4d31-99b4-b5a2dc208e82   ext3       
/dev/sda8        c5ced1b2-42dd-4895-9a29-8c0d57a63fba   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda7/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Debian GNU/Linux, with Linux 3.1.0-1-amd64' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 3.1.0-1-amd64 ...'
	linux	/boot/vmlinuz-3.1.0-1-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.1.0-1-amd64
}
menuentry 'Debian GNU/Linux, with Linux 3.1.0-1-amd64 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 3.1.0-1-amd64 ...'
	linux	/boot/vmlinuz-3.1.0-1-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.1.0-1-amd64
}
menuentry 'Debian GNU/Linux, with Linux 3.0.0-2-amd64' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 3.0.0-2-amd64 ...'
	linux	/boot/vmlinuz-3.0.0-2-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-2-amd64
}
menuentry 'Debian GNU/Linux, with Linux 3.0.0-2-amd64 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 3.0.0-2-amd64 ...'
	linux	/boot/vmlinuz-3.0.0-2-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-2-amd64
}
menuentry 'Debian GNU/Linux, with Linux 3.0.0-1-amd64' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 3.0.0-1-amd64 ...'
	linux	/boot/vmlinuz-3.0.0-1-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-1-amd64
}
menuentry 'Debian GNU/Linux, with Linux 3.0.0-1-amd64 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 3.0.0-1-amd64 ...'
	linux	/boot/vmlinuz-3.0.0-1-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-1-amd64
}
menuentry 'Debian GNU/Linux, with Linux 2.6.39-2-amd64' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 2.6.39-2-amd64 ...'
	linux	/boot/vmlinuz-2.6.39-2-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.39-2-amd64
}
menuentry 'Debian GNU/Linux, with Linux 2.6.39-2-amd64 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 2.6.39-2-amd64 ...'
	linux	/boot/vmlinuz-2.6.39-2-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.39-2-amd64
}
menuentry 'Debian GNU/Linux, with Linux 2.6.32-5-amd64' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 2.6.32-5-amd64 ...'
	linux	/boot/vmlinuz-2.6.32-5-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-5-amd64
}
menuentry 'Debian GNU/Linux, with Linux 2.6.32-5-amd64 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	echo	'Loading Linux 2.6.32-5-amd64 ...'
	linux	/boot/vmlinuz-2.6.32-5-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-5-amd64
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_otheros ###

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
menuentry "Windows Vista (loader)" {
	set root=(hd0,msdos1)
	search --no-floppy --fs-uuid --set 34c025f5c025bdcc
	chainloader +1
}

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
menuentry "Ubuntu, with Linux 2.6.39-020639rc4-generic (on /dev/sda7)" {
	set root=(hd0,msdos7)
	search --no-floppy --fs-uuid --set c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	linux /boot/vmlinuz-2.6.39-020639rc4-generic root=UUID=c5ced1b2-42dd-4895-9a29-8c0d57a63fba ro quiet splash vt.handoff=7 
	initrd /boot/initrd.img-2.6.39-020639rc4-generic
}


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
menuentry "Ubuntu, with Linux 2.6.39-020639rc4-generic (recovery mode) (on /dev/sda7)" {
	set root=(hd0,msdos7)
	search --no-floppy --fs-uuid --set c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	linux /boot/vmlinuz-2.6.39-020639rc4-generic root=UUID=c5ced1b2-42dd-4895-9a29-8c0d57a63fba ro single 
	initrd /boot/initrd.img-2.6.39-020639rc4-generic
}


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
menuentry "Ubuntu, with Linux 2.6.38-9-generic (on /dev/sda7)" {
	set root=(hd0,msdos7)
	search --no-floppy --fs-uuid --set c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	linux /boot/vmlinuz-2.6.38-9-generic root=UUID=c5ced1b2-42dd-4895-9a29-8c0d57a63fba ro quiet splash vt.handoff=7 
	initrd /boot/initrd.img-2.6.38-9-generic
}


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
menuentry "Ubuntu, with Linux 2.6.38-9-generic (recovery mode) (on /dev/sda7)" {
	set root=(hd0,msdos7)
	search --no-floppy --fs-uuid --set c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	linux /boot/vmlinuz-2.6.38-9-generic root=UUID=c5ced1b2-42dd-4895-9a29-8c0d57a63fba ro single 
	initrd /boot/initrd.img-2.6.38-9-generic
}

### END /etc/grub.d/30_otheros ###

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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=744aa943-a15d-4976-92b6-f8450417978e none            swap    sw              0       0
# swap was on /dev/sda6 during installation
UUID=d140d821-4971-4969-bfd1-ececc86c7ced none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 165.062286377 = 177.234280448  boot/grub/core.img                             1
 165.075229645 = 177.248178176  boot/grub/grub.cfg                             1
 164.815067291 = 176.968830976  boot/initrd.img-2.6.32-5-amd64                 5
 164.936424255 = 177.099137024  boot/initrd.img-2.6.39-2-amd64                 8
 164.828498840 = 176.983252992  boot/initrd.img-3.0.0-1-amd64                  5
 164.871120453 = 177.029017600  boot/initrd.img-3.0.0-2-amd64                  9
 164.871662140 = 177.029599232  boot/initrd.img-3.1.0-1-amd64                 16
 164.913391113 = 177.074405376  boot/vmlinuz-2.6.32-5-amd64                    2
 164.835517883 = 176.990789632  boot/vmlinuz-2.6.39-2-amd64                    2
 164.875743866 = 177.033981952  boot/vmlinuz-3.0.0-1-amd64                     4
 164.882759094 = 177.041514496  boot/vmlinuz-3.0.0-2-amd64                     5
 164.855773926 = 177.012539392  boot/vmlinuz-3.1.0-1-amd64                     2
 164.855773926 = 177.012539392  vmlinuz                                        2
 164.882759094 = 177.041514496  vmlinuz.old                                    5

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root c5ced1b2-42dd-4895-9a29-8c0d57a63fba
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos8)'
  search --no-floppy --fs-uuid --set=root c5ced1b2-42dd-4895-9a29-8c0d57a63fba
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root c5ced1b2-42dd-4895-9a29-8c0d57a63fba
insmod jpeg
if background_image /boot/grub/064.jpg; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
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
menuentry 'Ubuntu, with Linux 3.1.0-2-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	linux	/boot/vmlinuz-3.1.0-2-generic root=UUID=c5ced1b2-42dd-4895-9a29-8c0d57a63fba ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.1.0-2-generic
}
menuentry 'Ubuntu, with Linux 3.1.0-2-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	echo	'Loading Linux 3.1.0-2-generic ...'
	linux	/boot/vmlinuz-3.1.0-2-generic root=UUID=c5ced1b2-42dd-4895-9a29-8c0d57a63fba ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.1.0-2-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.1.0-1-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	linux	/boot/vmlinuz-3.1.0-1-generic root=UUID=c5ced1b2-42dd-4895-9a29-8c0d57a63fba ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.1.0-1-generic
}
menuentry 'Ubuntu, with Linux 3.1.0-1-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	echo	'Loading Linux 3.1.0-1-generic ...'
	linux	/boot/vmlinuz-3.1.0-1-generic root=UUID=c5ced1b2-42dd-4895-9a29-8c0d57a63fba ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.1.0-1-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=c5ced1b2-42dd-4895-9a29-8c0d57a63fba ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=c5ced1b2-42dd-4895-9a29-8c0d57a63fba ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.39-020639rc4-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	linux	/boot/vmlinuz-2.6.39-020639rc4-generic root=UUID=c5ced1b2-42dd-4895-9a29-8c0d57a63fba ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.39-020639rc4-generic
}
menuentry 'Ubuntu, with Linux 2.6.39-020639rc4-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	echo	'Loading Linux 2.6.39-020639rc4-generic ...'
	linux	/boot/vmlinuz-2.6.39-020639rc4-generic root=UUID=c5ced1b2-42dd-4895-9a29-8c0d57a63fba ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.39-020639rc4-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	linux	/boot/vmlinuz-2.6.38-9-generic root=UUID=c5ced1b2-42dd-4895-9a29-8c0d57a63fba ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	echo	'Loading Linux 2.6.38-9-generic ...'
	linux	/boot/vmlinuz-2.6.38-9-generic root=UUID=c5ced1b2-42dd-4895-9a29-8c0d57a63fba ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-9-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root c5ced1b2-42dd-4895-9a29-8c0d57a63fba
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 34C025F5C025BDCC
	chainloader +1
}
menuentry "Debian GNU/Linux, with Linux 3.0.0-2-amd64 (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	linux /boot/vmlinuz-3.0.0-2-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro quiet
	initrd /boot/initrd.img-3.0.0-2-amd64
}
menuentry "Debian GNU/Linux, with Linux 3.0.0-2-amd64 (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	linux /boot/vmlinuz-3.0.0-2-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro single
	initrd /boot/initrd.img-3.0.0-2-amd64
}
menuentry "Debian GNU/Linux, with Linux 3.0.0-1-amd64 (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	linux /boot/vmlinuz-3.0.0-1-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro quiet
	initrd /boot/initrd.img-3.0.0-1-amd64
}
menuentry "Debian GNU/Linux, with Linux 3.0.0-1-amd64 (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	linux /boot/vmlinuz-3.0.0-1-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro single
	initrd /boot/initrd.img-3.0.0-1-amd64
}
menuentry "Debian GNU/Linux, with Linux 2.6.39-2-amd64 (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	linux /boot/vmlinuz-2.6.39-2-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro quiet
	initrd /boot/initrd.img-2.6.39-2-amd64
}
menuentry "Debian GNU/Linux, with Linux 2.6.39-2-amd64 (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	linux /boot/vmlinuz-2.6.39-2-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro single
	initrd /boot/initrd.img-2.6.39-2-amd64
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-5-amd64 (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	linux /boot/vmlinuz-2.6.32-5-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro quiet
	initrd /boot/initrd.img-2.6.32-5-amd64
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-5-amd64 (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 20927c0e-36b9-4d31-99b4-b5a2dc208e82
	linux /boot/vmlinuz-2.6.32-5-amd64 root=UUID=20927c0e-36b9-4d31-99b4-b5a2dc208e82 ro single
	initrd /boot/initrd.img-2.6.32-5-amd64
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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=c5ced1b2-42dd-4895-9a29-8c0d57a63fba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=744aa943-a15d-4976-92b6-f8450417978e none            swap    sw              0       0
# swap was on /dev/sda6 during installation
UUID=d140d821-4971-4969-bfd1-ececc86c7ced none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 282.444759369 = 303.272751104  boot/grub/core.img                             1
 228.823181152 = 245.697019904  boot/grub/grub.cfg                             1
 260.996524811 = 280.242884608  boot/initrd.img-2.6.38-9-generic               2
 236.111152649 = 253.522419712  boot/initrd.img-2.6.39-020639rc4-generic       2
 232.611431122 = 249.764622336  boot/initrd.img-3.0.0-12-generic               2
 224.523475647 = 241.080246272  boot/initrd.img-3.1.0-1-generic                2
 239.122070312 = 256.755367936  boot/initrd.img-3.1.0-2-generic                2
 260.395820618 = 279.597883392  boot/vmlinuz-2.6.38-9-generic                  1
 230.669319153 = 247.679295488  boot/vmlinuz-2.6.39-020639rc4-generic          1
 248.486671448 = 266.810531840  boot/vmlinuz-3.0.0-12-generic                  1
 235.087478638 = 252.423258112  boot/vmlinuz-3.1.0-1-generic                   1
 235.501541138 = 252.867854336  boot/vmlinuz-3.1.0-2-generic                   2
 235.501541138 = 252.867854336  vmlinuz                                        2
 235.087478638 = 252.423258112  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by alfalahi on 2011-11-27
easy fix

start up ur Ubuntu live CD

start internet

install Boot repair and click fix  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

after you done restart ur pc and it will work

i have tried it 34573904 times i always break my system trying new things

good luck

---

### Post by drs305 on 2011-11-27
Your Ubuntu Grub files look OK, so it is probably just a matter of rebuilding the Ubuntu boot's core.img 

You could first just try running "sudo update-grub" from Debian. Debian appears to use a slightly different variation of Grub 2 as far as OO probing goes. If you haven't tried it already, updating Grub may be all you need for the system to properly identify Ubuntu. Otherwise:

I'd do what *alfalahi* recommends and run the Boot Repair tool. See if it allows you to repair the Ubuntu Grub installation. You can always revert back to Debian's after everything is working. Allow Ubuntu's Grub to be installed on the MBR, not the Ubuntu partition.

Once you get Ubuntu booting again you can decide whether you want Ubuntu or Debian controlling the boot. Ubuntu's Grub files have located your Debian and Windows OS's, so having it control the boot will allow you to boot any of your OS's.

If you decide to allow Ubuntu to take over booting, once booted into Ubuntu just run:```

sudo grub-install /dev/sda
```

---

### Post by DougieFresh4U on 2011-11-28
> **alfalahi said:**
> easy fix

start up ur Ubuntu live CD

start internet

install Boot repair and click fix  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

after you done restart ur pc and it will work

i have tried it 34573904 times i always break my system trying new things

good luck

> **drs305 said:**
> Your Ubuntu Grub files look OK, so it is probably just a matter of rebuilding the Ubuntu boot's core.img 

You could first just try running "sudo update-grub" from Debian. Debian appears to use a slightly different variation of Grub 2 as far as OO probing goes. If you haven't tried it already, updating Grub may be all you need for the system to properly identify Ubuntu. Otherwise:

I'd do what *alfalahi* recommends and run the Boot Repair tool. See if it allows you to repair the Ubuntu Grub installation. You can always revert back to Debian's after everything is working. Allow Ubuntu's Grub to be installed on the MBR, not the Ubuntu partition.

Once you get Ubuntu booting again you can decide whether you want Ubuntu or Debian controlling the boot. Ubuntu's Grub files have located your Debian and Windows OS's, so having it control the boot will allow you to boot any of your OS's.

If you decide to allow Ubuntu to take over booting, once booted into Ubuntu just run:```

sudo grub-install /dev/sda
```
Thanks for all the help :D
All sorted out now as I installed boot repair to my Debian partition and let it run annd re-booted to a fixed system.
Needless to say I had over 575 updates waiting for my attention with my Ubuntu :p and all went smooth

---

