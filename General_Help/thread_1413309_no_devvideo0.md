---
title: "no /dev/video0"
date: 2010-02-22
forum: General Help
---

### Post by tubunu on 2010-02-22
I want to run my webcam on Skype and I swear it did work two days ago after running this command: 
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

Today, Skype doesn't seem to recognize the webcam any more. I found that 
```
gstreamer-properties
``` gives me a 
"Video for Linux (v4l): Device "/dev/video0" does not exist" error for both v4l and v4l2

Could someone please advise how I can bring back /dev/video0? I searched the forums but there's only outdated information for Breezy and I'm on Karmic. Please help.

---

### Post by no2498 on 2010-02-22
what does lsusb show in a terminal

gstreamer-properties is the top plugin set to x window system (no xv)

applications internet
and try the cam in ekiga softphone

---

### Post by no2498 on 2010-02-22
1 more thing i bet you had cheese open
for some reason cheese changes things

---

### Post by tubunu on 2010-02-22
```
@koala910:~$ lsusb
Bus 004 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 004: ID 046d:0870 Logitech, Inc. QuickCam Express
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by gradinaruvasile on 2010-02-22
First plug the camera out and back in after 1-2 seconds.
Then open a terminal and type:

ls -al /dev/video*

What is the output?

---

### Post by Yellow Pasque on 2010-02-22
And if you get no /dev/video device after unplugging/plugging, what does the end of dmesg say?:
```
dmesg | tail -n 20
```

---

### Post by tubunu on 2010-02-24
> **gradinaruvasile said:**
> First plug the camera out and back in after 1-2 seconds.
Then open a terminal and type:

ls -al /dev/video*

What is the output?


```
@koala910:~$ ls -al /dev/video*
ls: cannot access /dev/video*: No such file or directory
@koala910:~$ ls -al /dev/video0
ls: cannot access /dev/video0: No such file or directory

```

---

### Post by tubunu on 2010-02-24
> **Temüjin said:**
> And if you get no /dev/video device after unplugging/plugging, what does the end of dmesg say?:
```
dmesg | tail -n 20
```

```
@koala910:~$ dmesg | tail -n 20
[   20.264347]   domain 1: span 0-1 level CPU
[   20.264349]    groups: 0-1 (__cpu_power = 2048)
[   21.005015] CPU0 attaching NULL sched-domain.
[   21.005021] CPU1 attaching NULL sched-domain.
[   21.028307] CPU0 attaching sched-domain:
[   21.028311]  domain 0: span 0-1 level MC
[   21.028314]   groups: 0 1
[   21.028319] CPU1 attaching sched-domain:
[   21.028321]  domain 0: span 0-1 level MC
[   21.028324]   groups: 1 0
[   29.968257] eth0: no IPv6 routers present
[   44.437480] UDF-fs: No VRS found
[   44.437485] UDF-fs: No partition found (1)
[   44.473927] ISO 9660 Extensions: Microsoft Joliet Level 3
[   44.474820] ISOFS: changing to secondary root
[   72.689409] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[  466.656042] usb 2-2: USB disconnect, address 2
[  474.544014] usb 5-1: new full speed USB device using uhci_hcd and address 2
[  474.707971] usb 5-1: configuration #1 chosen from 1 choice
[  487.240047] usb 5-1: USB disconnect, address 2

```

---

### Post by no2498 on 2010-02-24
try running in a terminal ( lsusb )
this looks like your problem
 72.689409] process `skype' is using obsolete setsockopt SO_BSDCOMPAT

---

### Post by tubunu on 2010-02-25
```
@koala910:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:0870 Logitech, Inc. QuickCam Express
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

The camera is there, it is being recognized. The problem is that there is no /dev/video0 device available and I would like to know HOW TO ENABLE it because it did work just a few days ago (and I could see webcam image on Skype.) :confused:

What is the meaning of this and how can it be fixed?
```
process `skype' is using obsolete setsockopt SO_BSDCOMPAT 
```

---

### Post by tubunu on 2010-02-25
It's strange that there are so many google hits for "no /dev/video0" but not one answer how to fix it... :cry:

---

### Post by Yellow Pasque on 2010-02-25
> [  466.656042] usb 2-2: USB disconnect, address 2
[  474.544014] usb 5-1: new full speed USB device using uhci_hcd and address 2
[  474.707971] usb 5-1: configuration #1 chosen from 1 choice
[  487.240047] usb 5-1: USB disconnect, address 2

That last line...
Did you finally disconnect the camera or did it disconnect itself?

---

### Post by tubunu on 2010-02-25
> **Temüjin said:**
> That last line...
Did you finally disconnect the camera or did it disconnect itself?

I disconnected it.

---

### Post by no2498 on 2010-02-25
any way to try the cam on a diff computer


open applications, internet,ekiga softphone  see if it finds it

---

### Post by tubunu on 2010-02-25
I'm going to test the web cam tomorrow on a different PC though I don't understand how this would fix the missing **/dev/video0** issue.

If the web cam is being recognized as attached to the USB port it (technically) should be able to work. (thinking out loud) The problem I'm trying to describe here is connected *not* with a broken web cam, but rather with the fact that *there is no **/dev/video0***. 


_Could anyone provide a straightforward answer, please?_ 


- should I reinstall Ubuntu to get back **/dev/video0**?
- I tried Live CD and **/dev/video0** wasn't there either
- I tried installing all possible Labtec QuickCam drivers and nothing works (tried: qc-usb, gspcav1-20071224, spca5xx and countless other things)
- I've tried what *I think* might be a step forwards, but it doesn't work in the end because no matter what I do **/dev/video0** is not there: 
```
mknod **/dev/video0** c 81 0
sudo chmod 666 **/dev/video0**
ln -s **/dev/video0** /dev/video
```

Finally, why is **/dev/video0** missing from my system? 

Thank you for any insight into this.

---

### Post by Yellow Pasque on 2010-02-25
> Finally, why is /dev/video0 missing from my system? 
It's called a "bug" in the software world. ;P In theory, udev should create the block device when you plug in your webcam. Since it doesn't, and you expected it to, that's a bug. Got it?

---

### Post by tubunu on 2010-02-25
Thanks. I hope there is a workaround that bug..

---

### Post by tubunu on 2010-02-28
I upgraded from Karmic to Lucid alpha and /dev/video0 is here and the webcam "works" on Skype. "Works" because the picture isn't solid and I need to find a workaround to that. I marked the thread as SOLVED because /dev/video0 is here.

---

