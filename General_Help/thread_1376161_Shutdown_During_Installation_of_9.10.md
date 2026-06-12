---
title: "Shutdown During Installation of 9.10"
date: 2010-01-08
forum: General Help
---

### Post by drpiotrowski on 2010-01-08
I'm a bit flustered here, so I would greatly appreciate any and all help! 

Upon installation of Karmic Koala, my laptop shutdown (I'm an idiot and had my AC plugged into wrong outlet [one of those where the light has to be on], and eventually the battery lost power). Upon reboot now, I get the following error:

One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/c75a8811-83ca-48c9-8d3f-80d8bfd239b2
/tmp: waiting for (null)
swap: waiting for UUID=89d9add5-91a8-4329-b2fb-8c0c420adf9a
/proc/bus/usb: waiting for usbfs

Upon attempting to enter the maintenance shell, I get the following message:
init: mountall main process (742) terminated with status 1
General error mounting filesystems.

----
Are there any steps I can take from the recovery shell to fix this error? 

Thanks so much for reading and providing any help you may provide!

---

### Post by mörgæs on 2010-01-09
It is faster and safer to install the system again  than trying to fix the bugs.

---

### Post by zey on 2010-01-09
> **mörgæs said:**
> It is faster and safer to install the system again  than trying to fix the bugs.

yes... I agree...
reinstall will is the best way..
you have nothing to lose..

---

