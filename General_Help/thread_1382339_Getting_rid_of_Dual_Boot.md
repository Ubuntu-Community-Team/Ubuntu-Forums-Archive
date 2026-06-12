---
title: "Getting rid of Dual Boot"
date: 2010-01-15
forum: General Help
---

### Post by mikeody on 2010-01-15
On one of my PCs I am dual booting Windows and Karmic [2 hard drives Windows on one, Karmic on the other].
I now dont need the windows OS but am unsure how to get rid of it without upsetting GRUB.
I would want to physically remove the windows hard drive and let Karmic boot up when I switch on.
Can someone advise please ?
Thanks

---

### Post by adam814 on 2010-01-15
Hrmm...where did you install GRUB?  As long as it's installed to the MBR of the drive with Karmic it seems like you could safely remove the Windows drive and the Windows entries would get removed the next time you ran update-grub.

Maybe post the results of the boot info script? [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Leppie on 2010-01-15
as adam814 stated, this depends on the exact setup of your system.
could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt so we can examine your system in a better way?

---

### Post by mikeody on 2010-01-15
Thanks for that. This issue stems from a problem I posted elsewhere in that I couldnt access the Windows OS via GRUB. I have since decided to get rid of the Windows OS entirely. And thats what I am trying to do now.

I have tried disconnecting the Windows Drive and setting the first boot disk to The Karmic Disk.

I got the message to 'insert a bootable drive'! Interesting - presumably something on the Karmic Drive is pointing at the [disconnected] Windows Drive in order to boot GRUB.

The results of infoscript are :

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x70527052

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,108,029    78,107,967   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfe35fe35

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   300,511,889   300,511,827  83 Linux
/dev/sdb2         300,511,890   312,576,704    12,064,815   5 Extended
/dev/sdb5         300,511,953   312,576,704    12,064,752  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="0C2C5EF22C5ED674" TYPE="ntfs" 
/dev/sdb1: UUID="6c203b65-3340-49a4-a323-cdcc06ad05ae" TYPE="ext4" 
/dev/sdb5: UUID="b6a485c2-3625-412f-a1fd-6401829e0263" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mike/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mike)


=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 6c203b65-3340-49a4-a323-cdcc06ad05ae
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
  set timeout=0
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
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6c203b65-3340-49a4-a323-cdcc06ad05ae
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=6c203b65-3340-49a4-a323-cdcc06ad05ae ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6c203b65-3340-49a4-a323-cdcc06ad05ae
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=6c203b65-3340-49a4-a323-cdcc06ad05ae ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6c203b65-3340-49a4-a323-cdcc06ad05ae
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=6c203b65-3340-49a4-a323-cdcc06ad05ae ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6c203b65-3340-49a4-a323-cdcc06ad05ae
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=6c203b65-3340-49a4-a323-cdcc06ad05ae ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6c203b65-3340-49a4-a323-cdcc06ad05ae
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=6c203b65-3340-49a4-a323-cdcc06ad05ae ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6c203b65-3340-49a4-a323-cdcc06ad05ae
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=6c203b65-3340-49a4-a323-cdcc06ad05ae ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6c203b65-3340-49a4-a323-cdcc06ad05ae
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6c203b65-3340-49a4-a323-cdcc06ad05ae ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 6c203b65-3340-49a4-a323-cdcc06ad05ae
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6c203b65-3340-49a4-a323-cdcc06ad05ae ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
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
	search --no-floppy --fs-uuid --set 0c2c5ef22c5ed674
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=6c203b65-3340-49a4-a323-cdcc06ad05ae /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=b6a485c2-3625-412f-a1fd-6401829e0263 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

---

### Post by adam814 on 2010-01-15
Ok, your setup is a little more complicated than I would have imagined.  It shows you have LILO installed on the MBR of /dev/sda and GRUB on the MBR of /dev/sdb.  Are you chainloading GRUB from LILO?

I'm guessing maybe your BIOS looks for the boot flag on the partitions?  You could try setting the boot flag on your Ubuntu partition (either in GParted or fdisk) to see if it will boot without the Windows drive in place.

---

### Post by mikeody on 2010-01-15
Thanks Adam,
The LILO on the Windows Disk is a throwback from an attempted fix for being unable to boot Windows via GRUB. [What happened was I installed Windows 7 over top of XP AFTER Karmic and it was all downhill from there !].
Sorry about being rather ignorant but you are going to have to explain things in a bit more detail vis.

Are you chainloading GRUB from LILO? I really have no idea ! IF I AM "CHAINLOADING', WHILST IT SOUNDS EXCITING IT WSNT INTENTIONAL !

I'm guessing maybe your BIOS looks for the boot flag on the partitions? You could try setting the boot flag on your Ubuntu partition (either in GParted or fdisk) to see if it will boot without the Windows drive in place.
NEED SOME DIRECTIONS ON THIS PLEASE.

Thanks Adam

---

### Post by mikeody on 2010-01-15
Me again Adam.
I managed to set a boot flag on the Karmic drive but same result. There were no flags set at all.
Things work OK in that I have set the GRUB delay to zero so whenever I start up I get straight into Karmic but the ex Windows hard drive has to be in place for that to work.

---

### Post by adam814 on 2010-01-15
Ok, probably the easiest method then is to boot an Ubuntu LiveCD.  Go to the "Try Ubuntu with no changes to your computer option.  Go to System > Administration > GParted.

Right-Click /dev/sdb1 and go to "Manage Flags".  Check the box for "boot".  Then shutdown normally and try removing the Windows drive and see if you still get the same error message or it boots.

---

### Post by meierfra. on 2010-01-15
Edit: I hadn't seen your last post, when I posted this.

Lilo is only installed in the MBR (its works just like a regular Window MBR)

You can do anything you want to do your Windows  hard drive and you still we be able to boot Ubuntu. But some bios require you to have a boot flag somewhere. So follow adam814 advice.

PS:  Could you try my last suggestion in your other thread? Even if you don't want Windows anymore, other people might have the same problem and it would be good to know if renaming "boot" will cure your problem. 
Thanks

---

### Post by adam814 on 2010-01-15
You might need to reinstall GRUB.  According to the script it's looking for /boot/core.img on /dev/sda1, which is your Windows partition.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")
At any rate it can't hurt.

---

### Post by mikeody on 2010-01-15
No problem meierfra,
Will have another look at that.
Mike

---

### Post by mikeody on 2010-01-15
All sorted guys. No need to take drastic measures.
meierfra's rename boot file option worked. See other postings in Installation and Upgrades.
Thanks everyone for your input.

---

### Post by meierfra. on 2010-01-16
Just for anybody who is curious. Here is the link to the other thread:

[http://ubuntuforums.org/showthread.php?t=1379592](http://ubuntuforums.org/showthread.php?t=1379592)

---

