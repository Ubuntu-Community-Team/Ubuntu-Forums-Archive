---
title: "webcam not recognised"
date: 2012-07-14
forum: General Help
---

### Post by rdh61 on 2012-07-14
Hi,

On a fresh install of 12.04 my webcam is not recognised. All the buttons on Cheese are greyed out. If I try to open video4linux control panel, I get:

"Unable to open file /dev/video0
No such file or directory"

The webcam worked perfectly with Ubuntu 10.10. I have verified that the webcam is plugged into a working USB port.

Many thanks.

---

### Post by papibe on 2012-07-14
Could you post the result of this command?
```
lsusb
```
Regards.

---

### Post by rdh61 on 2012-07-16
Thanks for your reply.

Before I saw your message I booted up Windows XP, which is on a separate partition, and found the webcam wasn't working there either. I reinstalled it, it worked. Then I booted into Ubuntu 12.04 again, and the webcam is recognised. (Why does it take a Windows installation to make something recognisable on Ubuntu?!)

robert@robert-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 125f:c03a A-DATA Technology Co., Ltd. 
**Bus 003 Device 002: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 Webcam**

Now video4linux control panel opens correctly.

**BUT**

Cheese still has all its control buttons greyed out, and just shows a black screen whichever way I adjust the video4linux settings.

---

### Post by papibe on 2012-07-16
Have you tried the LD_PRELOAD trick? Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1984328&highlight=LD_PRELOAD").

Regards.

---

### Post by rdh61 on 2012-07-19
Yes, that makes the webcam work with Skype. Thanks.

So any idea why Cheese should still not be displaying anything, with all its control buttons greyed out?

---

### Post by rdh61 on 2012-07-20
Cheese issue is a known bug:

[https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/930671](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/930671)

So that was a red herring as far as my original issue is concerned, and I'm marking this as solved.

---

