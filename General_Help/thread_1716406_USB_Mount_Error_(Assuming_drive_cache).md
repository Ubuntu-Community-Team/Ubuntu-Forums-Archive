---
title: "USB Mount Error (Assuming drive cache)"
date: 2011-03-28
forum: General Help
---

### Post by ondemanddesign on 2011-03-28
I have an issue where no matter what USB device I plug in (freshly formatted with FAT and FAT32) I get the following error:

```
[1107790.1554011] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[1107790.167241] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[1107790.178105] sd 8:0:0:0: [sdb] Assuming drive cache: write through

```

I then have to strike the enter key to get my ability to us BASH commands back. I run sudo fdisk -l to get a list of my devices

It says **Disk /dev/sdb: 4198 MB, 4198236160 bytes**
This is all fine and dandy but below that it says "[B]Partition 1 has different physical/logical beginnings (non-Linux?):
phys=(0, 1, 1) logical=(0, 13, 38 )[/B]"

When I mount the device it shows that the space available is only 1MB. What is going on here?

---

### Post by Omar11 on 2011-03-28
if you are using Natty Narwal Alpha or Beta, that makes sense, Alpha and Beta are NON-stable releases and are trying to be fixed and un-buggafied. So if you are using Natty, then downgrade to MAverick (atleast).
If you aren't using Natty Alpha, or beta, then I don't know what the problem is. You might have to go to [SIZE="4"]*Ubuntu documentation*[/SIZE].

---

### Post by Omar11 on 2011-03-28
> **Omar11 said:**
> if you are using Natty Narwal Alpha or Beta, that makes sense, Alpha and Beta are NON-stable releases and are trying to be fixed and un-buggafied. 
I mean it's going crappy right now.

---

### Post by newbuntuxx on 2011-03-28
Do you have any sensitive data on the usb?

If you DON'T have any sensitive data on it, then simply partition it again and format it to fat or fat32 using gpart:

```
sudo apt-get install gpart
``` 

You can access it from System - admin- gpart

Or you can re-partition and format using fdisk:

```
sudo fdisk /dev/usb_device_name
```

---

### Post by ondemanddesign on 2011-03-28
Please note, I am still able to transfer very large files onto this device once mounted and transfer it over to other Linux installs, but I would like to know why this error is generated.

---

### Post by Omar11 on 2011-03-28
> **newbuntuxx said:**
> Do you have any sensitive data on the usb?

If you DON'T have any sensitive data on it, then simply partition it again and format it to fat or fat32 using gpart:

```
sudo apt-get install gpart
``` 

You can access it from System - admin- gpart

Or you can re-partition and format using fdisk:

```
sudo fdisk /dev/usb_device_name
```

I tried fdisk before but It crashed my usb disk. Same with gpart. Gnome Format worked with me (because I use gnome! :D) And I just got it from ubuntu software centre. (Has a SD card icon pic. if you press more info.) not going against newbuntuxx's post btw.

---

### Post by Omar11 on 2011-03-28
> **ondemanddesign said:**
> Please note, I am still able to transfer very large files onto this device once mounted and transfer it over to other Linux installs, but I would like to know why this error is generated.

Just like before, you must be using natty, if not, refer to ubuntu documentation then...

---

### Post by ondemanddesign on 2011-03-28
> **Omar11 said:**
> Just like before, you must be using natty, if not, refer to ubuntu documentation then...

Using Maverick 10.10.

---

### Post by Omar11 on 2011-03-28
Ok, then you might have to refer to ubuntu documentation then.

---

