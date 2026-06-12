---
title: "left with 2 grub menus"
date: 2009-12-19
forum: General Help
---

### Post by dantibb on 2009-12-19
Hi,

After installing 9.10 from Wubi I have been left with 2 grubs.

I installed Ubuntu netbook remix 9.10 from a live USB on my dell netbook, and left the original windows XP as a dual boot accessible from grub.

In trying to get graphic acceleration to work, i killed my desktop. So I decided to install normal 9.10, this time using Wubi from the original install of XP.

Since then when turning on my netbook I get:

 first the original Grub which has ubuntu netbook remix (which has a bust desktop) and XP.
Then a choice between XP and Ubuntu (I assume this is a new grub/windows item as have never seen it before)
*Then* another grub with Ubuntu and XP which boots to normal 9.10 (non-netbook and working).

I really want to simplify this as my wife also uses this. How do I get this sorted? What I want is just the choice between Ubuntu and XP ( the middle stage above) and not the Grubs, though one grub would be fine.

I don't want to go around deleting grubs and the like without some advice as am worried will lose ability to boot.

Regards,

---

### Post by joes7 on 2009-12-19
Update GRUB.

OPEN A TERMINAL AND WRITE:
```

update-grub

```
YOU MUST BE LOGGED IN AS YOUR ROOT USER, FOR SAY "ROOT". I HOPE THIS HELPS :)!
[COLOR=Red]
[SIZE=6]JO-JO-JO! HAPPY M[/SIZE][/COLOR][SIZE=6][COLOR=DarkGreen]ERRY CHRISTMAS![/COLOR][/SIZE]

---

### Post by Leppie on 2009-12-19
Run the following commands from a terminal:
```
$sudo update-grub ##generate the grub.cfg configuration file
$sudo grub-install --recheck /dev/sda ##re-install grub2 to the mbr
```

Did you actually remove the wubi netbook installation in xp? If you haven't, then remove it and run the update-grub command.

---

### Post by dantibb on 2009-12-19
Hi,

Thanks for the reply, but hasn't helped.

I still get grub first of all with options of the 'broken' NBR and XP,
If I select XP, I then get 2 further options - XP or Ubuntu (this is not a grub screen I have ever seen).
If I select Ubuntu, I then get a new Grub with the working 9.10, XP and 'broken' NBR. 

How do I get rid of the first GRUB?
And what is the second menu I get? I have never seen it, but this is the first time i've installed via wubi.

Thanks!

---

### Post by dantibb on 2009-12-19
> Did you actually remove the wubi netbook installation in xp? If you haven't, then remove it and run the update-grub command.
Oh, and no, I left it in there as I plan on having a go at fixing it. Would you reccomend uninstalling? How easy is this?

---

### Post by Leppie on 2009-12-19
> **dantibb said:**
> Thanks for the reply, but hasn't helped.

what hasn't helped? please indicate what you did exactly, as this gives those who are trying to help you a better insight on what's going on.

If you want to fix the netbook install, then leave it be.

Could you please post your /boot/grub/grub.cfg (I believe in wubi installs the root is /host, so the complete path would be /host/boot/grub/grub.cfg)?

---

### Post by dantibb on 2009-12-20
Hi,
[FONT=monospace]
I tried
[/FONT]$sudo update-grub
$sudo grub-install --recheck /dev/sda 
[FONT=monospace]and it remained the same (as detailed above).

Here is my /boot/grub/grub.cfg (there is nothing in /host/[/FONT][FONT=monospace]boot/grub/grub.cfg[/FONT][FONT=monospace])

Please note - this is the second Grub I come to, and the install on SDA5 is the broken UNR. I can post the first one if required?


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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 9c2c50e52c50bc48
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 9c2c50e52c50bc48
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 9c2c50e52c50bc48
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 9c2c50e52c50bc48
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 9c2c50e52c50bc48
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 231b1215-9f43-43cf-9f75-1bcc287f0e73
    linux /boot/vmlinuz-2.6.31-16-generic root=UUID=231b1215-9f43-43cf-9f75-1bcc287f0e73 ro quiet splash
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 231b1215-9f43-43cf-9f75-1bcc287f0e73
    linux /boot/vmlinuz-2.6.31-16-generic root=UUID=231b1215-9f43-43cf-9f75-1bcc287f0e73 ro single
    initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 231b1215-9f43-43cf-9f75-1bcc287f0e73
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=231b1215-9f43-43cf-9f75-1bcc287f0e73 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 231b1215-9f43-43cf-9f75-1bcc287f0e73
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=231b1215-9f43-43cf-9f75-1bcc287f0e73 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

Thanks for all your help on this, it is greatly appreciated.
[/FONT]

---

### Post by Leppie on 2009-12-20
yes, please post the other grub.cfg as well.

---

### Post by dantibb on 2009-12-21
Here is the other grub.cfg:

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
search --no-floppy --fs-uuid --set 231b1215-9f43-43cf-9f75-1bcc287f0e73
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 231b1215-9f43-43cf-9f75-1bcc287f0e73
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=231b1215-9f43-43cf-9f75-1bcc287f0e73 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 231b1215-9f43-43cf-9f75-1bcc287f0e73
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=231b1215-9f43-43cf-9f75-1bcc287f0e73 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 231b1215-9f43-43cf-9f75-1bcc287f0e73
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=231b1215-9f43-43cf-9f75-1bcc287f0e73 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 231b1215-9f43-43cf-9f75-1bcc287f0e73
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=231b1215-9f43-43cf-9f75-1bcc287f0e73 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 9c2c50e52c50bc48
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

Thanks,

---

### Post by Leppie on 2009-12-21
what is the location of the 2nd grub you posted?

---

### Post by dantibb on 2009-12-21
it's on sda5(I think)

/media/231b1215-9f43-43cf-9f75-1bcc287f0e73/boot/grub

---

### Post by Leppie on 2009-12-21
can you still access the wubi install?
the thing you should do is boot into the wubi install and remove grub2:
```
$sudo apt-get purge grub2 grub-pc
```

---

### Post by dantibb on 2009-12-21
I do not seem to have grub2 installed:

daniel@ubuntu:~$ sudo apt-get purge grub2 grub-pc
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Package grub2 is not installed, so not removed
The following packages will be REMOVED
  grub-pc*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,753kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

I am currently in the WUBI install.

---

### Post by Leppie on 2009-12-21
> **dantibb said:**
> I do not seem to have grub2 installed:

daniel@ubuntu:~$ sudo apt-get purge grub2 grub-pc
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Package grub2 is not installed, so not removed
The following packages will be REMOVED
  grub-pc*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,753kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

I am currently in the WUBI install.

yes, you do have grub2 installed. grub2 consists of the packages grub-common and grub-pc.
try modifying the command to this:
```
$sudo apt-get purge grub-pc grub-common
```

---

### Post by dantibb on 2009-12-21
I ran
$sudo apt-get purge grub-pc grub-common 
[FONT=monospace]and removed all grub2 files,

but I still get the same experience booting.

How do I add the Wubi install to the first grub? Or remove the first one altogether?
[/FONT]

---

### Post by Leppie on 2009-12-21
boot into the non wubi ubuntu, and run this command:
```
$sudo grub-install --recheck /dev/sda
```

---

### Post by dantibb on 2009-12-21
I ran 
sudo grub-install --recheck /dev/sda
[FONT=monospace]and it gave 

(hd0) /dev/sda

as the last line (I don't have the rest of the output - there is no desktop available on that install, so not easy to copy and paste output!)

and still no change to boot sequence.
[/FONT]

---

### Post by Leppie on 2009-12-21
> **dantibb said:**
> I ran 
sudo grub-install --recheck /dev/sda
[FONT=monospace]and it gave 

(hd0) /dev/sda

as the last line (I don't have the rest of the output - there is no desktop available on that install, so not easy to copy and paste output!)

and still no change to boot sequence.
[/FONT]

i am confused now. i thought you wrote that the wubi install was the broken one?

do you still have a livecd at hand?

---

### Post by dantibb on 2009-12-21
> **Leppie said:**
> i am confused now. i thought you wrote that the wubi install was the broken one?

do you still have a livecd at hand?

Sorry for confusion, Wubi is working, the UNR from a live usb is broken.

Yes, I still have the live USB.

---

### Post by Leppie on 2009-12-21
could you run this command and post the resulting text file:
```
cd ~/Desktop \
&& wget 'http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.41/boot_info_script041.sh/download' \
&& chmod 755 boot_info_script041.sh \
&& sudo ./boot_info_script041.sh
```

---

### Post by meierfra. on 2009-12-21
Instead of getting the boot info script via "wget", I suggest to download it to the Desktop from
[URL="http://sourceforge.net/projects/bootinfoscript/"]
http://sourceforge.net/projects/bootinfoscript/[/URL]

This makes sure that you always get the newest version.  (boot_info_script042.sh has improved support for Wubi)

(See [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280) for detailed instruction)

---

### Post by Leppie on 2009-12-21
i'll keep that in mind, thanks :)

---

### Post by dantibb on 2009-12-21
here is results - this was done booted via live usb,

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk

sda3: _________________________________________________________________________

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

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa42d04a3

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325   157,565,519   157,485,195   7 HPFS/NTFS
/dev/sda3         157,565,520   312,576,704   155,011,185   5 Extended
/dev/sda5         157,565,583   306,616,589   149,051,007  83 Linux
/dev/sda6         306,616,653   312,576,704     5,960,052  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2017 MB, 2017460224 bytes
71 heads, 17 sectors/track, 3264 cylinders, total 3940352 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000642db

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *              1     3,940,351     3,940,351   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="89b61608-3b68-42e2-8c62-1752e2054ab6" TYPE="ext3" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: UUID="9C2C50E52C50BC48" TYPE="ntfs" 
/dev/sda5: UUID="231b1215-9f43-43cf-9f75-1bcc287f0e73" TYPE="ext4" 
/dev/sda6: UUID="8d36be5b-1776-48b5-892f-c058b4347465" TYPE="swap" 
/dev/sdc1: UUID="4540-D782" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sdc1 on /cdrom type vfat (rw)
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


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

================================== sda2Wubi: ==================================

Operating System: "Ubuntu 9.10"

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

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
search --no-floppy --fs-uuid --set 231b1215-9f43-43cf-9f75-1bcc287f0e73
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 231b1215-9f43-43cf-9f75-1bcc287f0e73
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=231b1215-9f43-43cf-9f75-1bcc287f0e73 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 231b1215-9f43-43cf-9f75-1bcc287f0e73
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=231b1215-9f43-43cf-9f75-1bcc287f0e73 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 231b1215-9f43-43cf-9f75-1bcc287f0e73
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=231b1215-9f43-43cf-9f75-1bcc287f0e73 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 231b1215-9f43-43cf-9f75-1bcc287f0e73
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=231b1215-9f43-43cf-9f75-1bcc287f0e73 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 9c2c50e52c50bc48
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
UUID=231b1215-9f43-43cf-9f75-1bcc287f0e73 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8d36be5b-1776-48b5-892f-c058b4347465 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  80.6GB: boot/grub/grub.cfg
  80.6GB: boot/initrd.img-2.6.31-14-generic
  80.6GB: boot/initrd.img-2.6.31-16-generic
  80.6GB: boot/vmlinuz-2.6.31-14-generic
  80.6GB: boot/vmlinuz-2.6.31-16-generic
  80.6GB: initrd.img
  80.6GB: initrd.img.old
  80.6GB: vmlinuz
  80.6GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

--------------------------------

what I am having difficulty understanding in all this is the partition wubi ubuntu 9.10 is on, or is it sharing sda2 with xp?

hope this makes sense to you.

---

### Post by meierfra. on 2009-12-21
> or is it sharing sda2 with xp?
Yes.


To solve your problem, you have a couple of options:


1)  Add Wubi to your grub menu for remix 9.10 and delete Wubi from the XP boot menu.  This way you will only have one grub menu and no other boot menus.


2)  Install a windows type MBR in /dev/sda and  hide your Wubi grub menu (and add remix 9.10 to the XP boot menu) . This way you will only have the XP boot menu and no other boot menus.

If you are planning to keep your Ubuntu remix 9.10 I would recommend option 1)

Let me know which option you prefer and I can give you detailed instruction.

---

### Post by dantibb on 2009-12-22
Hi

option 1 sounds good - being able to select wubi and xp from the first (and only) grub. Can you also advise on moving xp up the grub order so it is first on the list?

Many thanks.

---

### Post by meierfra. on 2009-12-22
Boot into Wubi and open a terminal.
Mount your Remix partition and move to the grub.d directory on the Remix via
```
sudo mount /dev/sda5 /mnt
cd /mnt/etc/grub.d
```

Open the file /mnt/etc/grub.d/40_custom:

```
gksudo gedit  custom_40
```

Add the following to the end of the file
```
menuentry "Wubi" {
	insmod ntfs
	set root=(hd0,2)
        loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /vmlinuz root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /initrd.img
}
```


 Save the custom_40 file. 

To move XP to the top of the list:

```
sudo mv {30,08}_os-prober 
```

To make this changes effective, boot into your Ubuntu Remix and  run

```
sudo update-grub
```

Reboot, XP should be the first item on the first Grub menu, and you should have an item for Wubi at the end of the menu.

Boot into Wubi from the first menu Grub menu, mount your XP partition and open the file boot.ini (Don't do this step if you can't boot into Wubi from the first grub menu)

```
sudo mount /dev/sda2 /mnt
sudo nano /mnt/boot.ini
```

(Using nano instead of gedit, it's better for dos-style linebreaks)

Change "timeout 30" to "timeout 0".
Delete the line  "C:\wubildr.mbr = "Ubuntu".
Save the file (look for the instruction on the bottom of the terminal, "^" means the "ctrl" key)

Reboot and choose XP at the first grub menu. You should boot directly into XP.

---

### Post by dantibb on 2009-12-24
Thankyou for this - it has worked.

I followed all the instructions above and the boot process is nice and smooth.

Can I ask a couple of questions for my own knowledge -

- What did sudo mv {30,08}_os-prober command do?

- If I did decide to uninstall Remix ubuntu, would this have any impact on the grub set up, and how does the netbook know to look at sda5 for the first grub?

Many thanks for your help again, if you know of any online tutorials that might help my knowledge of grub etc let me know!.

Merry Xmas.

---

### Post by meierfra. on 2009-12-24
> What did sudo mv {30,08}_os-prober command do?

"mv {30,08}_os-prober" is a the same as  "mv 30_os_prober 08_os_prober". It moves (renames) the file "30_os_prober" to "08_os_prober".  "update-grub" processes the files in /etc/grub.d" in lexicographic order.  Now XP  will be detected by "08_os_prober" and then Ubuntu by "10_linux. So XP is placed on the grub_menu before Ubuntu.  

> how does the netbook know to look at sda5 for the first grub?


From the boot_info_script:

> Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive in partition #5 for /boot/grub.


Your MBR (the first few sectors of your hard drive) contains instruction to look at /boot/grub on /dev/sda5 for the files necessary for Grub 2 to boot your computer.


> If I did decide to uninstall Remix ubuntu, would this have any impact on the grub set up,

You won't be able to boot, since Grub 2 is still installed in the MBR.
So before you uninstall the Remix you should do one of following

**Solution 1:  Place the Grub Folder on your XP Partition**

```
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
cd /mnt/boot/grub
sudo cp /boot/grub/grub.cfg .  [COLOR="Red"]#note the  period[/COLOR]
gedit grub.cfg
```

Remove the menuentries for your Remix.  

**Solution 2: Install a Windows type MBR and add Wubi to your Windows boot loader.**

```
sudo apt-get install lilo  [COLOR="Red"]#Ignore the message displayed, just press "enter"[/COLOR]
sudo lilo -M /dev/sda mbr
sudo mount /dev/sda2 /mnt
nano /mnt/boot.ini

```

Change "timeout 0" to "timeout 30", or whatever timeout you would like.
Add the  line "C:\wubildr.mbr = "Wubi" to the end of the file (replace "Wubi" by any title of your choosing)

---

