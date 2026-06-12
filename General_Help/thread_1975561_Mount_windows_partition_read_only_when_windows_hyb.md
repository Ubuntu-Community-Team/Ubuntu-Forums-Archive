---
title: "Mount windows partition read only when windows hybernated"
date: 2012-05-07
forum: General Help
---

### Post by mbohets on 2012-05-07
Hi,

I dual boot W7 and Kubuntu 12.04 on my work PC.
At work I have to use W7 (login to the domain) at home a use Kubuntu for a long time on a fixed PC. As my PC is getting slow compared to a modern PC, I decided to put Kubuntu on my work PC to enjoy the speed.
When I hybernate W7 at work, Kubuntu fails to start because it cannot mount the windows partition which is in fstab and I get an error message that I should mount it ro.
Is there a way to make Kubuntu automatically mount the W7 partition as read only
when this error occurs ?

Best rgds,

Marc

---

### Post by Helkaluin on 2012-05-07
Try the mount option "errors=remount-ro"?

---

### Post by mbohets on 2012-05-07
No luck, but perhaps there are too many options or I forgot a space or another syntax error, or it does not work on ntfs partitions ?

Here is my fstab file

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=b449533a-3b0e-4617-b13f-1d4848a602cc /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=20371b26-c832-4c6e-901b-b6c0925d741a /home           ext4    defaults        0       2
# /windows was on /dev/sda1 during installation
UUID=68DC90F6DC90BFAC /windows        ntfs    defaults,umask=007,gid=46,errors=remount-ro 0       0
# swap was on /dev/sda5 during installation
UUID=456124bb-8d86-4a54-aa11-9e6e240e3d0a none            swap    sw              0       0

---

