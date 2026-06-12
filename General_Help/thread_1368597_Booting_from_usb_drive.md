---
title: "Booting from usb drive"
date: 2009-12-30
forum: General Help
---

### Post by celikmus on 2009-12-30
Hi,
I cloned my hard disk onto an identical-size portable usb hard drive. I expected ubuntu to boot from the USB drive at my next restart, but it didn't. It doesn't mount the usb drive any more, though I can mount partitions of it manually. What do you think the problem might be?

Below is how I cloned:
[FONT=System][SIZE=1][COLOR=Gray]dd if=/dev/sda conv=noerror,sync bs=64k | dd of=/dev/sdb bs=64k[/COLOR][/SIZE][/FONT]

... which worked perfectly:
[FONT=System][SIZE=1][COLOR=Gray]> fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005ad94
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19136   153709888+  83  Linux
/dev/sda2           19137       19457     2578432+   5  Extended
/dev/sda5           19137       19457     2578401   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005ad94
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19136   153709888+  83  Linux
/dev/sdb2           19137       19457     2578432+   5  Extended
/dev/sdb5           19137       19457     2578401   82  Linux swap / Solaris[/COLOR][/SIZE][/FONT]

I made the change in BIOS to up usb drive's priority ahead of hard drive. BIOS was able to see my plugged-in usb drive, so it was easy to set up.

Below is a piece of log from syslog. I gather bootloader is trying to load from the USB drive and fails.
[FONT=System][SIZE=1][COLOR=Gray]Initializing USB Mass Storage driver...
scsi6 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22] ....
PM: Starting manual resume from disk
PM: Resume from partition 8:5
PM: Checking hibernation image.[/COLOR][/SIZE][/FONT][SIZE=1][COLOR=Gray]
PM: Resume from disk failed.[/COLOR][/SIZE]

Any help will be much appreciated.

Regards

---

### Post by lmarmisa on 2009-12-30
Try to reinstall the grub loader in your /dev/sdb hard drive.

Start your system, open a terminal and type these commands:

```

sudo bash
mount /dev/sdb1 /mnt
gedit /mnt/boot/grub/device.map   #update data to sdb
mount --bind /dev/ /mnt/dev
mount --bind /usr/ /mnt/usr
mount --bind /proc/ /mnt/proc
chroot /mnt
grub-install /dev/sdb
grub-install --recheck /dev/sdb
exit
reboot

```

---

### Post by Leppie on 2009-12-30
do you get any messages?
i think that only reinstalling grub will not resolve, as most probably fstab entries aren't correct (since you probably want to use the usb filesystem).
you will have to update the grub configuration file as well (which grub do you have installed? grub legacy or grub2?) and you will have to make appropriate amendments in fstab.

---

### Post by john newbuntu on 2009-12-30
In general, after cloning, it would also be prudent to check the file system consistency on the new partition(s) using e2fsck.
Also check the blkids.

---

### Post by lmarmisa on 2009-12-30
I have read again your post and I have a doubt. Did you use a Live Cd for cloning your hard drive?. If you try to clone your /dev/sda hard drive while Ubuntu is running on it the result will be bad.

I recommend you to use [http://www.clonezilla.org/](http://www.clonezilla.org/) if you want to clone partitions or hard drives. Clonezilla is also good for backups.

---

### Post by celikmus on 2009-12-30
Hi guys,
thanks for your prompt responses. You guessed it right, all I want to do is backing up my system into a portable usb device. I checked fsck is ok, and my grub is the legacy one.

Because I do this for back-up, and will do this regularly, I did not go beyond the grub device map line at lmarmisa's first post. I did not want to use CloneZilla as I thought there could be a way to clone my image without having to logout the system. I've previously tried partimage, which came short at taking the disk image - it takes images of partitions only. So, I ended up using dd to clone my hard drive. I ran dd while Ubuntu was running idle on the drive.

I'm thinking it could work if I changed all 'hda' references 'hdb' in relevant files. Would it work? The BIOS setting forces the processor to boot from /dev/sdb, so is it not all to sdb's MBR to orchestrate? I need the system to load from sdb when sda fails. 

As per lmarmisa's note, /boot/grub/device.map is one file to make the 'hdb' change, any other files? fstab could be one of them, I suspect I may have to put the UUID of the sdb in there as well?

Regards

---

### Post by lmarmisa on 2009-12-31
I think that it does not make sense to try to clone your hard drive with the dd command while your system is running.

Maybe this documentation could be useful for you:

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by celikmus on 2010-01-10
Hi,
I believe there must be a way to backup a disk image in Linux without having to boot from a CD or to unmount the disk in question. Does anyone know how SuperDuper on Macs does it?

I started off with aiming to backup my disk as a bootable image on a USB drive. After several days of efforts, I've forgone the bootable part as none of the solutions offered it. Now I am being asked to forgo the ability to do it as an application; that's too much of a limitation for a Linux system, given it is already done on Macs!

Regards

---

### Post by CharlesA on 2010-01-10
You could clone the drive using something like Clonezilla and then restore it from USB. But I don't think that's what you are looking for.

---

