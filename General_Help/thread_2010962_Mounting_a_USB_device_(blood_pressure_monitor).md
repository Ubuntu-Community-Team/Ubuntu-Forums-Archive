---
title: "Mounting a USB device (blood pressure monitor)"
date: 2012-06-26
forum: General Help
---

### Post by SoFl W on 2012-06-26
I have a Homedics blood pressure device that has a usb plug on the back.  I think the higher end models come with software (windows) this one did not.
I wanted to see if there was any useful information written to the device and check out the file system,  When I plug the device in it does not show up in "places"

the lsusb command returns:    
```
Bus 004 Device 002: ID 1241:0150 Belkin
```
(It shows other items also but this is the only new device that shows up when I plug the monitor in)

"sudo fdisk -l" only shows my two hard drives and nothing else.

If I run Windows in Virtualbox the virtualbox will show "HealthLife HL168" under the USB devices and it appears to mount in Windows.  Gives me "New device found" and a device is now ready popup but it does not show up under my computer as a drive.

Can this be mounted as a drive or is it not a drive?

Thanks.

---

### Post by MG&amp;TL on 2012-06-26
I highly doubt it's got a filesystem on it...but we can try:

Do you know what the /dev/ filename is? If not, try posting:

```
ls /dev/
```

---

### Post by SoFl W on 2012-06-26
The more I look around the more I agree it probably doesn't have a file system.  It doesn't have a /dev name.
I think I tried mounting it several years ago but I don't remember. I had the blood pressure kit in storage, and started using it again so I figured I would see if there was any useful data on it.

Thank you for your help but I think I will give up on it for now.

---

### Post by Grenage on 2012-06-26
Isn't it more likely that such units pump out data over a serial (over USB) connection?  What does minicom show?

Edit, I missed the lack of a dev entry, forget the output query. :)

---

