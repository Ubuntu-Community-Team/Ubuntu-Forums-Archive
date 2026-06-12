---
title: "How to boot by having 2 OSs?"
date: 2010-01-14
forum: General Help
---

### Post by talkingtree on 2010-01-14
Hi,

I have 2 OS on my computer, Window XP and Ubuntu, now I use Window XP, how do I make it so that I can change to boot from Ubuntu?

My motherboard is P7P55DLE Asus

---

### Post by sh4d0w808 on 2010-01-14
Theoretically U should be able to select the OS at boot time.

---

### Post by Kevbert on 2010-01-14
How did you install XP and Ubuntu ? Ubuntu first ?  Or did you install Ubuntu through Windows using Wubi ?

---

### Post by drs305 on 2010-01-14
We need to know if Ubuntu is the normal install or inside Windows (wubi).

We need to know which version of Grub you are using - Grug legacy or Grub 2. You can find out with this command "grub-install -v"

I have a link to making default changes in Grub 2 here:
[Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

But to avoid confusion and answer the above questions, follow this thread to run the boot info script and post the results here (use the # symbol as explained in the link):
[http://ubuntuforums.org/showthread.php?t=1291280]("http://ubuntuforums.org/showthread.php?t=1291280")

---

### Post by talkingtree on 2010-01-14
I installed Ubuntu then I installed XP. I didnt use Wubi.

Here's the data for Grub using liveCD (as I cannot get into Ubuntu), the terminal shows there's no such file for output?

```
 
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/Downloads/boot_info_script*.sh
bash: /home/ubuntu/Downloads/boot_info_script*.sh: No such file or directory ubuntu@ubuntu:~$ 

```

---

### Post by Leppie on 2010-01-14
to which location did you save the boot info script?
if you didn't save it to the desktop, you have to amend the location in the command.

---

### Post by talkingtree on 2010-01-14
oh rite, sorry about this, okay here it is the output for Grub

```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7c4e7c4e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   819,202,544   819,202,482   7 HPFS/NTFS
/dev/sda2         819,202,545 1,908,570,194 1,089,367,650   7 HPFS/NTFS
/dev/sda3       1,908,570,195 1,924,217,504    15,647,310   5 Extended
/dev/sda5       1,908,586,260 1,924,217,504    15,631,245  82 Linux swap / Solaris
/dev/sda4       1,924,217,505 1,953,520,064    29,302,560  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8032 MB, 8032092160 bytes
131 heads, 50 sectors/track, 2395 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6d916d91

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,192    15,687,679    15,679,488   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="D41C1FF71C1FD2FA" TYPE="ntfs" 
/dev/sda2: UUID="2658E03058E00103" LABEL="chuck" TYPE="ntfs" 
/dev/sda4: UUID="02f50b06-4d80-4b71-92ec-2a68692cf58f" TYPE="ext4" 
/dev/sda5: UUID="6a5bc8c6-3933-41d2-bf6d-a999326576b9" TYPE="swap" 
/dev/sdb1: LABEL="Transcend" UUID="59AB-FF62" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/Transcend type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 02f50b06-4d80-4b71-92ec-2a68692cf58f
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 02f50b06-4d80-4b71-92ec-2a68692cf58f
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=02f50b06-4d80-4b71-92ec-2a68692cf58f ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 02f50b06-4d80-4b71-92ec-2a68692cf58f
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=02f50b06-4d80-4b71-92ec-2a68692cf58f ro single 
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

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=02f50b06-4d80-4b71-92ec-2a68692cf58f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6a5bc8c6-3933-41d2-bf6d-a999326576b9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


 985.1GB: boot/grub/core.img
 985.1GB: boot/grub/grub.cfg
 985.1GB: boot/initrd.img-2.6.31-14-generic
 985.1GB: boot/vmlinuz-2.6.31-14-generic
 985.1GB: initrd.img
 985.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

---

### Post by mister_playboy on 2010-01-14
> **talkingtree said:**
> I installed Ubuntu then I installed XP. I didnt use Wubi.

Windows should always be installed first, since it will overwrite the MBR and erase any other bootloaders (such as GRUB) there.  MS doesn't want to play nice... ;)

---

### Post by Leppie on 2010-01-14
> **talkingtree said:**
> oh rite, sorry about this, okay here it is the output for Grub
you don't have grub installed in any mbr at the moment. you can install it to the mbr of sda booting with a livecd:
```
sudo mount /dev/sda4 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```
reboot and issue the following command to add xp to the boot menu:
```
sudo update-grub
```

---

### Post by drs305 on 2010-01-14
Here is a link to reinstalling Grub 2 on a dual boot system. Your linux parition for the commands is sda4.

[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by talkingtree on 2010-01-14
wow now it can boot up as 2 OSs, thanks alot guys!

---

