---
title: "Ironkey won't automount in Karmic"
date: 2009-12-14
forum: General Help
---

### Post by bitter_mike on 2009-12-14
Hey all.

So I have an IronKey: its an encrypted flash drive, but that shouldn't really affect the problem I'm having. It has a small, permanent partition on it which pretends to be a generic external CD bay containing a disk with the unlock program on it. In every previous version of Ubuntu (7.10, 8.04, 8.10, 9.04) I would plug it into the USB and it would automatically mount, no problems. Now that I'm running Karmic though, it will not automount. Other USB external media like flash drives and SD cards automount just fine, but not the fake external CD bay on the IK.

I'm up to the latest version of udev, even in the proposed repository, and up to date on everything else. The device is detected by disk manager and lsusb and fdisk and I can manually mount it, but I'd  like it to automount like all my other USB media. Here is the dmesg output for it:

[  504.176124] usb 1-4: new high speed USB device using ehci_hcd and address 6
[  504.309667] usb 1-4: configuration #1 chosen from 1 choice
[  504.311570] scsi5 : SCSI emulation for USB Mass Storage devices
[  504.315127] usb-storage: device found at 6
[  504.315142] usb-storage: waiting for device to settle before scanning
[  505.686815] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1077
[  509.312388] usb-storage: device scan complete
[  513.703742] scsi 5:0:0:0: CD-ROM            IronKey  CD-ROM           1.00 PQ: 0 ANSI: 0

I'd be most grateful if someone could figure out why this isn't working. Thanks.

---

### Post by dondano on 2010-01-27
Hello, I am having exactly the same problem. Could you finally solve it??
 
Many thanks

---

### Post by albtross on 2010-02-04
I have the same problem, you have to update your ironkey firmware to support linux. ...it will add a linux directory.

see this url
[https://support.ironkey.com/article/096](https://support.ironkey.com/article/096)

You may run into a cert issue, I have.... 

[https://support.ironkey.com/article/448](https://support.ironkey.com/article/448)

Hope this helps

---

### Post by bitter_mike on 2010-02-04
That's not the same problem. The problem I and dondano are experiencing is that when we plug the drive into the USB port, the computers fails to automount the permanent drive with the unlocking software on it and we have to do it manually. The software for using the ironkey on linux is present, its just a pain to manually mount the drive that contains it.

And dondano: no I have not found a way to fix it

---

### Post by dondano on 2010-02-09
Bitter is right, it is not the same problem. IK will open in Red Hat straight away, but not Ubuntu. 
 
Getting frustrated with this.
 
Thank you all!

---

