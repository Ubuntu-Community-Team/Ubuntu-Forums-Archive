---
title: "Passes GRUB and Ubuntu splash screen, then crashes/freezes before logon"
date: 2010-12-24
forum: General Help
---

### Post by dwigyit on 2010-12-24
After both an Ubuntu update and the enabling of a few settings in Ubuntu Tweak (Nautilus extensions only, so I doubt they caused it), Ubuntu stops booting passed a blank screen with a flashing underscore. It's nothing to do with GRUB, as it passes the dual-boot menu, and the Ubuntu loading screen shows without problems (other than some odd text-only mode it's got itself in, but it's been like that for ages so no new problems there). It's only after this that it goes to this blank flashing underscore screen. After a few seocnds on it, the HDD light stops flashing and it just sits there, so I have to power it off manually :(

Any help much appreciated :)

---

### Post by Quackers on 2010-12-24
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by VonFilmjölk on 2010-12-24
have U tried starting with out  quiet splash to se what it says doing start up?

---

### Post by dwigyit on 2010-12-24
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       411,647       409,600   7 HPFS/NTFS
/dev/sda2             411,648   312,578,047   312,166,400   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,046     2,000,895     1,998,850   5 Extended
/dev/sdb5               2,048     2,000,895     1,998,848  82 Linux swap / Solaris
/dev/sdb2           2,000,896   312,580,095   310,579,200  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9E8A8D0F8A8CE55D                       ntfs                                     
/dev/sda2        28F48BADF48B7BB6                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb2        f6aedbdb-c819-4e1e-905a-2c9351044dc0   ext4                                     
/dev/sdb5        e3ed7432-b797-4ff3-972b-68aa97a10c82   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set f6aedbdb-c819-4e1e-905a-2c9351044dc0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set f6aedbdb-c819-4e1e-905a-2c9351044dc0
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
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set f6aedbdb-c819-4e1e-905a-2c9351044dc0
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=f6aedbdb-c819-4e1e-905a-2c9351044dc0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set f6aedbdb-c819-4e1e-905a-2c9351044dc0
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=f6aedbdb-c819-4e1e-905a-2c9351044dc0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set f6aedbdb-c819-4e1e-905a-2c9351044dc0
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f6aedbdb-c819-4e1e-905a-2c9351044dc0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set f6aedbdb-c819-4e1e-905a-2c9351044dc0
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f6aedbdb-c819-4e1e-905a-2c9351044dc0 ro single 
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
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set f6aedbdb-c819-4e1e-905a-2c9351044dc0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set f6aedbdb-c819-4e1e-905a-2c9351044dc0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 9e8a8d0f8a8ce55d
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

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=f6aedbdb-c819-4e1e-905a-2c9351044dc0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=e3ed7432-b797-4ff3-972b-68aa97a10c82 none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 134.3GB: boot/grub/core.img
  33.4GB: boot/grub/grub.cfg
   1.7GB: boot/initrd.img-2.6.35-22-generic
 118.3GB: boot/initrd.img-2.6.35-23-generic
 129.9GB: boot/initrd.img-2.6.35-24-generic
 134.4GB: boot/vmlinuz-2.6.35-22-generic
 136.3GB: boot/vmlinuz-2.6.35-23-generic
 136.3GB: boot/vmlinuz-2.6.35-24-generic
 129.9GB: initrd.img
 118.3GB: initrd.img.old
 136.3GB: vmlinuz
 136.3GB: vmlinuz.old
```

One bootscript result presented in code tags :)

In don't understand most of what it says, but I have a feeling the problem is more to do with the GNOME login screen than the boot sequence. Just a guess, though :)

---

### Post by Quackers on 2010-12-24
You may be right :-)
However the boot script does show that although Windows is on drive sda the Windows bootloader is in the mbr of drive sdb. I don't know why that would be. Grub2 is installed in the mbr of sda but is looking for its boot files in sda2, but they're actually in sdb2.
In any event I think it may be advisable to re-install grub2, but a second opinion wouldn't do any harm :-)
In the meantime VonFilmjolk's suggestion is worth trying.
At the grub menu, making sure Ubuntu is highlighted, press the "e" key and in the new screen navigate to the line which ends with "quiet splash" and delete those two words then press ctrl + X to reboot. At some point the boot will stop and the last thing it tried to do will be displayed on your screen. Make a note of that. It may give someone an idea.

---

### Post by VonFilmjölk on 2010-12-24
when i come to think about it  i had a similar prob with my 64bit cmp. I replaced quiet splash with "noapic  apci_irq_balance"      the apci_irq_balance is so the system recognice that i have more than one core. since I had an Issue with that , remember chainging this in grubb loader will not result in a permanent sulution u will have to change the grubb loader file . dont remember how  but , Ill come back to you with that when i find It if that is your issue.

---

### Post by VaGentry on 2010-12-24
I have the same problem.  It started on the first restart after the latest update.  After a long string of text I get statements:

mount:mounting /dev on /root/dev failed no such file or directory
mount:mounting /sys on /root/sys failed no such file or directory
mount:mounting /proc on /root/proc failed no such file or directory
Target filesystem doesn't have requested /sbin/init
No init found. Try passing init=bootarg

Busybox v.1.15.3 (ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter help for a list of built in commands
(initramfs)

I can't even reinstall ubuntu without wiping out the Windows 7 partition.  In Windows I can't see the Ubuntu or root partition.

Any advice would be welcomed.

---

### Post by VonFilmjölk on 2010-12-24
well for your problem with  starting the partition that can't be found i have no sulution since I havnt had that issue my self, but regarding reinstalling u should have a partition with linux dev or something like it. was a while since i did this

---

### Post by VonFilmjölk on 2010-12-24
did u uppgrade from 10.04  to 10. 10 ? and then it were unable to locate  the parition? If u have  another  os installed, se if u can find a partiion  with equal size  in a partitioner tool or something like it to see if the partition still exist.

---

### Post by dwigyit on 2010-12-24
Ok - I've disabled quiet boot. The last few lines in the boot before it just stops are:
```
[   2.171565] EXT4-fs (sdb2): mounted filesystem with odered date mode. 0pts:
(null)
Begin: Running /scripts/local-bottom ... done
done.
Begin: Running /scripts/init-bottom ... done."
```

---

### Post by VaGentry on 2010-12-24
In my case I was already in 10.10.  I just performed the regular incremental update.

---

### Post by VonFilmjölk on 2010-12-24
karmic had a similar issue, some one seemes to have found a sulution for  that prob in this thread [https://bugs.launchpad.net/ubuntu/+bug/398214](https://bugs.launchpad.net/ubuntu/+bug/398214) im not saying this will work for you but it might be worth a shot

in short try either 1. Start your machine and select the "kernel linux" with the "down" button.
2. Press "e" on your keyboard.
3. Select the "kernel uuid=..." entry with the "down" button and type "e" again.
4. Change "quite splash" to "nomodeset". Press "Enter" and "b" on the keyboard.
or 1. Ensure you are connected to your router by DHCP.
2. Start your machine and select the "recovery kernel linux 2.6.31-10" with the "down" button. Press "e" on your keyboard.
3. Select the "kernel uuid=..." entry with the "down" button and type "e" again.
4. Change "ro single" to "rw init=/bin/bash". Press "Enter" and "b" on the keyboard.
5. Wait until booting stops and press "Enter".
6. "root@(none):" is displayed. Type in the konsole:
dhclient eth0
7. After this operation the connection to the internet is activated and you can type in the konsole:
apt-get dist-upgrade
8. Wait 10 min until upgrade is done.
9. Reboot your machine and select "kernel linux 2.6.31-9" in grub.



remember  I have not tried this  my self I am just reffering to ppl who said it worked for them and also this is for karmic "It might  solve it It might not"

---

### Post by dwigyit on 2010-12-24
That seems like it might work, but is there not a way to recover it from the CD instead of plugging it into a router and all that? Doesn't the ubuntu CD have any recovery options like the Windows CD does, or at least, with a bit of terminal work, have the ability to repair whatever damage the update manager did?

---

### Post by VonFilmjölk on 2010-12-25
nope no recovery from what I can see but you do have the option of booting from cd,  choose try ubuntu then u can start up your system with ubuntu and see if u can fint  your previous install

---

### Post by dwigyit on 2010-12-25
From what little I understand of the solution you posted before, it's just a case of reinstalling the kernal or something? The Ubuntu installer does that during an install so it must be on the CD somewhere?

I'll have to reccomend a recovery option on the Ubuntu CD on the Ubuntu Brainstorm :D

---

### Post by VonFilmjölk on 2010-12-25
well i couldnt find a grub recovery in the options on the cd. have u tried the sulutions i posted earlier?

---

### Post by dwigyit on 2010-12-25
It's nothing to do with GRUB, it passes grub before it crashes. And I havn't tried the connecting to the router solution because I don't have the right cables :(

---

### Post by dwigyit on 2010-12-25
Ok, Vonfilmjonk, I tried your method with a cable I found but it doesn't work. The first problem is that Grub's text editor has changed so enter and b now just type enter and b. I've adapted as best as I can (using appropriate keys etc), but I still get the same errors during boot :(


Thing is, I'd be more than happy to just reinstall Ubuntu if only I could back up/export my precious MySQL databases through only the filesysten access provided by the live CD. The only method I know if is through PHPMyAdmin which would have to run in Xampp along with MySQL. Any ideas on how to save those SQL databases?

---

### Post by dwigyit on 2010-12-25
Reading the other posts, I'll just mention that it wasn't a distro upgrade I did, just an ordinary everyday update with update manager :)

---

### Post by VonFilmjölk on 2010-12-27
well Im sorry I dont think I can give any more help, Ill stay on it but Ive run out of suggestions. one thing that might work if u just want to export your files an stuff is to run ubuntu from your cd. and se if u can find your file system that way.

---

