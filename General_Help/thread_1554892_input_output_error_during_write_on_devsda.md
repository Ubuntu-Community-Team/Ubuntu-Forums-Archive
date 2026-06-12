---
title: "input output error during write on /dev/sda"
date: 2010-08-17
forum: General Help
---

### Post by apoorvumang on 2010-08-17
I was installing Ubuntu 10.04 on my computer, then I got this error.
```

ERROR!!!
input output error during write on /dev/sda
```
I tried what some other threads said, but got nowhere.
Help please.

---

### Post by aeiah on 2010-08-17
doesn't sound too healthy. have you run a full disk check?

---

### Post by tripmix on 2010-08-17
Yeah, do a full disk check as soon as possible, looks like your harddrive is going bye-bye. It can be caused by any number of things, like improper shutdown, moving the disk around while it's running or dropping it or just old age or low quality/production error. It's NOT ubuntu or anything else you installed, it's very rare that code bricks your hardware.

---

### Post by apoorvumang on 2010-08-17
Well, I just installed Opensolaris without a hitch. 9.1 Karmic doesn't show this problem either (although it does show other errors because my cd drive's faulty). It's only with the 10.04 CD that I get this error.

Still, I need to install 10.04. Please help.

---

### Post by apoorvumang on 2010-08-17
> **aeiah said:**
> doesn't sound too healthy. have you run a full disk check?
btw how do I run a disk check? I don't have any OS installed. Is it possible to do that through 10.04 live CD?

---

### Post by philinux on 2010-08-17
> **apoorvumang said:**
> btw how do I run a disk check? I don't have any OS installed. Is it possible to do that through 10.04 live CD?

The error is the livecd not your HD.

Boot the livecd and at the first graphic press any key, you need to be quick. From the menu choose check cd for defects.

---

### Post by apoorvumang on 2010-08-17
> **philinux said:**
> The error is the livecd not your HD.

Boot the livecd and at the first graphic press any key, you need to be quick. From the menu choose check cd for defects.
I tried that on my laptop (which works fine), and it showed no disk problems. However, it shows errors on my desktop (the one which isn't working). Strange, but I think that's because my CD drive is a little bit faulty.
So how do I install Ubuntu?

---

### Post by apoorvumang on 2010-08-17
And one more thing, whenever I try booting from a USB (which I have done a million times before), it now shows this error:
```
Boot Error
```
Why is this happening?
Should I start a new thread for that?

EDIT : This problem's solved now.

---

### Post by apoorvumang on 2010-08-17
Well, I was able to boot from the pen drive, but I still get the same error:
```
ERROR!!!
input output error during write on /dev/sda
```
Can this be a problem with my bios settings, or is it the CD's problem?

---

