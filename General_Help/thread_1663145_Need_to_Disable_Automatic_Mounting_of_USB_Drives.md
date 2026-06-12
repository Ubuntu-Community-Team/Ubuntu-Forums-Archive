---
title: "Need to Disable Automatic Mounting of USB Drives"
date: 2011-01-09
forum: General Help
---

### Post by GWild on 2011-01-09
Update:

Solution posted below.


Hello.

Distro: Kubuntu 10.04 AMD 64.

My system automatically mounts USB devices when attached to the system.

I have explicitly disabled this function in (KDE) System Settings --> Advanced --> Removable devices.

It doesn't matter - as soon as a USB device is plugged in the system mounts it as root.

Any suggestions as to how I can disable this?

---

### Post by tredegar on 2011-01-09
**usb-storage** is automatically loaded when a usb disk is plugged in.
So disable it my renaming it
```
sudo mv /lib/modules/$(uname -r)/kernel/drivers/usb/storage/usb-storage.ko \
/lib/modules/$(uname -r)/kernel/drivers/usb/storage/usb-storage.ko-disabled
```
Now remove the module
```
sudo rmmod usb-storage
```
USB disks do not work now.

---

### Post by GWild on 2011-01-09
> **tredegar said:**
> **usb-storage** is automatically loaded when a usb disk is plugged in.
So disable it my renaming it
```
sudo mv /lib/modules/$(uname -r)/kernel/drivers/usb/storage/usb-storage.ko \
/lib/modules/$(uname -r)/kernel/drivers/usb/storage/usb-storage.ko-disabled
```
Now remove the module
```
sudo rmmod usb-storage
```
USB disks do not work now.


Thank you for the response.

I found my issue.  After messing around for several days I searched packages containing the name/description *USB* and realized that (and I don't remember when) I previously installed USB Mount.

That was the source of the issue.  The system now 'behaves' according to the current parameter settings (do not automatically mount USB devices).

---

### Post by MARP1961 on 2011-01-09
I wish I had this problem in Ubuntu 10.10! I can't get it to automount at all.

---

### Post by tredegar on 2011-01-09
> I wish I had this problem in Ubuntu 10.10! I can't get it to automount at all.
You should start a new thread for a new problem but ..... post your **/etc/fstab** (without any USB drives plugged in)

---

