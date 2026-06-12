---
title: "IOError: [Errno 25]"
date: 2009-11-18
forum: General Help
---

### Post by brian_hayward on 2009-11-18
I am running Mythbuntu 9.04 and I am trying to burn a DVD with mytharchive, and i get this error message:

> drivestatus = ioctl(f,CDROM.CDROM_DRIVE_STATUS, 0)
IOError: [Errno 25] Inappropriate ioctl for device


I'm still a little green at programming, I get the general sense of what the error is trying to tell me, but i dont know what i can do to trouble shoot this.  

I did some searching on the google and the bing but i couldn't find anything that would help me out with this.  It seems to me that the CDROM.CDROM_DRIVE_STATUS, doesn't look right, is CDROM.CDROM the correct syntax?

I can put DVD's in and play them with no problem...if that is of any help.  

I wasn't real sure where to post this thread, if i should try another category please let me know....any suggestions, ideas or tips are greatly appreciated...thanks.

---

### Post by Sin@Sin-Sacrifice on 2009-11-18
By default mytharchive tries to burn to /dev/dvd whereas you may have the device on /dev/cdrom or the like. You might want to look around the mythtv settings and try to tell it where to burn the disk. If it is /dev/dvd then the drive is bad. If you can't find it in the settings you could also use ```
ln -s /dev/dvd /actualdevice
``` changing "/actualdevice" to your actual device.

---

