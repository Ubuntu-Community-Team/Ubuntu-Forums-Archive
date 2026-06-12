---
title: "Unable to migrate to new partition"
date: 2010-10-04
forum: General Help
---

### Post by turqoisehex on 2010-10-04
I want to change my partition configuration, and migrate my install to a drive I haven't used in a while. I've followed the steps which I have seen in several locations, but for some reason I can't boot into it (hopefully it's something simple :KS)

Here's what I've done so far:

Deleted all of the partitions on the drive

created a new EXT4 and swap partition on the drive (and others that are currently unused)

mounted the new drive, and rsynced the old drive with this command:

```
sudo rsync -va --exclude=/media --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --progress / /media/ubuntu

```

it completed with one error relating to my .gvfs folder

used mkdir to create the skipped folders

took the UUID for the new partitions out of information in Gparted and replaced the old ones in /etc/fstab. The UUID for the new EXT4 looked different than what I expected, don't know if it's relevant (SDA is the new drive):
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda2 :
UUID=705dc27d-c467-4eec-82ba-aaf58565d860    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sdb1 :
UUID=C6F2972DF29720AB    /media/d    ntfs-3g    defaults,locale=en_CA.UTF-8    0    0
#Entry for /dev/sdc1 :
UUID=D0206DA8206D95EE    /media/e    ntfs-3g    defaults,locale=en_CA.UTF-8    0    0
#Entry for /dev/sda1 :
UUID=085456A75972261D    /media/xp    ntfs-3g    defaults,locale=en_CA.UTF-8    0    0
#Entry for /dev/sdc3 :
UUID=09180280-2bbc-491f-ab33-09324a54b091    none    swap    sw    0    0

```

ran sudo update-grub, which showed the new OS on sda2

Rebooted. At Grub I selected the new drive... but it took me to the old drive. I thought that was confusing, and figured it was possibly related to grub, so I ran:

```
sudo grub-install --root-directory=/media/ubuntu /dev/sda
```
which returned no errors, then

```
sudo update-grub
```
again, no errors

Changed the boot order to go to SDA first

This is where it gets weird; when I got to grub, it showed only one linux image (the old one) and Windows XP/NT, which is not currently installed on any drive. My guess is that this is somehow an old grub from when I have used this drive in the past... 

Then I ran:
sudo grub-install --root-directory=/media/ubuntu /dev/sda
sudo grub-setup -d /media/ubuntu/boot/grub /dev/sda
sudo update-grub

Still no luck. It's back to showing the SDA2 installation in the grub menu but when I boot to it I'm still going to the SDC installation.


at this point I don't know what to do next, any and all help is appreciated.[-o<

---

### Post by andrewthomas on 2010-10-04
You have to have the boot order how you want it when you do the installation of grub.  

Just reinstall grub again.

---

### Post by turqoisehex on 2010-10-05
Thanks, I installed again:

```
sudo grub-install --root-directory=/media/ubuntu /dev/sda
sudo grub-setup -d /media/ubuntu/boot/grub /dev/sda
sudo update-grub
```

as suggested in the Grub2 Wiki... Still no luck. It's back to showing the SDA2 installation in the grub menu but when I boot to it I'm still going to the SDC installation.

When I run 
grub-probe -t device /boot/grub

It returns:
/dev/sdc2

**Edit:**

I booted into a live CD and followed the instructions on the Grub2 wiki for restoring after Windows has damaged the MBR (The chroot method). Worked like a charm :-)

---

### Post by ka3sem on 2010-10-12
Hi,

can you explain me what means the 1st parameter after --root-directory  and the 2d one please

sudo grub-install --root-directory=/media/ubuntu /dev/sda

I have only ubuntu 8.10 in my computer, and trying to desinstall some tools and make more free space to do the update to ubuntu 9, I have deleted some system-files (python), and my OS become defected :( , no internet connexion, no graphic interface, ...

my ubuntu CD is defected too and shows ubiquited error. I can only boot from it, but can not install the install packet which is in the desktop.

I have downloaded the .iso version 10.04 but the grub failed :confused:

I have followed this link
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

but in step3, I founed /etc/grub.d/20_memtest86+ instead of /etc/grub.conf or /boot/grub/menu.lst or /etc/grub.d/40_custom and I have added the following files in my 20_memtest86+

menuentry "installer" {
        insmod ext2
        set root=(hd0,1)
        linux /casper/vmlinuz boot=casper root=/dev/ram1 ramdisk_size=1048576 rw
        initrd /casper/initrd.lz
}


can someone help me please :confused:

---

### Post by ka3sem on 2010-10-12
sorry the link is the following

[https://help.ubuntu.com/community/Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux")

---

