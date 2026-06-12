---
title: "are &quot;Safely remove drive&quot; and &quot;Unmount&quot; the same?"
date: 2010-01-17
forum: General Help
---

### Post by ubudog on 2010-01-17
Do they both do the same thing?

---

### Post by blueridgedog on 2010-01-17
Take a look at this thread and see if it answers your question:


[http://ubuntuforums.org/showthread.php?t=1344031](http://ubuntuforums.org/showthread.php?t=1344031)

---

### Post by tom4everitt on 2010-01-17
I would say so, yes.

---

### Post by ubudog on 2010-01-17
> **blueridgedog said:**
> Take a look at this thread and see if it answers your question:


[http://ubuntuforums.org/showthread.php?t=1344031](http://ubuntuforums.org/showthread.php?t=1344031)

It does.  Thank you!

---

### Post by Leppie on 2010-01-17
I'm using Xubuntu which ships with Thunar instead of Nautilus. in thunar there's no "safely remove device" option like nautilus offers. but if i choose "unmount volume" i receive a pop-up stating "device is now safe to remove" message if this is a usb pen drive (with only 1 partition).
"safely remove device" in nautilus does not cut off the power to my usb sticks either, so for they are more or less the same (safely remove device removes the desktop icon, but i can still remount in nautilus without physically removing the usb stick).

---

### Post by ubudog on 2010-01-17
> **Leppie said:**
> I'm using Xubuntu which ships with Thunar instead of Nautilus. in thunar there's no "safely remove device" option like nautilus offers. but if i choose "unmount volume" i receive a pop-up stating "device is now safe to remove" message if this is a usb pen drive (with only 1 partition).

It's the same thing, except "Safely remove device" turns off the power to the device and "Unmount" simply unmounts it.

---

### Post by Leppie on 2010-01-17
> **ubudog said:**
> It's the same thing, except "Safely remove device" turns off the power to the device and "Unmount" simply unmounts it.
the led's of my usb stick are (and remain) happily on after using safely remove device...

---

### Post by ubudog on 2010-01-17
> **Leppie said:**
> the led's of my usb stick are (and remain) happily on after using safely remove device...

Well, as long as you unmounted it, it should be safe to remove.

---

### Post by Leppie on 2010-01-17
> **ubudog said:**
> Well, as long as you unmounted it, it should be safe to remove.
not sure if it's the same in ubuntu, but in xubuntu apparently there is no difference other than the desktop icon being removed between the two.

---

### Post by Puzzled Guy on 2010-01-17
Exactly the same

---

### Post by linuxcss on 2010-01-17
it is NOT exactly the same in all cases.

Example:

If you have attached an USB drive with more than one mount,
unmounting one may leave others still mounted ... 
where safely remove drive will attempt to unmount all mounted partitions for that drive

---

### Post by ubfu on 2010-01-31
So where can I find to command to triggered "Safely Remove Drive"I wanted it to be in 8.04 , is it hard ? I did a lot of google search but no one know to write this Safely Remove Drive command.

I just wanted to power down my external hard disk , that simple only.

---

### Post by tom4everitt on 2010-02-01
> **ubfu said:**
> So where can I find to command to triggered "Safely Remove Drive"I wanted it to be in 8.04 , is it hard ? I did a lot of google search but no one know to write this Safely Remove Drive command.

I just wanted to power down my external hard disk , that simple only.

Here is a simple bash script to achieve what you want (i.e unmounting all partitions on a certain hard drive). It should be used like this

sudo safely-remove /dev/sdb

and it will unmount all partitions on the sdb drive.

```

#!/bin/bash

# Author: Tom Everitt, tom4everitt@gmail.com
# Run as sudo
# Usage: safely-remove /dev/sdX 

for drive in $1?*; do
	if $( umount $drive ); then
		echo "unmounted $drive"
	else 
		echo "failed to unmount $drive"
	fi
done

```

just put it in a new file /usr/local/bin/safely-remove and give that file full permissions (chmod 777 /usr/local/bin/safely-remove).

Tell me how it works!

EDIT: Fixed the script to work even if some devices are already unmounted.

---

