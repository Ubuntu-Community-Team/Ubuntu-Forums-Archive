---
title: "grub.cfg file"
date: 2010-01-28
forum: General Help
---

### Post by sandkernel on 2010-01-28
Reading about the new way ubuntu works with grub. so now there is no menu.lst and from what I've read you aren't supposed to manually edit this file.

Currently I'm dual booting XP/Ubuntu 9.10. I am going to remove XP from my drive and later create an ext4 filesystem out of it. If I unbderstand this correctly, I should be able to fire up Gparted while Linux is running, delete the partiton and then run update-grub2. update-grub2 should see the blank partition, and then successfully update /boot/grub/grub.cfg. This should allow me to boot successfully.

Before I do this I noticed that in Gparted I see the XP partition has flag "boot". No other partition has that. Now, if I wipe XP from Gparted, will it wipe out some important boot information? I guess what I am wondering is, does Ubuntu have stored some required boot info on the mbr on that partition that, if I wipe it out, will be lost and therefore result in a failed boot next time I reboot?

Here's my layout:
/dev/sda1 XP ntfs Flag:boot
/dev/sda2 extended
/dev/sda5 /
/dev/sda6 swap
/dev/sda7 /projects

What do ya'll think?

---

### Post by audiomick on 2010-01-28
Hallo.
What you describe sounds right to me, although I haven't actually done it myself.

As far as I know, the MBR is outside the partitions you can manipulate with gparted. Amongst other things, I believe the partition table is in there.

Have a look here
[https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows)
the guide refers to grub, and you need grub2, so here as well
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

The command you need to reset your grub is
```
sudo update-grub
```
That is explained in the Grub 2 documentation the the link above will bring you to.

---

### Post by philinux on 2010-01-28
> **sandkernel said:**
> Reading about the new way ubuntu works with grub. so now there is no menu.lst and from what I've read you aren't supposed to manually edit this file.

Currently I'm dual booting XP/Ubuntu 9.10. I am going to remove XP from my drive and later create an ext4 filesystem out of it. If I unbderstand this correctly, I should be able to fire up Gparted while Linux is running, delete the partiton and then run update-grub2. update-grub2 should see the blank partition, and then successfully update /boot/grub/grub.cfg. This should allow me to boot successfully.

Before I do this I noticed that in Gparted I see the XP partition has flag "boot". No other partition has that. Now, if I wipe XP from Gparted, will it wipe out some important boot information? I guess what I am wondering is, does Ubuntu have stored some required boot info on the mbr on that partition that, if I wipe it out, will be lost and therefore result in a failed boot next time I reboot?

Here's my layout:
/dev/sda1 XP ntfs Flag:boot
/dev/sda2 extended
/dev/sda5 /
/dev/sda6 swap
/dev/sda7 /projects

What do ya'll think?

If this is one drive then grub should be on the mbr unless you told it to install to a partition. While your at it with gparted you could just format the partition as ext4. That would get rid of wondows in one go.

Then run sudo update-grub.

See the grub link bin my sig for info on grub2.

---

### Post by oldfred on 2010-01-28
the boot flag is only used by windows (maybe some others), not by Ubuntu. So you do not have to have a partition set as boot for Ubuntu to boot.

---

### Post by Leppie on 2010-01-28
if you want a more accurate answer, please [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt.

---

### Post by sandkernel on 2010-01-28
> **Leppie said:**
> if you want a more accurate answer, please [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt.

Thanks for the reply. Here are the results:

root@camellia:/home/mike# cat RESULTS.txt
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x64656469

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    92,389,814    92,387,767   7 HPFS/NTFS
/dev/sda2          92,389,815   312,576,704   220,186,890   5 Extended
/dev/sda5          92,389,878   303,532,109   211,142,232  83 Linux
/dev/sda6         303,532,173   305,572,364     2,040,192  82 Linux swap / Solaris
/dev/sda7         305,572,428   312,576,704     7,004,277  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        421E5E981E5E8537                       ntfs                                     
/dev/sda5        2ad75afc-5ff2-4642-9d89-a89ca13c709f   ext4                                     
/dev/sda6        b6ad5208-f202-4dfa-8e46-622aae22b2cb   swap                                     
/dev/sda7        ab92fba8-5a1e-49e7-a307-eb542690f0f3   ext4       /projects                     

============================ "mount | grep ^/  output: ===========================

Device           Mount Point      Type       Options

/dev/sda5        /                ext4       (rw,errors=remount-ro)
/dev/sda7        /projects        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="IBM Client for e-business Windows XP v3.00" /noexecute=alwaysoff /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 2ad75afc-5ff2-4642-9d89-a89ca13c709f
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 2ad75afc-5ff2-4642-9d89-a89ca13c709f
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=2ad75afc-5ff2-4642-9d89-a89ca13c709f ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 2ad75afc-5ff2-4642-9d89-a89ca13c709f
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=2ad75afc-5ff2-4642-9d89-a89ca13c709f ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 421e5e981e5e8537
	drivemap -s (hd0) ${root}
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
UUID=2ad75afc-5ff2-4642-9d89-a89ca13c709f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=3ba3bb05-444a-4f5e-96bd-71dff385aafd none            swap    sw              0       0
UUID=b6ad5208-f202-4dfa-8e46-622aae22b2cb none            swap    sw              0       0

# /dev/sda7 
UUID=ab92fba8-5a1e-49e7-a307-eb542690f0f3 /projects               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
nandina:/storage1 /nandina/storage1 nfs rw,hard,intr 0 0
nandina:/storage2 /nandina/storage2 nfs rw,hard,intr 0 0
vanderbilt:/firethorn-nfs /vanderbilt nfs rw,hard,intr 0 0
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0

=================== sda5: Location of files loaded by Grub: ===================


  47.3GB: boot/grub/core.img
  47.3GB: boot/grub/grub.cfg
  47.3GB: boot/initrd.img-2.6.31-17-generic
  47.3GB: boot/vmlinuz-2.6.31-17-generic
  47.3GB: initrd.img
  47.3GB: vmlinuz
root@camellia:/home/mike#

---

### Post by Leppie on 2010-01-28
this part:
```
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same  drive in 
    partition #5 for /boot/grub.
```and this part:
```
sda1: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
```indicate that you have grub2 installed successfully into the mbr and there's no grub configuration files on your xp partition. you can safely delete the xp partition and add it to your current ubuntu system.

---

### Post by sandkernel on 2010-01-28
Thanks Leppie for the great reply

---

### Post by Leppie on 2010-01-28
> **sandkernel said:**
> Thanks Leppie for the great reply
you're welcome :)

---

### Post by sandkernel on 2010-01-29
> **Leppie said:**
> you're welcome :)

Worked like a charm - no issues. Thanks again.

---

