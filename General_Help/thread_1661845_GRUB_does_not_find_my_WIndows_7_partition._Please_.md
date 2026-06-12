---
title: "GRUB does not find my WIndows 7 partition. Please help!"
date: 2011-01-07
forum: General Help
---

### Post by Charkel on 2011-01-07
Ok so I messed up my mbr by deleting my other drive which I guess had the MBR for both my OS (2 Windows 7's). So i installed Ubuntu in an attempt to fix it all hoping to get the GRUB. It then booted directly into Ubuntu.
So I ran bootsect.exe to fix the mbr and it said success.
Still boots into Ubuntu directly without and grub.

I ran **sudo update-grub** 
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done

No windows loader found :(

Please help. I have to attend a few online games later and need my windows.

---

### Post by sikander3786 on 2011-01-07
Please post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

That would tell us more about your setup and thus help diagnose the problem.

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

---

### Post by Charkel on 2011-01-07
> **sikander3786 said:**
> Please post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

That would tell us more about your setup and thus help diagnose the problem.

While posting, click the # icon in post menu and paste your text in between the generated ```
 tags.

[CODE]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,773,119   976,771,072   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   409,602,047   409,600,000   7 HPFS/NTFS
/dev/sdb2         409,602,048 1,914,457,516 1,504,855,469   7 HPFS/NTFS
/dev/sdb3       1,914,458,110 1,953,523,711    39,065,602   5 Extended
/dev/sdb5       1,914,458,112 1,916,456,959     1,998,848  82 Linux swap / Solaris
/dev/sdb6       1,916,459,008 1,953,523,711    37,064,704  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        387A25E5251D8944                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0CD0E901D0E8F1BE                       ntfs                                     
/dev/sdb2        FC162B2D162AE87A                       ntfs                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        a4a3dec5-6c6c-4a4a-bc01-b4dd11cdac63   swap                                     
/dev/sdb6        34aa3eeb-7a69-4a0a-9b78-4d11e6e16280   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 34aa3eeb-7a69-4a0a-9b78-4d11e6e16280
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 34aa3eeb-7a69-4a0a-9b78-4d11e6e16280
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 34aa3eeb-7a69-4a0a-9b78-4d11e6e16280
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=34aa3eeb-7a69-4a0a-9b78-4d11e6e16280 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 34aa3eeb-7a69-4a0a-9b78-4d11e6e16280
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=34aa3eeb-7a69-4a0a-9b78-4d11e6e16280 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 34aa3eeb-7a69-4a0a-9b78-4d11e6e16280
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 34aa3eeb-7a69-4a0a-9b78-4d11e6e16280
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=34aa3eeb-7a69-4a0a-9b78-4d11e6e16280 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=a4a3dec5-6c6c-4a4a-bc01-b4dd11cdac63 none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


 986.0GB: boot/grub/core.img
 985.6GB: boot/grub/grub.cfg
 992.3GB: boot/initrd.img-2.6.35-22-generic
 986.0GB: boot/vmlinuz-2.6.35-22-generic
 992.3GB: initrd.img
 986.0GB: vmlinuz
```

sdb1 is my Windows install.

---

### Post by Charkel on 2011-01-07
Firkkin thread keeps getting bumped to the last page :( 
Still need help guys.

---

### Post by Quackers on 2011-01-07
The first 2 Windows boot files are missing from sdb1. They can be replaced by running the Startup Repair option from the Windows repair/installation disc. This may need to be run 3 times.
This should get Windows booting again.
Then, to get Ubuntu booting you will need to re-install grub to sdb.

---

### Post by sikander3786 on 2011-01-07
So you are missing some boot files for Windows 7. Boot files on your sdb1 need to look like this.

> Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

You need to perform startup repair from a Windows 7 install/repair disc at least 3 times. If you don't have the disc, grab it here. Its legit.

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Once you are able to boot Windows successfully (independent of Grub), you need to re-install Grub. Boot an Ubuntu Live CD/USB and do the following commands.

```
sudo mount /dev/sdb6 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sd[COLOR="Red"]b[/COLOR]
```

Note, it is just sdb without an integer and not sdb1 or sdb6 for the 2nd command.

Reboot and hopefully, it should list Windows 7 this time. If it doesn't, from installed Ubuntu's Terminal,

```
sudo update-grub
```

Good Luck!

---

### Post by Charkel on 2011-01-07
Problem is. The windows 7 repair does not show my drives :o
But the install menu does :\

---

### Post by Quackers on 2011-01-07
It doesn't need to. Are you entering the recovery mode and then "repair my computer", then Startup Repair?

---

### Post by Quackers on 2011-01-07
It doesn't need to. Are you entering the recovery mode and then "repair my computer", then Startup Repair?

---

### Post by sikander3786 on 2011-01-07
As Quackers said above :-)

[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)

If Startup Repair doesn't solve your problem, you can try bootrec.exe from the command prompt.

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by Charkel on 2011-01-07
DONE!
Wow that was in the last second. My first match is in 30 minutes :D

Thank you so much for your help!

My solution:
I removed the empty hard drive. Dunno if it made nay difference but just to be safe. And then i booted into restore and saw my HDD!
I restored the booting things and then restarted. Then ubuntu booted without a grub...
BUT. With a ```
sudo update-grub
``` i got my Windows 7 listed in the terminal! WIN!

Thank you again guys. I _really_ appreciate it :)

P.S
Only took me 9 hours...

---

### Post by sikander3786 on 2011-01-08
Glad you got it working :-)

(On behalf of all the contributors) Please mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

