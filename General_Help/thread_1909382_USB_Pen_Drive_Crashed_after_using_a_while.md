---
title: "USB Pen Drive Crashed after using a while"
date: 2012-01-15
forum: General Help
---

### Post by savinthra on 2012-01-15
hello
i have installed ubuntu 11.10 and xubuntu-dektop
i logged with xubuntu-desktop environment
i plugged my usb storage device (Kingston 16GB) and was watching a movie on it.
at that time i have mounted 2 usb storage devices including the one i'm talking of.
i have unmounted one while keep the other one (the usb disk containing the movie) mounted.
after sometime i noticed the video stopped playing and both the usb storage devices have unmounted. i went to the file manager the usb device not there. so i unplugged and plugged it again but no result. then restarted the machine and try plugging it again but it doesn't work.

then i try plugging the usb storage drive on a windows machine and it ask to format the drive. when i try accessing the drive it gives the following messege,
////
The volume does not contain a recognized file system.
Please make sure that all required file system drivers are loaded and that the volume is not corrupted
///

*Please help me, i had allmost the 16GB of file space filled with a lot of important data. i still did not formatted the drive. So I highly appreciate any solution for this.

Thanks....

---

### Post by ottosykora on 2012-01-15
this may be rather difficult, as the file system on it as we do understand it (fat, ext? etc) is on it just in kind of virtual form. 

At the moment it will probably not even want to run some chkdisk  on it, thought you may try it.

You may try recovery software like photorec or recuva just to try to extract some files from it.

To run the software testdisk can be also a try, if the stick is still recognized by the system in its full size.

Did you try if the stick can be read on other computer (other hardware) or tried at least to insert it to other usb ports on same computer?

Flash sticks are still not so reliable as one thinks. Frequent backup is needed.

---

### Post by savinthra on 2012-01-15
Thanks for the reply.

The file system was fat32

~But the problem is when i plug the USB storage drive in ubuntu it doesn't show up in the file manager.
~When i go to the "Disk Utility" it shows as "Kingston DT 101 II"
and it never shows as mounted and the mount button has gone from there  for this USB storage drive. But the "Safe to remove" button is visible  and when i click it, it says
///
Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1)
///

~And when i try plugging it on windows it asks to format.

~I can't open it, see it's properties.

~I wonder why the usb drive that i work so finely just a hour before behaves like this.

PS: I experienced a slowness of detecting any USB storage device since i upgrade ubuntu from version 11.04 to 11.10, but this was the first time the USB drive get crashed.

Thanks in advance!

---

### Post by savinthra on 2012-01-15
anyone here to help me? plz...
I have almost everything i wanted in that usb pen drive and i really wanted the data so badly.

---

### Post by bluexrider on 2012-01-15
Manually mounting USB drive

[SEE THIS]("https://help.ubuntu.com/community/Mount/USB")

---

### Post by dcstar on 2012-01-16
> **savinthra said:**
> anyone here to help me? plz...
I have almost everything i wanted in that usb pen drive and i really wanted the data so badly.

All USB "pen" drives will eventually die - it is just a matter of when. It is foolish to rely on them for storage of important data.

Install the **testdisk** package and try and use that to recover any data.

---

