---
title: "Disable webcam?"
date: 2010-04-15
forum: General Help
---

### Post by Klump on 2010-04-15
Hi,

any ideas on how to disable a webcam in Eee PC (Ubuntu 9.10, XFCE)? Whenever I disable it in BIOS it seems that Ubuntu re-enables it.

Cheers.

---

### Post by Klump on 2010-04-16
Bumpidy bump.

---

### Post by Klump on 2010-04-17
So, no ideas at all? Maybe I'll ask another question... How do I disable any device in Ubuntu? Maybe it will give me some hints :)

---

### Post by Directive 4 on 2010-04-17
this is the best way

---

### Post by Klump on 2010-04-17
Tried that without any luck. Webcam is still loading.

---

### Post by Directive 4 on 2010-04-17
it might load, but does it work;)

i'd say, disabled for sure, 

only way to be 100% sure

---

### Post by Klump on 2010-04-17
Still doesn't help my battery save energy. Maybe your way is more suitable for teens who want to hide their spotty faces and even if you had any luck with that, that's not what I'm asking. Thanks anyway :)

---

### Post by Directive 4 on 2010-04-17
very good!:lolflag:

---

### Post by talktorishav on 2010-04-17
I'm not sure on eee pc but in Lenovo Y510 I do the following:

sudo rmmod uvcvideo

or

Press the Keys Fn+Esc

I use sudo powetop to monitor my power usage.

Also to note some devices consumes more power in disabled state.

Regards,
[http://techspalace.blogspot.com](http://techspalace.blogspot.com)
(Not Only Ubuntu Blog)

---

### Post by Klump on 2010-04-17
I also use powertop. In fact, that's why I'm looking for a solution to disable it permanently :) Cheers, mate.

---

### Post by gordintoronto on 2010-04-17
Which EEE PC?

Have you checked the computer manual for a key combination?

---

### Post by Klump on 2010-04-17
Eee PC 1000. There's no key combination for the webcam.

---

### Post by libssd on 2010-08-21
> **Klump said:**
> I also use powertop. In fact, that's why I'm looking for a solution to disable it permanently :) Cheers, mate.
I have the opposite problem. I'm fairly certain that I disabled the built-in webcam on an Acer AA1 D150 using powertop, but I cannot figure out how to re-enable it. This seems to be a hardware setting, as I have the problem with 10.04, 9.04, Mint 9, and Windows XP. 

**BUT**... XP still detects the webcam, so I don't think it's a hardware problem. Windows Movie Maker reports two separate error messages:

> 
The video device is currently in use. Close any other application that is using the device and try again.

The video device cannot be started at this time because there has been an error when starting the device.

Suggestions?

---

### Post by no2498 on 2010-08-21
more of a ? but can you turn it off in the start up menu, control center

---

### Post by libssd on 2010-08-21
> **no2498 said:**
> more of a ? but can you turn it off in the start up menu, control center
Not applicable. I have two drives, a HDD and an SSD, which replaced the HDD. The HDD is partitioned between Ubuntu 9.04 and Windows, so powertop is not installed. Also Mint on an SDHC memory card, also without powertop. Webcam was disabled on 10.04, but will not work under any of the 3 devices/4 operating systems. Since I had a pre-powertop backup of 10.04, I even re-installed Ubuntu, with no change in the situation.

Something has been changed at the hardware level, but I don't see any settings for the webcam in the BIOS. I suppose I could reflash the BIOS, but I'm not sure that would do any good.

I almost never use the webcam, so this is a challenge, rather than a real problem.

---

### Post by libssd on 2010-08-21
More info, last four lines of output from dmesg | grep uvcvideo:

```

$ dmesg | grep uvcvideo
[last unloaded: uvcvideo]
[ 4407.079078] uvcvideo: Found UVC 1.00 device WebCam (0c45:62c0)
[ 4407.079821] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[ 4407.080503] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[ 4407.080514] uvcvideo: Failed to initialize the device (-5).
```
It looks like the WebCam is being detected, but can't be initialized. Since this is independent of OS, so there must be a hardware reason.

Attached is the complete output of lines containing uvcvideo from the boot process, as well as a screenshot from Cheese.

---

### Post by libssd on 2010-08-21
After running sudo modprobe -r uvcvideo  
then sudo modprobe  uvcvideo
then rebooting, dmesg is greatly cleaned up (but the webcam still doesn't work):

```

$ dmesg | grep uvcvideo
[    5.169867] uvcvideo: Found UVC 1.00 device WebCam (0c45:62c0)
[    5.176712] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[    5.178580] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[    5.178746] uvcvideo: Failed to initialize the device (-5).
[    5.178977] usbcore: registered new interface driver uvcvideo

```

---

### Post by libssd on 2010-08-22
**UPDATE**: I reflashed the BIOS 1.11 (it was already on 1.11, and this just restored BIOS settings to default values). No change. 

I'm beginning to think that powertop is a red herring, and that the webcam simply failed.

---

