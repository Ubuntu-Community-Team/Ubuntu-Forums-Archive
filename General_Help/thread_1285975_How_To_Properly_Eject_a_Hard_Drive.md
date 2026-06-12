---
title: "How To Properly Eject a Hard Drive"
date: 2009-10-08
forum: General Help
---

### Post by ejectHD on 2009-10-08
I have a USB hard drive attached to my Ubuntu 9.04 computer. There is no "eject" option when I right click on the USB hard drive.

There is an unmount option. After I unmount how do you power down the USB powered external hard drive? I'm not going to pull the plug and damage the hard drive.

---

### Post by philinux on 2009-10-08
> **ejectHD said:**
> I have a USB hard drive attached to my Ubuntu 9.04 computer. There is no "eject" option when I right click on the USB hard drive.

There is an unmount option. After I unmount how do you power down the USB powered external hard drive? I'm not going to pull the plug and damage the hard drive.

As long as it's unmounted it can be unplugged.

---

### Post by ejectHD on 2009-10-08
Thanks for the reply but Western Digital's own website explains that the USB hard drive should be powered down before removal from the computer. How can you power down the USB hard drive from within Ubuntu 9.04?

[http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1547&p_created=1185552801&p_sid=Jnhfj6kj&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NjIsNjImcF9wcm9kcz0yMjgsMTk1LDIxMiZwX2NhdHM9JnBfcHY9My4yMTImcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9mbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD12aXN0YSBzYWZlIHJlbW92ZQ**&p_li=&p_topview=1](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1547&p_created=1185552801&p_sid=Jnhfj6kj&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NjIsNjImcF9wcm9kcz0yMjgsMTk1LDIxMiZwX2NhdHM9JnBfcHY9My4yMTImcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9mbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD12aXN0YSBzYWZlIHJlbW92ZQ**&p_li=&p_topview=1)
[I]
**Question**
Why doesn't my external hard drive power down when I use the Windows Safe Removal tool in Windows Vista?

**Answer, Problem:**
A USB connected external hard drive may not shut down properly when you use the Windows Safe Removal tool in Windows Vista.

**Cause:**
This is a known issue caused by Windows Vista and USB external devices.

**Resolution:**
Microsoft knows of this issue and is currently working on a patch or hotfix. For more information about this issue, please contact Microsoft for support at [http://support.microsoft.com](http://support.microsoft.com).
As a workaround, you will need to shut down the computer system with the hard drive attached to safely eject/dismount the hard drive.[/I]

---

### Post by Michal77 on 2009-10-12
> **philinux said:**
> As long as it's unmounted it can be unplugged.

It's not so easy. External HDD with own power supply have to be first unmount and stop. I have the same problem. Anyone found solution?
M.

---

### Post by dhughes on 2009-10-12
> **ejectHD said:**
> I have a USB hard drive attached to my Ubuntu 9.04 computer. There is no "eject" option when I right click on the USB hard drive.

There is an unmount option. After I unmount how do you power down the USB powered external hard drive? I'm not going to pull the plug and damage the hard drive.


To find its designation you could do this in Terminal ```
sudo fdisk -l
```

Yes I'd also suggest you unmount it first then, if it's /dev/sdd then do this ```
sudo eject /dev/sdd
```

You can also use that for a DVD/CD-ROM too, and if you want to close the CD tray ```
sudo eject -t /dev/sdd
```

---

### Post by Michal77 on 2009-10-13
I've found this [article]("http://ssergeje.wordpress.com/2009/08/11/unmounting-external-usb-drives-in-ubuntu/"). I'll try it soon and I'll let you know guys.
M.

---

### Post by Michal77 on 2009-10-13
I did follow instruction by [Sergei]("http://ssergeje.wordpress.com/2009/08/11/unmounting-external-usb-drives-in-ubuntu/").

I have to add:
1) You need first install sdparm.
2) If your device has name/mounting point two elements e.g. "My Book", you have to change mounting point to one element name (no space) e.g. "Book" or "MyBook".
 Them just follow Sergei's instruction. It works well just take some time to stop 500GB WD HDD.
M.

---

### Post by Michal77 on 2009-10-13
> **Michal77 said:**
> I did follow instruction by [Sergei]("http://ssergeje.wordpress.com/2009/08/11/unmounting-external-usb-drives-in-ubuntu/").

I have to add:
1) You need first install sdparm.
2) If your device has name/mounting point two elements e.g. "My Book", you have to change mounting point to one element name (no space) e.g. "Book" or "MyBook".
 Them just follow Sergei's instruction. It works well just take some time to stop 500GB WD HDD.
M.

PS.: I did test it on two devices:
1GB USB Scandisk (flash)
500GB Western Digital My Book (HDD)
Both USB 2.0

---

### Post by Michal77 on 2009-11-01
In Karmic there is no more such a problem. Enough to install gnome-mount:
```
 sudo aptitude install gnome-mount
```
This add to context menu option to safe remove (alongside of unmount) volume.
M.

---

### Post by P4man on 2009-11-01
Frankly if the filesystem is not mounted, I fail to see what harm it could possibly do to unplug the usb drive. USB is hotpluggeable after all, only mounted filesystems are not.

---

### Post by 6205 on 2009-11-01
> **ejectHD said:**
> I have a USB hard drive attached to my Ubuntu 9.04 computer. There is no "eject" option when I right click on the USB hard drive.

There is an unmount option. After I unmount how do you power down the USB powered external hard drive? I'm not going to pull the plug and damage the hard drive.

I always simply click on eject icon in Nautilus sidebar. I have WD Passport USB HDD. After "ejecting" i simply unplug it. In my case, there is no way how to power it down first. Same behavior is in Vista, so propably it's OK..

---

### Post by finesse on 2009-11-01
> **P4man said:**
> Frankly if the filesystem is not mounted, I fail to see what harm it could possibly do to unplug the usb drive. USB is hotpluggeable after all, only mounted filesystems are not.

A Hard Drive is a mechanical device, meaning it has moving parts.. to cut it's power off when it's not ready isn't good for it as they like to move their head off the drive platters when they power down for instance.

Unmounting the FS doesn't tell the HDD to prepare to be turned off.

---

### Post by P4man on 2009-11-02
> **finesse said:**
> A Hard Drive is a mechanical device, meaning it has moving parts.. to cut it's power off when it's not ready isn't good for it as they like to move their head off the drive platters when they power down for instance.

Unmounting the FS doesn't tell the HDD to prepare to be turned off.

AFAIK the last time a harddrive needed preparation for power off was like 15 years ago when we had to "park the heads"  (move the heads to a safe track before the drive spins down and its heads land on the platter). Ever since they do that automatically using a weak spring or the rotattional energy of the platter to move  the head there. 

[http://www.storagereview.com/guide2000/ref/hdd/op/actParking.html](http://www.storagereview.com/guide2000/ref/hdd/op/actParking.html)

I cant see any other reason to "prepare" a drive to be turned off, nor have I ever heard of a need to do so.

---

