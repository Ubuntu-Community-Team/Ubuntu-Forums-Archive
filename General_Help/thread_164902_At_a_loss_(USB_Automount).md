---
title: "At a loss (USB Automount)"
date: 2006-04-23
forum: General Help
---

### Post by sameat on 2006-04-23
I have multiple usb flash/hard drives, and an mp3 player (all fat32).  I plug them in whenever I need them.  When I plug them in, I want them to mount in the same place each time respectively, preferably using the volume name.

For example: The hard drive has the volume name "bu".  I'd really like it to mount to /foo/bu every time I plug it in.  At this point, it mounts to /media/sdX1.  X is any letter between a and g depending on what else I have used during my current session.

This wouldn't be such a big deal, except that KDE is not handling things right for the flash drives.  It appears to mount the drive, and I appear to have full access.  I delete stuff and add stuff jsut like it's working fine.  However, if I remove the drive and plug it back in, none of my changes are there.  To add further confusion, the hard drive always seems to accept the changes just fine (although it would still be bice to find it in the same place each time).

It all seems to work just fine if I mount them manually as root.

I would use fstab, but I can't predict what the X in sdX will be.  

I've asked this question before, and I've seen a handful of posts with the same question, but I can't seem to find the definitive answer.

Any help would be greatly appreciated.  Even if the answer is that it is not possible, I would be happy to put thisis issue to bed.

Thanks!

---

### Post by Sutekh on 2006-04-23
Try looking into making your own rules for using [udev](http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev.html)

It allows a device to be consistently mounted in the same mount point.  You can use it in conjuction with the fstab.  

I am trying to use this currently.  I'm sure there is some useful information about using udev on the forum.

---

### Post by JohnnyLee on 2006-04-23
I just tried the instructions linked above and they work very well. Thanks.

---

### Post by Sutekh on 2006-04-24
That's great! Glad it helped.  

I don't suppose you could post the udev rule you used and how you got it to work?

---

### Post by JohnnyLee on 2006-04-24
I'm not at the same computer at the moment, but when I get back to my desktop, I'll post my rules. I followed the instructions pretty closely, and didn't have any real problems, except at first my rules file didn't have the .rules extension, so it wasn't parsed. After I got that changed it all started working. 

It really is nice to have those devices show up in the same place so you can put them in fstab.

---

### Post by sameat on 2006-04-24
So it looks like udev rules are the answer.  I also followed the [guide]("http://reactivated.net/writing_udev_rules.html") pretty closely, but I'll document it here.

1. Plug in Device
2. Determine the device node it attached itself to (I used dmesg)
```
dmesg
```
3. run:
```
sudo udevinfo -a -p /sys/block/sdX/sdX1/
```
(where sdX=where the device is attached from step 2)

4. find unique bits related to the device in the output of the above command
5. Create /etc/udev/rules.d/10-xxx.rules  (I think the xxx could be anything, but the number should be lower than 50. Not sure about that, the guide should help)
6.  Add a line to 10-xxx.rules for each device with one unique field  (from step 4 above) and symlink of your choice.  Mine ended up looking like this:
> 
[SIZE="1"]BUS=="usb", KERNEL=="sd*", SYSFS{product}=="JUMPDRIVE*", NAME="%k", SYMLINK="lexar1gb"
BUS=="usb", KERNEL=="sd*", SYSFS{product}=="Samsung*", NAME="%k", SYMLINK="mp3"
BUS=="usb", KERNEL=="sd*", SYSFS{product}=="USBX-833*", NAME="%k", SYMLINK="bu"
[/SIZE]

It looks like the reult is a unique /dev symlink for each of the three devices, eg:  /dev/lexar1gb, /dev/mp3, /dev/bu that points to the device node where it is actually connected.

I haven't altered fstab yet, but I have been able to mount each from the command line using the symlink.

I hope this is right.  It sure seemed to do what I wanted it to. 

Thanks for the pointer...it's nice to have this fixed.

---

### Post by Sutekh on 2006-04-24
Nice work sameat!!  Thanks for posting your rules and your method.

Just wanted to add a rule of mine that is slightly different
> BUS=="usb", SYSFS{product}=="TS128MJFLASHA", KERNEL=="sd?1", NAME="flash128mb", SYMLINK="usbdiscs/128mb"
The KERNEL="sd?1" will only match locations like /dev/sda1, /dev/sdb1 and more importantly, as the guide says, it won't match nodes like /dev/sda, /dev/sdb, which can be fdisk'ed.

I also used a different NAME and SYMLINK option, so that the node will be created at /dev/flash128mb, as well as a symlink /dev/usbdiscs/128mb that links to /dev/flash128mb.  I did this, mainly because I could, and so that all my usb devices will have links in /dev/usbdiscs, it just looks nicer in my fstab
```
/dev/usbdisc/128mb    /media/...
/dev/usbdisc/256mb    /media/...
/dev/usbdisc/1gb      /media/...
```
I'm a neat freak.

The guide also said that you need to use udevstart to update your new rules.  In the guide it had```
# udevstart
```the # indicates to me; a root prompt, so you need to use```
sudo udevstart
```before they take effect.


Also you should edit your link, you have [http://http//reactivated.net/writing_udev_rules.html](http://http//reactivated.net/writing_udev_rules.html), one too many http//, which takes you to Mircosoft.com 

*shudder*

---

### Post by sameat on 2006-04-24
Fixed the link, and I am going to implement your naming procedures.  The symlinks are a little too neat freakish for me.:) 

Thanks again for the assist.

---

