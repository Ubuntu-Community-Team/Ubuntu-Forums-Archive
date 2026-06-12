---
title: "&quot;Removable drives and media&quot; is missing totally"
date: 2009-12-10
forum: General Help
---

### Post by jeffbiss on 2009-12-10
Hello,

I am trying to get Ubuntu 9.10 to access my USB drive and so searched for information. In that search I found references to Preferences/Removable drives and media but when I look at the listing under Preferences, there is no "Removable drives and media".

Why wouldn't it show up? What do I have to install to get it to show? I already installed all usb packages using Synaptic Package Manager thinking that it may have been part of one of those, but it doesn't appear so. Nothing told me to reboot, so perhaps it may show up.

Thanks in advance,
Jeff

---

### Post by Sin@Sin-Sacrifice on 2009-12-10
What's the output of ```
sudo fdisk -l
```?

---

### Post by hwttdz on 2009-12-10
Are you referring /usr/lib/thunar-volman/thunar-volman-settings?

Check if you right click on the menu and hit edit menu.  Then browse over to system, preferences, and check your box.  If it's not there you might have to install thunar. How did you end up with thunar in the first place?  It's usually associated with the xfce desktop.  I suppose gnome probably has something similar, but 1) I dont' know exactly it's name, and 2) it might not be named "Removable drives and media" in the menu, and I know the thunar one is.

---

### Post by jeffbiss on 2009-12-11
The output of sudo fdisk -l is (with the USB zipo drive inserted in a USB port):

[FONT=Courier New]Disk /dev/sda: 18.5 GB, 18480365568 bytes
255 heads, 63 sectors/track, 2246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e458b7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               2        2246    18032962+   f  W95 Ext'd (LBA)
/dev/sda5               2        2246    18032931    7  HPFS/NTFS

Disk /dev/sdb: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00033440

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       15017   120616020    f  W95 Ext'd (LBA)
/dev/sdb5               2       15017   120615988+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ad6b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       59686   479427763+  83  Linux
/dev/sdc2           59687       60801     8956237+   5  Extended
/dev/sdc5           59687       60801     8956206   82  Linux swap / Solaris[/FONT]

When I right-click System and check Preferences the only currently unchecked menu items are "File Management" and "Multimedia Systems Selector". My Ububtu 9.10 system shows no /usr/lib/thunar-volman, maybe because gnome was installed by default, I suppose.

I am going to check out thunar but don't know why installing Ubuntu wouldn't have installed a utility to handle USB drives in addition to regular HDs. I can go through the lower level USB stuff but think a high level tool would be nice.

Sincerely, Jeff

---

### Post by fragos on 2009-12-11
What exactly are you trying to set or control? Ubuntu 9.10 doesn't have that preferences ap anymore but the capabilities may now be in found elsewhere. Nautilus now has a Media tab in Preferences that assigns media handling.

---

### Post by jeffbiss on 2009-12-16
I am trying to enable USB because Ubuntu 9.10 didn't enable it by default at installation. Now that I know that Ubuntu no longer has the "Removable drives and media" app in Preferences, I know that I need to find another way.

---

### Post by fragos on 2009-12-16
Every USB device with storage that I plug in comes up in Nautilus mounted for access. I'm not sure what your system isn't doing.

---

### Post by itlarson on 2009-12-26
Removable media mounting in 9.10 is completely fubar.  Sometimes flash drives show up read only.  Ipods and cameras often don't show up at all. Somtimes this can be worked around by the following procedure:

-killall -9 nautilus
-plug in device
-wait 60 sec.
-start nautilus

However, this is hit or miss at best.  My friend who hates linux will give me no end of **** if he finds out it cant even handle flash drives, so hopefully this will be fixed- SOON!

---

