---
title: "Can read but not copy files from UFS drive"
date: 2010-08-15
forum: General Help
---

### Post by The Flying Penguin on 2010-08-15
My Freenas server is currently off line for the moment pending the arrival of some thermo paste and I need to get some files off one of the drives. The drive is formatted in the UFS file system.

I am using a usb to sata converter to hook the drive up to my laptop which is running 10.04.

I have manage to get the drive to mount by:

```
sudo modprobe ufs
```then

```
mount -t ufs -o ro,ufstype=ufs2 /dev/sdc1 /mnt
```I am then able to browse the files by going to my /mnt folder. The problem is I cannot copy any of the files. I get a permission error. I have tried chmod 777 command to change the permission but I get an error about it being read-only. I tried running nautilus as root to copy the files but I still get a permission error. Using nautilus as root to change the permission or alter any of the read/write options fails because the drive is read only.

From what I understand I can only mount the drive as read only because its UFS and I can't change the permissions because its read only. Sounds a bit like an endless loop lol.

Running Freesbie (freebsd live cd) didn't do me any good as it didn't even detect my hard drive and I don't want to learn a new OS just to transfer my files.

Any advice would be appreciated. I really don't want to wait until my thermo paste comes and I will be on the road for the next couple of weeks so I won't even be able to get it setup. I need these files now.

Thanks

---

### Post by The Flying Penguin on 2010-09-02
Anyone have an idea what to do? I have almost 640GB of files that I need to get off this drive!

Turns out my Freenas motherboard is shot. I've had problems in the past getting UFS formatted drives to mount in Freenas if they weren't unmounted before removal so I don't even want to try to put it in a new Freenas machine.

---

