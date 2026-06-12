---
title: "Can't mount Kodak C310 camera USB ..."
date: 2010-02-18
forum: General Help
---

### Post by Bucky Ball on 2010-02-18
Hi all,

I have a Kodak C310 stills camera that plugs in usb. When I plug in and switch on, I get this from dmesg | tail:

```
[  616.381972] usb 4-2: new full speed USB device using uhci_hcd and address 3
[  616.593353] usb 4-2: configuration #1 chosen from 1 choice

```... and that's it. No /dev or device details; if it assigned a /dev/? I would be good to go I think!

lsusb shows me the correct device details:

```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 040a:058a Kodak Co. C310
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```sudo fdisk -l shows no sign of the device. So, recognised as a USB device but that seems to be where it stops. 

Do I need to add a udev rule or something along those lines? If I add a custom command to perform when a  camera is connected, gimp for instance, in Settings Manager->Removable media->Cameras, I switch the camera on and sure enough the Gimp boots up, so the camera is definitely being detected. It just shows no icon on desktop and I can't transfer the pics from the camera.

If I could set the custom command to software that would allow me to transfer files from the camera that would be sweet enough, no icon required, but a work around. I would really like to see the camera on my desktop or in my media folder.

Should I perhaps alter the /fstab? Just a friendly reminder to make it absolutely clear, I am using ***X***ubuntu Hardy 8.04 on this machine (xfce only), so no Gnome tips, please. ;)

Slightly bonkers, any help? Thanks in advance ...

---

### Post by Bucky Ball on 2010-02-18
I installed gThumb Image Viewer, had it boot when I switch the camera on, go to File->Import Photos and get this error message:

> An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.Getting closer. Any ideas? Perhaps I'm not a member of the appropriate group ...

* UPDATE: Solution? Open gThumb with the command 'gksudo gthumb' when a camera is present. Fantastic. Camera is identified correctly in gThumb and I can now drag files from the camera no problem. BUT, I still can't get into the camera and delete the flash card contents once I have imported the files from the camera. Hmm.

Let's call it half solved. All input appreciated.

---

### Post by leonbravo on 2010-11-26
Great post. Learned some new commands.

However, in my case is a kodak M1073, ubuntu 10.04. Using gthumb, I've got a message saying the Camera is already in use.

weird right?

Same outputs as you had in dmesg and lsusb (usb 5-1)


did you fully solve the problem in another way.

cheers, Leo

---

