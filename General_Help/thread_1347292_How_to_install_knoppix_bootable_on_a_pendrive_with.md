---
title: "How to install knoppix bootable on a pendrive with Linux?"
date: 2009-12-06
forum: General Help
---

### Post by frenchn00b on 2009-12-06
here is the installer for Windows XP:
[http://www.pendrivelinux.com/usb-knoppix-510/](http://www.pendrivelinux.com/usb-knoppix-510/)

is there the same for LINUX ubuntu?

---

### Post by frenchn00b on 2009-12-06
sudo knoppix2pendrive-installer.sh
```

echo "enter the username of the regular user:"
printf ":> "
read theuser
clear
fdisk -l
read "enter the device /dev/xxx to install where is the pendrive, to be erased ?"
printf "enter xxx value eg sda1:> "
read thedevice
cd /tmp
sudo -u $theuser 'cd /tmp ; wget -N "http://www.kernel.org/pub/dist/knoppix/KNOPPIX_V5.1.1CD-2007-01-04-EN.iso"'
mkdir -p /tmp/pendrive
mkdir -p /tmp/cdrom
mount -t vfat /dev/$thedevice /mnt/pendrive
mount -t iso96000 -o loop /tmp/KNOPPIX_V5.1.1CD-2007-01-04-EN.iso /mnt/cdrom
cp -a /mnt/cdrom/* /mnt/pendrive/

### what now to do?? how to make it bootable??


```

---

### Post by frenchn00b on 2009-12-06
You can try this to make a boot pendrive
> **spiderbatdad said:**
> this shouldn't be too hard. I'll confess i haven't done this on ubuntu, but recently make a bootable usb for slackware. The process should be very similar. Obtain boot.img.gz for karmic: [http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/hd-media/)

Plug in your usb stick. Become root with sudo -i, or you may need to modify permissions of the drive to 666

Unmount the usb drive ```
umount /dev/sdc1
``` or whatever your device drive is.

```
zcat boot.img.gz > /dev/sdc 
```this should write boot.img.gz to the usb stick. Remount your usb drive and copy the iso to a root partition.

---

