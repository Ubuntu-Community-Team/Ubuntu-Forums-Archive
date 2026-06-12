---
title: "WP7 not detected?"
date: 2011-07-16
forum: General Help
---

### Post by MotherMonster on 2011-07-16
I bought an HTC Trophy today, and when I plugged it into my laptop it just charges. Ubuntu doesn't mount the device (it's not on the desktop or in the Unity sidebar) 

When I run lsusb, however, I get this output:

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 04f2:b249 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 045e:04ec Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I'm assuming Microsoft is the device because I have no other hardware attached to the device. Thankyou for all help.

---

### Post by Ozymandias_117 on 2011-07-16
Try pasting the output of ```
sudo fdisk -l
```

---

### Post by MotherMonster on 2011-07-16
> **Ozymandias_117 said:**
> Try pasting the output of ```
sudo fdisk -l
```

Nothing happens.

---

### Post by MotherMonster on 2011-07-16
Help please!! When I plug the phone in nothing happens :( I don't wanna have to install Windows 7 over Ubuntu

---

### Post by westie457 on 2011-07-16
> **MotherMonster said:**
> Help please!! When I plug the phone in nothing happens :( I don't wanna have to install Windows 7 over Ubuntu

First steps are to check the connectivity settings on the phone.

Personally I do not have a Windows Phone so cannot suggest what is needed.

---

### Post by 3rdalbum on 2011-07-16
Does the phone have a mass storage device mode?

You might struggle to get Microsoft stuff to work with Linux, it's usually made to be locked to Windows.

---

### Post by I_ated_it on 2011-07-16
Im having the same issue, as I understand it there is no usb storage mode for WP7 (though there is a windows registry hack that will make it a usb storage device for windows).  I run windows 7 on my computer through Virtual box but I still cant get it to recognize my phone.

Is it possible to get a device that isnt supported in linux to work in windows virtually?

---

### Post by MotherMonster on 2011-07-16
Exactly, I'm running Windows XP in Virtual Box and it detects things like flash drives and what not but the computer just refuses to see the phone. I can't do any registry hack if the phone isn't even seen on the computer.

---

### Post by westie457 on 2011-07-17
> **MotherMonster said:**
> Exactly, I'm running Windows XP in Virtual Box and it detects things like flash drives and what not but the computer just refuses to see the phone. I can't do any registry hack if the phone isn't even seen on the computer.

Absolutely no idea if it will work. Have you tried running Wine then connecting your phone?

---

### Post by gandaran on 2011-07-17
I used to have a windows mobile phone and I just installed an application on the phone I found on some windows apps webpage to turn the phone into usb storage mode when needed, this was the only way I could use the phone on Ubuntu.

---

### Post by I_ated_it on 2011-07-17
I downloaded the usb storage enabler tool from xda hoping it would get me somewhere but unfortunately it only enables storage for the windows PC it is installed on (in this case my windows laptop) and not for the device itself.

I also tried installing the enabler tool with wine but it didnt work, I never have much luck trying to do anything with wine.

---

### Post by I_ated_it on 2011-07-31
> **MotherMonster said:**
> Exactly, I'm running Windows XP in Virtual Box and it detects things like flash drives and what not but the computer just refuses to see the phone. I can't do any registry hack if the phone isn't even seen on the computer.


I actually got Zune to recognize my phone on my windows 7 guest, it should be the same for XP.  The problem I had is I didnt have administrative access to the vboxuser account.  Im not sure if this will help you or not but its worth checking out.

[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)

Once you have access  with your phone connected via usb you should run in terminal  ```
VBoxManage list usbhost 
```and it should output something like this


```
UUID:               43497b50-ec4a-46fb-9c22-df21141a1ab8
VendorId:           0x045e (045E)
ProductId:          0x04ec (04EC)
Revision:           0.0 (0000)
SerialNumber:       99461300-b56a-0801-0100-da4300420000
Address:            sysfs:/sys/devices/pci0000:00/0000:00:12.2/usb1/1-6//device:/dev/vboxusb/001/003
Current State:      Available
```along with any other usb devices you have connected

Also for this to work you need to have the VirtualBox Extension pack installed

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

When you have access to the Vboxuser account and the VirtualBox Extension pack installed go into your Virtual Box settings for the XP guest and go to the usb tab and click add new filter and it should show "Unknown device 045E:04EC" or something like that.  With the usb controller enabled and the filter selected you can start your your windows XP virtual machine.  It probably wont automatically find your device so you will need to go to add new hardware in the control center and install it manually.

Hopefully this helps.  This is my first time writing any kind of tutorial so Im not sure how easy it is to follow.

---

