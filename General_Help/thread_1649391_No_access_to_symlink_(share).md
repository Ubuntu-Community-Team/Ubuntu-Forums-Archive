---
title: "No access to symlink (share)"
date: 2010-12-20
forum: General Help
---

### Post by vbSteve on 2010-12-20
Platform: Ubuntu Server 10.10 (Terminal Mode)


Hi,

Yesterday, I bought a new USB harddrive of 1TB and i'm trying to share that drive to all the users on my network (mostly windows users)

Samba is already installed and users do have access to the home folder. I've created a user (store) and placed a symlink inside its home folder to the mount point of the usb drive, but for some reason no one has access to the folder; though they can see it, and the store user itself (when logged onto ssh) has access to the folder.

These are the actions I have performed:

1- $ tail /var/messages :> *Found out that the drive is named sdc1*
2- $ sudo mkfs.ext4 /dev/sdc1
3- $ sudo e2label /dev/sdc1 usb-store
4- $ sudo mkdir /media/usbdrv0
5- $ sudo mount /dev/sdc1 /media/usbdrv0 -t ext4
6- $ sudo adduser store (...)
7- $ cd /home/store
8- $ sudo ln -s /media/usbdrv0 usb-store


On my windows computer, opening Windows Explorer and typed in \\192.168.1.10\store (logged on with user (store) and password). I can see the folder usb-store, but when I double-click it, it says that I don't have permission. I can see all the other files in the home folder that were copied from skel and I can modify them without problem, I can add folder, add files, delete them, etc; I just can't enter usb-store.
I've tried to set permission to chmod 777 on /media/usbdrv0 but it wouldn't let me so I changed it back to 755.
I've also tried restarting the server computer, but with no result.
I've tried mounting with option "-o users" as well.


If anyone can shed some light on this, I would be very grateful.
Thanks,

---

