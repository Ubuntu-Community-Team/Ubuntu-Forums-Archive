---
title: "Brasero won't copy CD"
date: 2011-03-20
forum: General Help
---

### Post by timgood on 2011-03-20
I've previously been able to copy CDs using Brasero. Now when I try, the program will copy the disk, but instead of pausing to allow you to insert the destination disk, it will simply eject the disk and then quit. I can copy disks by selecting 'copy to image' and then burning the image, but this is a pain. Any suggestions as to why this is now occurring and how it may be rectified?

Thanks.

---

### Post by Tamlynmac on 2011-03-20
> timgood

I've experienced numerous issues with Brasero and after discussing it with other users found that [K3b]("http://www.k3b.org/") worked much better. After installing K3b I've never again experienced any issues when copying or creating a CD. Assuming the cd device was recognized by Ubuntu.

It's available from the software center or from the Synaptic Package Manager. You may wish to try it.

Good Luck & hope this helps.

---

### Post by billd42 on 2011-05-12
Yeah, I'm experiencing this too.  Using an alternate CD-burning application is, of course, a workaround, but it's not really a solution.

---

### Post by andrew.46 on 2011-05-12
I personally gave up on gui cd burners a while back and use commandline burning. This is not for everybody but I have published a small subset of the commands that I use which copy audio cds quite nicely:

Howto: Duplicate Audio CDs using cdrdao
[http://ubuntuforums.org/showthread.php?t=795181](http://ubuntuforums.org/showthread.php?t=795181)

Not a solution for brasero I am afraid :(.

---

### Post by krustybaguette on 2011-10-06
> **andrew.46 said:**
> I personally gave up on gui cd burners a while back and use commandline burning. This is not for everybody but I have published a small subset of the commands that I use which copy audio cds quite nicely:

Howto: Duplicate Audio CDs using cdrdao
[http://ubuntuforums.org/showthread.php?t=795181](http://ubuntuforums.org/showthread.php?t=795181)

Not a solution for brasero I am afraid :(.

I tried this but for the device information I get /dev/sr0 which results in an error at the next step. It seem to want something like your "1,0,0"
Here' what my latest attempt got me:

> Error in string constant '"1,0,0'
Error in string constant '"/1.0.0'
Cdrdao version 1.2.3 - (C) Andreas Mueller <andreas@daneb.de>
ERROR: Unable to open SCSI device /dev/sr0: Device or resource busy.
ERROR: Unable to open SCSI device (null): Bad address.
ERROR: Please use option '--device {[proto:]bus,id,lun}|device', e.g. --device 0,6,0, --device ATA:0,0,0 or --device /dev/cdrom
ERROR: Cannot setup device (null).

It's that next-to-the-last line that gets me. It seems he wants me to choose from among three or even four options to identify my device, which in human terms is a MATSHITA DVDRAM.  

Need more help. TIA

---

### Post by andrew.46 on 2011-10-06
Hmmmm..... cdrdao seems to have changed something in newer versions. What do you get with:

```
sudo cdrecord --scanbus
```

With any luck this will generate the required numbers to use with the *--device* option, although you will not be using the actual cdrecord but rather the Debian fork.

---

