---
title: "gparted resizing trouble"
date: 2012-04-07
forum: General Help
---

### Post by ZeroCool96 on 2012-04-07
I have a USB stick with Ubuntu 11.10 on it and I want to resize my disk so I can have a separate partition for backups. Everytime I boot off of that USB stick and open gparted, I resize it to what I want and then I apply the changes, after I click apply changes I get an error saying ubuntu doesn't know weither or not the disk is mounted or not. Can anyone provide any help?

---

### Post by Bucky Ball on 2012-04-07
Boot from the LiveCD, 'Try Ubuntu', open Gparted, try again.

The partitions/disks need to be unmounted to resize. If you are running Ubuntu and Gparted from the USB stick this is not the case.

To make sure the USB is unmounted (which it should be) right click it in Gparted and it will give the option to 'mount' or 'unmount'. DON'T try this running Ubuntu from the USB dongle. You won't be able to unmount it in that case.

---

### Post by ZeroCool96 on 2012-04-07
> **Bucky Ball said:**
> Boot from the LiveCD, 'Try Ubuntu', open Gparted, try again.

The partitions/disks need to be unmounted to resize. If you are running Ubuntu and Gparted from the USB stick this is not the case.

To make sure the USB is unmounted (which it should be) right click it in Gparted and it will give the option to 'mount' or 'unmount'. DON'T try this running Ubuntu from the USB dongle. You won't be able to unmount it in that case.

It tells me that the disk is unmounted because when I click unmount it says it can't be unmounted because it already is.

---

### Post by Bucky Ball on 2012-04-07
Are you doing this from the LiveCD? If not, do it and see if you get the same results.

Also, double check you are resizing the correct, unmounted partition.

I just want to get this clear in my mind:

You have Ubuntu on the USB dongle;
You are running Gparted from that and want to resize partitions on an internal drive in your desktop/laptop?
When you resize (the internal partition) using Gparted (from the USB dongle) and apply changes you get the error?

... ;)

[QUOTE=ZeroCool96]It tells me that the disk is unmounted because when I click unmount it says it can't be unmounted because it already is.[/QUOTE]

This is odd because if the partition (not disk) is unmounted already then the option available when you right click should be 'mount' rather than 'unmount'. This would suggest that there is no option to mount the disk if you wanted to (unless you use the terminal to do so). 'Mount' should be the right-click option so the plot thickens ...

---

### Post by ZeroCool96 on 2012-04-08
Here's images on everything.

**This is me trying to mount the partition (it's currently unmounted)**
[IMG]http://i54.photobucket.com/albums/g105/zyphfx/mount.png[/IMG]

**This is the partition I made (it's called New Partition)**
[IMG]http://i54.photobucket.com/albums/g105/zyphfx/newpartition.png[/IMG]

**Here's it telling me an error occured**
[IMG]http://i54.photobucket.com/albums/g105/zyphfx/erroroccured.png[/IMG]

**Here's the error message itself**
[IMG]http://i54.photobucket.com/albums/g105/zyphfx/errormessage.png[/IMG]

---

### Post by Bucky Ball on 2012-04-08
Very odd. Try deleting /dev/sda5, applying it, then try again. The unknown partition might be confusing things re mount/unmount. You might try searching for that error message if that doesn't work. Or ... 

If just installed I would be tempted to reinstall but this time, when you get to the partitioning section, choose 'Something Else' and manually partition it the way you want it. 

Make a plan before starting.

One other point: you have no /swap partition there ... You should have (2Gb is fine).

PS: Well done with the screen shots. Very clear now. ;)

---

### Post by ZeroCool96 on 2012-04-08
> **Bucky Ball said:**
> Very odd. Try deleting /dev/sda5, applying it, then try again. The unknown partition might be confusing things re mount/unmount. You might try searching for that error message if that doesn't work. Or ... 


I deleted the unknown partition and then tried to mount/unmount /dev/sda1 but it wouldn't allow it so I just partitioned it how I wanted and applied. Still nothing.

**I have no unknown drive:**
[IMG]http://i54.photobucket.com/albums/g105/zyphfx/nounknowndrive.png[/IMG]

**Here's the error again:**
[IMG]http://i54.photobucket.com/albums/g105/zyphfx/error2.png[/IMG]

**Here's what else is getting an error:**
[IMG]http://i54.photobucket.com/albums/g105/zyphfx/error22.png[/IMG]

> **Bucky Ball said:**
> PS: Well done with the screen shots. Very clear now. ;)

Thanks! I thought they would help a little!

---

