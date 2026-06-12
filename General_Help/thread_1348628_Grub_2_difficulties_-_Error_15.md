---
title: "Grub 2 difficulties - Error 15"
date: 2009-12-07
forum: General Help
---

### Post by gizzacroggy on 2009-12-07
Hello,

I installed Ubunt9 9.10 alongside my existing Vista last week. It worked fine for two days and then could no longer find bootable device.

I have tried many solutions.

Super Grub Disk - cannot repair it - returns an error 15 message

I can though enter into Ubuntu with SGD.

I have tried following instructions from many different forums and no joy,

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)
 
sudo grub - command not found

[URL="https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD"]https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD
[/URL]I get as far as update-grub and it comes back at me with 

"Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!"

[http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/)
Here when i open menu.lst nothing is displayed.


I am on a steep learning curve, enjoying it, but could really do with some help to understand what is going on and understand what i need to do to fix it.

Thanks

G x

---

### Post by namok on 2009-12-07
In Grub2 file ''/boot/grub/menu.lst'' it has been replaced by ''/boot/grub/grub.cfg''. Read here: [The Grub 2 Guide.]("http://ubuntuforums.org/showthread.php?t=1195275")
If you want to restore Grub2 in MBR use this: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) (scroll to: How to restore the Ubuntu grub bootloader (9.10 and beyond))

---

### Post by gizzacroggy on 2009-12-08
Thanks for the suggestions.

I gave it ago, following the instructions below. After it told me that all was succesfully installed but when I reboot I get the same message - no bootable device.

Any other suggestions? 


G 

sudo mkdir /media/sda5
 sudo mount /dev/sda5 /media/sda5
sudo grub-install --root-directory=/media/sda5 /dev/sda

---

### Post by oldfred on 2009-12-08
Error 15 is supposedly mixed versions of grub. Did you reinstall work correctly?

It is very coincidental that your commands match the sample commands exactly using sda5. You are supposed to use the sdax that is where your install is, unless it was sda5?

---

### Post by gizzacroggy on 2009-12-08
I used sda5 as that is my linux partition, according to fdisk.

---

### Post by oldfred on 2009-12-08
No one else can see your grub.cfg since you posted that in someone else's thread which makes it difficult for others to help. I am mostly at a loss, but in reviewing you results.lst it shows mount issues.

My entry:
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)

your entry:
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)

The none says to me that it is not mounting correctly and grub is finding that issue and not letting you boot.

---

### Post by gizzacroggy on 2009-12-08
Hi,
You are right, I should have just started my own thread in the first place.

Here is the information i posted elsewhere ( on someone else&#347; thread who had a similiar problem.) in the hope that might help the detective search.


sudo xxd  -l  2 -p /dev/sda         = eb63
sudo xxd -s 1049 -l 2 -p /dev/sda   = ffff
sudo xxd  -l  2 -p /dev/sdb         = no medium found
sudo xxd -s 1049 -l 2 -p /dev/sdb   = no medium found


Here is my fdisc information in case useful.
gizzacroggy@gizzacroggy-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a7c51dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1918       23354   172183732    7  HPFS/NTFS
/dev/sda4           23355       30401    56605027+   5  Extended
/dev/sda5           23355       30107    54243441   83  Linux
/dev/sda6           30108       30401     2361523+  82  Linux swap / Solaris


```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sda5 and 
                       looks at sector 376389137 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #5 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1a7c51dd

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3    *     30,801,920   375,169,383   344,367,464   7 HPFS/NTFS
/dev/sda4         375,182,010   488,392,064   113,210,055   5 Extended
/dev/sda5         375,182,073   483,668,954   108,486,882  83 Linux
/dev/sda6         483,669,018   488,392,064     4,723,047  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: UUID="9E98822C9882034F" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="EE94845794842465" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="315caa64-ddbe-4f7e-8dfc-eb0b23f5d405" TYPE="ext4" 
/dev/sda6: UUID="357af9e8-2c9d-40bb-a1bd-3e82feb3c024" TYPE="swap" 

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
search --no-floppy --fs-uuid --set 315caa64-ddbe-4f7e-8dfc-eb0b23f5d405
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
  set timeout=15
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
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 315caa64-ddbe-4f7e-8dfc-eb0b23f5d405
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=315caa64-ddbe-4f7e-8dfc-eb0b23f5d405 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 315caa64-ddbe-4f7e-8dfc-eb0b23f5d405
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=315caa64-ddbe-4f7e-8dfc-eb0b23f5d405 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set ee94845794842465
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
UUID=315caa64-ddbe-4f7e-8dfc-eb0b23f5d405 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=357af9e8-2c9d-40bb-a1bd-3e82feb3c024 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 192.0GB: boot/grub/grub.cfg
 192.0GB: boot/initrd.img-2.6.31-14-generic
 192.0GB: boot/vmlinuz-2.6.31-14-generic
 192.0GB: initrd.img
 192.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb
``````

```

---

### Post by Leppie on 2009-12-08
Try the following after booting with a live cd:
```
$sudo mkdir -p /mnt/temp
$sudo mount /dev/sda5 /mnt/temp
$sudo chroot /mnt/temp
$sudo grub-install --recheck /dev/sda
$sudo update-grub
```

---

### Post by gizzacroggy on 2009-12-08
Just a quick question - after chrooting I get the root prompt - do i need to leave that to later use sudo grub-install?


```
ubuntu@ubuntu:~$ sudo mkdir -p /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt/temp
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# sudo grub-install --recheck /dev/sda
sudo: unable to resolve host ubuntu
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
root@ubuntu:/# grub-install --recheck /dev/sda
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
root@ubuntu:/#
``````

```

---

### Post by Leppie on 2009-12-08
The chroot command changes the root of your filesystem to the directory passed onto the command. This is needed in order to re-install grub correctly. If you don't use the chroot command, grub will try to install using the /boot directory on the live cd (which most probably isn't very useful for your grub re-install).

Edit:
It actually looks like grub-install isn't able to identify your filesystem type.
Try to change to the following:
```
$sudo mkdir -p /mnt/temp
$sudo mount -t ext4 /dev/sda5 /mnt/temp  ##ext4 is the default filesystem type for Karmic, if you changed it during installation change the ext4 part to whatever filesystem type you chose during installation
$sudo chroot /mnt/temp
$sudo grub-install --recheck /dev/sda
$sudo update-grub
```

---

### Post by oldfred on 2009-12-08
You still seem to be having troubles even with the chroot not identifying everything. I just saw leppies post but I was going to also suggest as long as you have chrooted into your system to try some updates.

sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain you mounted the correct partition).
[COLOR=DarkRed]apt-get update
apt-get upgrade[/COLOR]
#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

The red are the only additonal commands over what leppie suggested. adn he may be more correct on the file type issue.

---

### Post by gizzacroggy on 2009-12-08
```
ubuntu@ubuntu:~$ sudo mkdir -p /mnt/temp
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda5 /mnt/temp
mount: /dev/sda5 already mounted or /mnt/temp busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt/temp
ubuntu@ubuntu:~$ sudo umount /dev/sda5
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda5 /mnt/temp
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# grub-install /dev/sda
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
root@ubuntu:/# 


```

I can't use the recheck function when in chroot. and if i am learning right, being in root just means you don't have to use sudo.

---

### Post by Leppie on 2009-12-08
> **gizzacroggy said:**
> I can't use the recheck function when in chroot. and if i am learning right, being in root just means you don't have to use sudo.

Sorry, I did not count on you still being in the system without rebooting. If you try to mount with different options, you need to unmount first:
```
$sudo umount /mnt/temp
```

After that you can remount the partition with the new option.

And the error is not caused by chroot, but after chrooting you can cd to /boot and see if the grub directory is there.


Edit:
must be cos I'm getting tired... sudo isn't recognized properly after chrooting, but I suspect it's because the grub prober cannot determine the filesystem type.

---

### Post by gizzacroggy on 2009-12-08
Hello,

Following Leppies instructions I can only get as fas as grub-install

```
gizzacroggy@gizzacroggy-laptop:~$ sudo mkdir -p /mnt/temp
gizzacroggy@gizzacroggy-laptop:~$ sudo mount -t ext4 /dev/sda5 /mnt/temp
gizzacroggy@gizzacroggy-laptop:~$ sudo chroot /mnt/temp
root@gizzacroggy-laptop:/# grub-install /dev/sda
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
root@gizzacroggy-laptop:/# ^C

```

I followed Oldfred&#347; suggestions. Only problem is that when i got to umount it told my device was busy. Trying not to bother you with every little question I looked on forums and found out about fuser. I typed (from what i remember - i cant find the forum thread that guided me)
sudo fuser -km /mnt/dev
and then my screen went blank with just a cursor! I had to power off and reboot. Problem with booting continues. I hope I didnt do any damage with this fuser -km command.

So i never managed to umount before rebooting. would this effect the success of the commands i did, oldfred?

I am getting tired too, thank you so much for your time and effort.

I have just looked in /media/OS/boot and grub is not in there. 

G x

---

### Post by oldfred on 2009-12-08
Are we going backwards. The results.txt showed /boot/grub with the correct files. It should not be missing.

I just know they recommend unmounting and do not know if then the file system may need a file check which should only be done to an unmounted partition. From the liveCD you should be able to 
sudo fskc.ext3 /dev/sda5  or
sudo fskc.ext4 /dev/sda5 if it is ext4 (I forget)

---

### Post by gizzacroggy on 2009-12-09
I just rerun a boot info script.

It does not tell me at the very beginning that I have Grub 1.95 installed in the MBR of /dev/sda
  My earlier boot inforscript did tell me this. 

It does however tell me it is installed in sda5.

 ```


sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sda5 and 
                       looks at sector 376389137 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #5 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab
```

---

### Post by namok on 2009-12-09
Do you tried to start Ubuntu using [Super Grub Disk]("http://prdownload.berlios.de/supergrub/sgd_cdrom_1.21.iso.gz") or [CLI or Rescue Mode.]("https://help.ubuntu.com/community/Grub2#Using CLI to Boot") Then you can reinstall grub within Ubuntu.

---

### Post by gizzacroggy on 2009-12-09
I do indeed get in to Ubuntu with Superdisk. I was pondering whether that might have worsened the problem as someone earlier mentioned that superdisk is not updated to work with Grub2 and ubuntu 9.10. and so maybe it tried to install some older grub files.

I followed install grub from within ubuntu instrutions here [URL="https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"]

https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows


[/URL]```
izzacroggy@gizzacroggy-laptop:~$ sudo mkdir /mnt/linux
gizzacroggy@gizzacroggy-laptop:~$ sudo mount /dev/sda5 /mnt/linux
gizzacroggy@gizzacroggy-laptop:~$ cd /mnt/linux/sbin
gizzacroggy@gizzacroggy-laptop:/mnt/linux/sbin$ sudo ./grub
sudo: ./grub: command not found

```

Yesterday I also tried [METHOD 2 - Copy GRUB 2 Files from the Installed Partition]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")It told me it succesfully installed grub but when i rebooted i had same problem.

Today I cant use this method as my grub folder is no longer here. /media/OS/boot, also the reason for the above error.

So first step I guess would be getting that back in that folder?

---

### Post by namok on 2009-12-09
You have to mount the partition only when you start the livecd.

If you want to install grub2 in MBR within Ubuntu write in terminal:
```
sudo grub-install /dev/sda
``` Look here:[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html")(scroll down 'How to install, update and repair GRUB')

---

### Post by ranch hand on 2009-12-09
If this is a clean install of 9.10, rather than an upgrade, I would chroot in to the bugger from your live CD and remove "grub-pc" and grub-common".

Then install "grub-pc" and "grub-common".

I think this may help.  Your grub, to me, seems like it is not behaving as designed.  I think it is corrupted in some way.

If you can boot directly using SGD that would be easier.  I would not use it again with grub2.  I do not believe that it is really ready for that and may be the cause of part or your trouble.

---

### Post by gizzacroggy on 2009-12-09
Thanks ranchhand. I tried

sudo mount /dev/sda5 /mnt
sudo mount --bind /dev/mnt/dev
sudo chroot /mnt
apt-get remove grub-pc
apt-get remove grub-common.
apt-get install grub-pc

I got the following - does this tell us something new?

```

root@gizzacroggy-laptop:/# apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt4-opengl libqt4-assistant libqt4-test libqt4-dbus libqt4-core
  libqt4-gui libqtcore4 libqt4-svg libqt4-xml libqt4-network libqt4-designer
  libqtgui4 libqt4-script libaudio2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  grub-common
Suggested packages:
  multiboot-doc grub-emu desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 13 not upgraded.
Need to get 0B/1,428kB of archives.
After this operation, 4,170kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package grub-common.
(Reading database ... 114322 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.97~beta4-1ubuntu4.1_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.97~beta4-1ubuntu4.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for sreadahead ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up grub-common (1.97~beta4-1ubuntu4.1) ...

Setting up grub-pc (1.97~beta4-1ubuntu4.1) ...
sed: warning: failed to get security context of /tmp/grub.4apZ2WOGV2: No data availablesed: warning: failed to get security context of /tmp/grub.4apZ2WOGV2: No data availablesed: warning: failed to get security context of /tmp/grub.4apZ2WOGV2: No data availablesed: warning: failed to get security context of /tmp/grub.4apZ2WOGV2: No data availablegrub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
grub-probe: error: cannot find a device for /.

dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@gizzacroggy-laptop:/# 

```

---

### Post by oldfred on 2009-12-09
Did you copy commands or type them, this looks like it is missing a space?

sudo mount --bind /dev/mnt/dev

---

### Post by ranch hand on 2009-12-09
Try that again but use this for a template;
```

sudo mkdir /mnt/Daily-root
sudo mount /dev/sda13 /mnt/Daily-root/
sudo mount -o bind /proc /mnt/Daily-root/proc
sudo mount -o bind /dev /mnt/Daily-root/dev
sudo mount -o bind /dev/pts /mnt/Daily-root/dev/pts
sudo mount -o bind /sys /mnt/Daily-root/sys
sudo cp /etc/resolv.conf /mnt/Daily-root/etc/resolve.conf
sudo chroot /mnt/Daily-root /bin/bash

```
Where I have "Daily-root" you will have to put your partition (mine are labeled and I get better results with chrooting that way.

The above is what I am running every day as;
```

#!/bin/sh

sudo mkdir /mnt/Daily-root
sudo mount /dev/sda13 /mnt/Daily-root/
sudo mount -o bind /proc /mnt/Daily-root/proc
sudo mount -o bind /dev /mnt/Daily-root/dev
sudo mount -o bind /dev/pts /mnt/Daily-root/dev/pts
sudo mount -o bind /sys /mnt/Daily-root/sys
sudo cp /etc/resolv.conf /mnt/Daily-root/etc/resolve.conf
sudo chroot /mnt/Daily-root /bin/bash

fi

```
as a script to chroot to another one of my 10.04-testing installs to update.

It does work and it mounts the stuff that you are not able to write to because it is not mounted.

---

### Post by gizzacroggy on 2009-12-09
I thing i copied it from the page i got it from. 

```
gizzacroggy@gizzacroggy-laptop:~$ sudo mount /dev/sda5 /mnt
gizzacroggy@gizzacroggy-laptop:~$ sudo mount --bind /dev/mnt/dev
mount: can't find /dev/mnt/dev in /etc/fstab or /etc/mtab

```Now when I try it it doesnt work.

I am going away for work in about an hour until at least sunday and maybe all of next week so will have to put this on pause till I get back. Thanks for the help so far, and fingers crossed we can get it resolved when i get back before christmas.


EDIT
i just tried your latest selection.

sudo mkdir /mnt/Daily-root
sudo mount /dev/sda5 /mnt/Daily-root/
sudo mount -o bind /proc /mnt/Daily-root/proc
sudo mount -o bind /dev /mnt/Daily-root/dev
sudo mount -o bind /dev/pts /mnt/Daily-root/dev/pts
sudo mount -o bind /sys /mnt/Daily-root/sys
sudo cp /etc/resolv.conf /mnt/Daily-root/etc/resolve.conf
sudo chroot /mnt/Daily-root /bin/bash
apt-get remove grub-pc
apt-get remove grub-common
apt-get install grub-pc
apt-get install grub-common

This time it did install grub-pc but when installing grub common it told me i already had the newest version even though the remove was succesful.

I tried rebooting but no joy.

G x

---

### Post by Leppie on 2009-12-09
And can you reinstall grub to your mbr?
```
sudo mkdir /mnt/Daily-root
sudo mount /dev/sda5 /mnt/Daily-root/
sudo mount -o bind /proc /mnt/Daily-root/proc
sudo mount -o bind /dev /mnt/Daily-root/dev
sudo mount -o bind /dev/pts /mnt/Daily-root/dev/pts
sudo mount -o bind /sys /mnt/Daily-root/sys
sudo cp /etc/resolv.conf /mnt/Daily-root/etc/resolve.conf
sudo chroot /mnt/Daily-root /bin/bash
sudo grub-install --recheck /dev/sda
sudo update-grub
```

---

### Post by ranch hand on 2009-12-09
I can do anything that I know how to do on the CLI, which I admit is limited, but I change the the OS I am using as boot/root quite often just to make sure they are all working.  I was using Daily and change to Lounge (a 9.10>10.04 upgrade) yesterday using that same script for that partition.  I had changed to Daily from a 9.10 OS using that script.

It comes in handy.  I had trouble (noob) getting the script to work, still not sure why.

Just entering the commands, one at a time, in terminal works fine too.

I fine it is easier, for me, to get things right if I label my partitions.  Another thing I am not sure why works.

Geeze what a noob.  And a grumpy geezer to boot.

---

### Post by Leppie on 2009-12-09
Grub seems to be perpetually in beta release, which probably makes it more difficult to predict it's behavior on each system.

Not sure why this system is behaving like this, it's almost like some folders were corrupted.

---

### Post by ranch hand on 2009-12-09
Grub has been updated in 10.04-testing to grub1.97.  I am not sure why it has not made it to 9.10.

The main differences that I have seen is that "update-grub" does not work.  It was left in for "comfort" as it is a grub-legacy command and has been slated for removal in the final all along.  If you need t odo that job in the final the command is "grub-mkconfig".

The other difference is quite noticable.  It is the result of running "grub-config".  Instead of the rather brief info you got with "update-grub" "grub-mkconfig" displays the whole /boot/grub/grub.cfg file.  I like it.

---

### Post by Leppie on 2009-12-09
AFAIK Karmic ships with grub2 by default (my live cd installed grub2).

I actually like the update-grub script, I modified the grub.d scripts to customize my menu. update-grub gives me confirmation of the scripts working properly.

---

### Post by ranch hand on 2009-12-09
I have not tried it on any of my 9.10 installs,but enabling "backports may get the update quicker.  I really do not know why it has not been upgraded to the final of 1.97.

You might be able to tell from the link in my sig that I am quite a fan of grub2.  We all had some major doubts when 9.10-testing-alpha2 hit us.  I put another install on my test drive just to screw with grub2.  It would not boot.  I had / on sda and /home on sdb.  Just could not handle it.  I put on another install just on sda and it booted fine and picked out the first one and booted it fine.

It was kind of a rough ride for a while.  But we all kind of grew up with it and most of us decided we liked it.  Some did not but that is folks.  They are who they are (thank god we are not all alike).

I have my main drive booting from PhatDebian (a lenny respin using the 2.6.30 kernel so it has ext4 support).  I installed grub1.96 from the Debian repos on it and it boots to versions of 9.04 and Lenny and, of coarse itself.

If you like grub2 (I think it is better) and you have a 9.04 install grub1.96 is in the repo there.

I may just cheat on my 9.10 installs and enable which ever repo grub is in from Lucid just long enough to get grub1.97.

---

### Post by gizzacroggy on 2009-12-19
Hello,

Back at the computer and ready to try and fix this wee problem.

Ranch-hand: I tried your latest suggestion. Several few commands do not function, i tried to adapt them,  

sudo mkdir /mnt/Daily-root
sudo mount /dev/sda5 /mnt/Daily-root/
sudo mount -o bind /proc /mnt/Daily-root/proc
sudo mount -o bind /dev /mnt/Daily-root/dev  - # /dev not a block device

sudo mount -o bind /dev/pts /mnt/Daily-root/dev/pts
sudo mount -o bind /sys /mnt/Daily-root/sys
sudo cp /etc/resolv.conf /mnt/Daily-root/etc/resolve.conf
sudo chroot /mnt/Daily-root /bin/bash
sudo grub-install --recheck /dev/sda  # recheck is invalid command. i used apt-get install grub

sudo update-grub # update-grub is invalid command.
Where should we go from here?

G x

---

### Post by Leppie on 2009-12-19
> **gizzacroggy said:**
> sudo grub-install --recheck /dev/sda  # recheck is invalid command. i used apt-get install grub

I think you have installed grub legacy. To install grub2:
```
$sudo apt-get install grub-pc grub-common
```

---

### Post by gizzacroggy on 2009-12-19
Thanks/ I tried that and get these errors



```
root@gizzacroggy-laptop:/# apt-get install grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt4-opengl libqt4-assistant libqt4-test libqt4-dbus libqt4-core
  libqt4-gui libqtcore4 libqt4-svg libqt4-xml libqt4-network libqt4-designer
  libqtgui4 libqt4-script libaudio2
Use 'apt-get autoremove' to remove them.
Suggested packages:
  multiboot-doc grub-emu desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 13 not upgraded.
Need to get 0B/1,428kB of archives.
After this operation, 4,170kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 114347 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.97~beta4-1ubuntu4.1_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.97~beta4-1ubuntu4.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for sreadahead ...
Setting up grub-common (1.97~beta4-1ubuntu4.1) ...

Setting up grub-pc (1.97~beta4-1ubuntu4.1) ...
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
grub-probe: error: cannot find a device for /.

dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@gizzacroggy-laptop:/# 
```

---

### Post by Leppie on 2009-12-19
ok, not sure when you tried installing grub2 but you can only do that after chrooting:
```
sudo mkdir /mnt/Daily-root
sudo mount /dev/sda5 /mnt/Daily-root/
sudo mount -o bind /proc /mnt/Daily-root/proc
sudo mount -o bind /dev /mnt/Daily-root/dev
sudo mount -o bind /dev/pts /mnt/Daily-root/dev/pts
sudo mount -o bind /sys /mnt/Daily-root/sys
sudo cp /etc/resolv.conf /mnt/Daily-root/etc/resolv.conf
sudo chroot /mnt/Daily-root /bin/bash
apt-get install grub-common grub-pc
```

if you try this before chrooting, the root of your system will be the live cd.

---

### Post by gizzacroggy on 2009-12-19
I followed those exact commands, except that /mnt/Daily-root and /dev/sda5 are already mounted from previous attempts. I tried to umount so i could remount (dont know if important but causes no harm to do so) but it told me device is busy and wouldnt let me.

---

### Post by Leppie on 2009-12-19
> **gizzacroggy said:**
> I followed those exact commands, except that /mnt/Daily-root and /dev/sda5 are already mounted from previous attempts. I tried to umount so i could remount (dont know if important but causes no harm to do so) but it told me device is busy and wouldnt let me.

if you have chrooted into your actual system, you cannot umount it (it's supposed to be the base of your system). try rebooting.
oh and the last command doesn't need sudo, so you can just type the apt-get install...

---

### Post by gizzacroggy on 2009-12-19
That worked better but no joy when rebooted


```
gizzacroggy@gizzacroggy-laptop:~$ sudo mkdir /mnt/Daily-root
[sudo] password for gizzacroggy: 
mkdir: cannot create directory `/mnt/Daily-root': File exists
gizzacroggy@gizzacroggy-laptop:~$ sudo mount /dev/sda5 /mnt/Daily-root/
gizzacroggy@gizzacroggy-laptop:~$ sudo mount -o bind /proc /mnt/Daily-root/proc
gizzacroggy@gizzacroggy-laptop:~$ sudo mount -o bind /dev /mnt/Daily-root/dev
gizzacroggy@gizzacroggy-laptop:~$ sudo mount -o bind /dev/pts /mnt/Daily-root/dev/pts
gizzacroggy@gizzacroggy-laptop:~$ sudo mount -o bind /sys /mnt/Daily-root/sys
gizzacroggy@gizzacroggy-laptop:~$ sudo cp /etc/resolv.conf /mnt/Daily-root/etc/resolv.conf
cp: `/etc/resolv.conf' and `/mnt/Daily-root/etc/resolv.conf' are the same file
gizzacroggy@gizzacroggy-laptop:~$ sudo chroot /mnt/Daily-root /bin/bash
root@gizzacroggy-laptop:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-common is already the newest version.
grub-pc is already the newest version.
The following packages were automatically installed and are no longer required:
  libqt4-opengl libqt4-assistant libqt4-test libqt4-dbus libqt4-core
  libqt4-gui libqtcore4 libqt4-svg libqt4-xml libqt4-network libqt4-designer
  libqtgui4 libqt4-script libaudio2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up grub-pc (1.97~beta4-1ubuntu4.1) ...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda3
done

root@gizzacroggy-laptop:/# 
```

---

### Post by Leppie on 2009-12-19
> **gizzacroggy said:**
> That worked better but no joy when rebooted

was there an error code? any other message(s)?
what happened/did you see when booting?

---

### Post by gizzacroggy on 2009-12-19
the same message as always - no bootable devices found.

the error 15 message only comes when i try and fix grub with the supergrub disk

---

### Post by Leppie on 2009-12-19
try to issue this command:
```
grub-install --recheck /dev/sda
```

---

### Post by gizzacroggy on 2009-12-19
```
izzacroggy@gizzacroggy-laptop:~$ sudo grub-install --recheck /dev/sda
[sudo] password for gizzacroggy: 
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdc
gizzacroggy@gizzacroggy-laptop:~$ 

```

---

### Post by Leppie on 2009-12-19
what is the drive you are booting from?
normally this is /dev/sda (unless you've changed it).

---

### Post by gizzacroggy on 2009-12-19
i am booting from the SGD cd at present to get in to Ubuntu, if that is what you are asking.

if you asking normally, when this was running properly - i assume i was booting from /dev/sda as that is where both my vista and linux partition is.

do my results from recheck show something different?

---

### Post by Leppie on 2009-12-19
you need to modify your device.map, it currently has two links (sda and sdc).
modify the file:
```
leafpad /boot/grub/grub.cfg ##replace leafpad with whatever editor you have available (e.g. gedit, gvim)
```
then run the install again:
```
grub-install --recheck /dev/sda
```

---

### Post by gizzacroggy on 2009-12-19
Can you guide me as what exactly i need to modifty  especially as it tells me not to edit?

My slowly-becoming-educated guess would be to  change ext2 to ext 3? 
i dont see anything in the file about sda that gives me a hint as to what to do

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
search --no-floppy --fs-uuid --set 315caa64-ddbe-4f7e-8dfc-eb0b23f5d405
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
  set timeout=15
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
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 315caa64-ddbe-4f7e-8dfc-eb0b23f5d405
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=315caa64-ddbe-4f7e-8dfc-eb0b23f5d405 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 315caa64-ddbe-4f7e-8dfc-eb0b23f5d405
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=315caa64-ddbe-4f7e-8dfc-eb0b23f5d405 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set ee94845794842465
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

### Post by Leppie on 2009-12-19
my apologies, i meant to write /boot/grub/device.map
you need to delete the line containing the /dev/sdc link.
the file should look like this:
```
(hd0)    /dev/sda

```

the last line should be an empty line.

---

### Post by Leppie on 2009-12-19
i need glasses...

---

### Post by gizzacroggy on 2009-12-19
Ok, made that change and now when i run the recheck command I get just
(hd0)    /dev/sda

But rebooting still tells me no bootable device.

---

### Post by Leppie on 2009-12-19
do you get a grub shell after the error? or does it just display the error and then "hangs"?

---

### Post by gizzacroggy on 2009-12-19
its says no bootable device press F2 to exit, FX for something esle and F5 to run onboard diagnosis.

nothing else.

when i press F2 and F5 nothing happens, when i pressed F5 i cant remember what happened but know it didnt give me any options.

---

### Post by Leppie on 2009-12-19
ok, this sounds more like a hardware issue, or does it explicitly say it's grub?
when you boot your system, you should get a screen where it says to press some key to enter bios (or to modify setup or something similar). usually the bios has a utility to probe installed hard drives, try running it.

---

### Post by gizzacroggy on 2009-12-19
difficulty with that suggestion is that is has an administrative password, set by dell and doing some quick research, there are ways to override it but can have unexpected consequences. 

any other way to check hardrives?

---

### Post by gizzacroggy on 2009-12-19
I was just searching for help on how to overcome administrator BIOS password and found this post


" I changed the time and date in setup and when i rebooted it said the HDD was password protected. It gave me 3 tries to guess then went to a black screen that said
 
Primary hard disk drive 0 not found
No bootable devices--strike F1 to retry boot, F2 for setup utility

 Now i have these 2 Dell CD's, one is drivers and utilites and drivers, and the other is operating system. I was wondering if i should put either one of these into the CD port and run them, but i wanted to ask here 1st. I know my knowlege is low and this may be an easy ?, but thanks for the help."


This made me suddenly remembered something. When i installed Ubuntu i put the time in correct but when it booted either vista or ubuntu had the time wrong. i changed whichever one it was and i have a feeling that might have been the last time i could boot

based on this, i think your suggestion that it might be my hardware could be right. I got so hooked that itr was grub that i didnt think about this time change.

No one answered the above post. I have all the disks, any suggestions?

Here it gives advice for a fresh install of windows, but unclear what i should do when i have both. first reinstall windows and then ubuntu?
[http://www.techspot.com/vb/all/windows/t-53377-No-Bootable-Devicesstrike-F1-To-Reboot-F2-For-Setup.html](http://www.techspot.com/vb/all/windows/t-53377-No-Bootable-Devicesstrike-F1-To-Reboot-F2-For-Setup.html)

G

---

### Post by Leppie on 2009-12-19
> **gizzacroggy said:**
> difficulty with that suggestion is that is has an administrative password, set by dell and doing some quick research, there are ways to override it but can have unexpected consequences. 

any other way to check hardrives?

you could try downloading some boot cd with disk analysis utilities (a particularly rich boot cd is Hiren's boot cd). if you have a windows recovery disk, you could try to restore the master boot record to factory settings (in windows you can do that using the fdisk utility).

i find it strange to hear that dell has set an administrative password for bios access. i've owned several dell laptops, all without admin password on bios when purchased.

---

### Post by gizzacroggy on 2009-12-19
Under boot sequence only cd/dvd is selected. not internall HDD, 

so back to how to get password to change this.

---

### Post by Leppie on 2009-12-19
all windows versions store local time on the machine. most other operating systems (among which linux) prefer to store utc. however, ubuntu asks which one to use during installation (and advices the user to use local time if another os is installed).

i think ubuntu install is quicker than windows. just remember to set the correct time option ;)

---

### Post by gizzacroggy on 2009-12-19
when the problem first came up i reinstalled UBuntu but no difference. However it did not give the options to change the time option. 

Do i need to uninstall it first? and if so how do i do that? actually i can search for that info mayself as sure its been asked a thousand times but do please let me know if i must uninstall.

ta x

---

### Post by Leppie on 2009-12-19
> **gizzacroggy said:**
> Under boot sequence only cd/dvd is selected. not internall HDD,

can you not add the hdd?

---

### Post by Leppie on 2009-12-19
> **gizzacroggy said:**
> when the problem first came up i reinstalled UBuntu but no difference. However it did not give the options to change the time option. 

Do i need to uninstall it first? and if so how do i do that? actually i can search for that info mayself as sure its been asked a thousand times but do please let me know if i must uninstall.

check the cd for errors before re-installing again.
also, have you tried changing back the time in the bios?

i'd say that removing isn't necessary, if you have all your ubuntu partitions formatted (at least the system ones, e.g. /, swap and /boot if present) upon re-install.

---

