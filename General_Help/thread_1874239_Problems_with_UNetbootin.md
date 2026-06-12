---
title: "Problems with UNetbootin"
date: 2011-11-02
forum: General Help
---

### Post by djbigwillie on 2011-11-02
Hello I am on Ubuntu 11.10 and I have a Windows 7 ISO that I want to put onto a USB drive as a bootable drive I have formatted the USB to NTFS with Gparted but when I get to UNetbootin it does not allow me to view the USB drive and it does not show the checkbox option (show all drives) as I have seen in many forums. Do I need another version of UNetbootin or do I need to edit some preferences?

---

### Post by dniMretsaM on 2011-11-02
First, make sure the drive is mounted. The easiest way to do this is to open Nautilus and click on the drive's icon in the sidebar. Also, make sure the drive's boot flag is set (do this through GParted). I don't remember if this is necessary, but do it just in case. And make sure the drive selection (drop-down menu near the bottom of the UNetbootin screen) is set to show USB drives (not hard drives).

---

### Post by vicshrike on 2011-11-02
Is this relevant?:

[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by djbigwillie on 2011-11-02
I have the drive mounted and USB drives is selected and yes I did make sure BOOT was selected in Gparted the problem is when I am IN UNetbootin there should be a box I am able to check that says (show all drives) after i have checked the USB drive one as well to allow my NTFS formatted USB drive to show and it's not there

---

### Post by djbigwillie on 2011-11-02
vicshrike yes that is the area I am talking about as it shows in the images on that page that you linked to just below DISKIMAGE theres an option to (show all drives) my UNetbootin does not have that for some reason

---

### Post by gandaran on 2011-11-02
you cant put any windows OS on unetbootin

---

### Post by djbigwillie on 2011-11-02
Is there a program I can use on linux to do this? I do not have a windows OS on any computer here nor at work so I am trying to do it from my Ubuntu.

---

### Post by gandaran on 2011-11-02
> **djbigwillie said:**
> Is there a program I can use on linux to do this? I do not have a windows OS on any computer here nor at work so I am trying to do it from my Ubuntu.
I don't know if windows 7 can run from live usb (sorry not actually run but using the usb drive to install to disk) you can do this with XP by just extracting the XP ISO to usb drive, no need for any install application, google the subject, there are plenty articles about it.

---

### Post by djbigwillie on 2011-11-02
Tyvm gandaran I will try that at least from there I can upgrade to the windows 7 I did not know XP did not need to be installed to the drive first I will be back after I try this :D

---

### Post by djbigwillie on 2011-11-04
Ok I tried the XP and it doesnt allow me to do that without using some kind of windows tool for it and all the tools I have seen used do not work in WINE so still at a stump

---

### Post by wojox on 2011-11-04
Try this, open Disk Utility and format to NTFS then find where your usb drive is:
```
sudo fdisk -l
```

and use the dd command:

```
sudo dd if=/Downloads/windows.iso of=/dev/sdc
```

---

