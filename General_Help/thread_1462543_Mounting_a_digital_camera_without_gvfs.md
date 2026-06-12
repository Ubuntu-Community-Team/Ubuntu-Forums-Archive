---
title: "Mounting a digital camera without gvfs"
date: 2010-04-25
forum: General Help
---

### Post by nolanpro on 2010-04-25
When I plug in my digital camera, it mounts it as a gvfs-mount. I have a few problems with this
 * It takes 2 times: I have to plug it in, wait, unplug it, plug it back in before it shows on the desktop
 * Don't have command line access: Nothing in ~/gvfs after mount and I cant do anything with gphoto2://[usb....]
 * Cant access it from another desktop instance: gvfs-mount -l lists it when i'm on a terminal on the desktop, but not when i'm ssh'ed into the system.

Really i just want to mount, rsync photos for backup, unmount and be done with it (all this in 3 lines of a shell script that i'll add to udev so its fired when ever the camera is plugged in)

dmesg: usb 1-5: new high speed USB device using ehci_hd and address 8. Configuration #1 chosen from 1 choice

lsusb: Bus 001 Device 008: ID 04a9:3176 Canon, Inc. PowerShot A590

How can I mount it as a normal mount (perhaps something that automatically shows up in /media or something)

Any ideas? Thanks!

---

### Post by oldfred on 2010-04-25
I just never connect my camera. I have several media cards so I am taking them in and out. My portable has a multicard reader. I bought a multicard USB adapter years ago. And when I built my desktop I included a multicard reader. I prefer to manage my photos in my own way so I have not found any system that works and it is not that hard to manually copy new photos.

---

### Post by nolanpro on 2010-04-25
I guess I might just need to get a card reader. Don't have one now, I just use the USB cable.

The camera is unable to identify itself as a mass storage device, only as a camera. Even with hacked chdk firmware.

So would it appear that ubuntu is unable to mount a device that identifies itself as a digital camera?

---

### Post by slooow on 2010-04-25
Hi,

Although I have a card reader, I never use it. My method run with a script:
If you have Ubuntu, the system might mount your camera on /media when you plug it in with the usb cable. Check in /etc/fstab or check with 'df' once you plugged the camera in. If there is no entry of /media, then enter the following line in fstab as superuser:
/dev/sdf1        /mnt/pen    vfat        noauto,users,rw,umask=0 0 0

Then I run the following script, called dwnld.sh, located in the photo directory. It mounts the camera, moves the photographs to the directory where the dwnld.sh script is located and then unmount the camera again. If you prefer leaving a copy of the photographs on the card in the camera, use cp (which is commented out). Your paths might be different.

#!/bin/bash -x
mount /mnt/pen
mv /mnt/pen/dcim/10*/* ./
#cp /mnt/pen/dcim/101msdcf/* ./
umount /mnt/pen


After that I rename the photographs with 'renrot' to a YYYYMMDDhhmmss format.

---

### Post by nolanpro on 2010-04-25
Thanks for the info but unfortunately I don't have /dev/sdf1. I actually get 4 entries in /dev when I plug in the camera:

usbdev1.11_ep00
usbdev1.11_ep02
usbdev1.11_ep81
usbdev1.11_ep83

Dont know if I should attempt to mount any of those.

ANOTHER very strange thing i just discovered:

Its hit or miss when I plug in the camera whether it will gvfs-mount or not (with a camera icon on the desktop). However, when it DOESN'T mount, i DO get an accessible path in ~/.gvfs.

This is OK except I never know when its actually.. well... not going to mount. Very strange.

---

### Post by slooow on 2010-04-25
Plug the camera in, and get the output of 'less /var/log/dmesg | grep sd'. It should show the amount of memory and something like /dev/sdb1. Like this you can identify the camera.

---

### Post by no2498 on 2010-04-26
i do not have the same camera
but i need to turn mine on and push the set button to connect it to the computer
then it acts like a card reader
hope this helps

---

