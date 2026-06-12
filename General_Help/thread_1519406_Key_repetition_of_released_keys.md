---
title: "Key repetition of released keys"
date: 2010-06-28
forum: General Help
---

### Post by wooo on 2010-06-28
I've upgraded from 9.10 to 10.04 a few days ago.
Sometimes when I am typing on (USB) keyboard random key starts to repeat, as if I am holding it down (but I am not). Repetition stops when I press some other key. 
This is happening randomly. Sometimes 3 times in 5 minutes, sometimes once in 2 hours. I feel like it's load dependent (it occurs more often under higher load).
Does anyone have idea how to get rid of it? It is really annoying.

I am using gnome with compiz. The keyboard is autoconfigured. Xorg.0.log excerpt:
```
(II) config/udev: Adding input device CHICONY USB Keyboard (/dev/input/event7)
(**) CHICONY USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) CHICONY USB Keyboard: always reports core events
(**) CHICONY USB Keyboard: Device: "/dev/input/event7"
(II) CHICONY USB Keyboard: Found keys
(II) CHICONY USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "CHICONY USB Keyboard" (type: KEYBOARD)
```

I have tried several keyboards to prove it is not hardware issue.

---

### Post by mörgæs on 2010-06-28
Hi, welcome to the forum.

There is a bug report on the problem, but since the report was against 9.10 it is closed. Great if you would reopen it against 10.04

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/548909](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/548909)

---

### Post by wooo on 2010-06-28
I filled Bug #599316

---

### Post by ticket on 2010-08-18
I have added to bug #599316 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/599316](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/599316)
=============================
I have same problem - but in my case, once the key starts repeating, I can't stop it.
Any window that gets the focus starts receiving the endless key repeats. Hitting other keys has no effect. Only the mouse can be used, and I have to use it to restart the computer.

The bug has only appeared after a long editing session or user session. It also appears to be related to using the shift key or other key modifier. The last time this happened, I was trying to type '&' but got an endless repeat of 777777....

I have tried two different keyboards with same results - it is not a hardware fault.

I tried lowering the auto-repeat threshold and the auto-repeat frequency - bug is still there.

This bug is actually quite serious - a real show stopper. While you are editing, the threat of it appearing and forcing a restart is ever present. It can really mess up your day.

I have always been running compiz, don't know if this is a factor.

I have not been running VMware or other virtual stuff.

Release 10.04, upgraded from 9.1
Kernel 2.6.32-24-generic
GNOME 2.30.2
Keyboard : PS/2 (not a USB)

---

### Post by mörgæs on 2010-08-18
Thanks for adding to the bug report. 

Will it be possible for you to do a clean install of 10.04 for comparison?

---

### Post by ticket on 2010-08-19
> **mörgæs said:**
> Thanks for adding to the bug report. 

Will it be possible for you to do a clean install of 10.04 for comparison?

Happy to contribute, but my machine is a production PC, so I'm reluctant to do a clean install.  However, it might come to that if a bug fix doesn't come soon. Do we know of any evidence that this bug is present in a clean install?

I will be adding some more bug info to the bug report.

-----
Sorry,this is off-topic, but how are things in Iceland following the banking mess-up?

---

### Post by mörgæs on 2010-08-19
> **ticket said:**
> Do we know of any evidence that this bug is present in a clean install?


I don't know about this, but it might be interesting for the developers to know, both if it is there and if it is not. 


I'll send you a private message about Iceland.

---

