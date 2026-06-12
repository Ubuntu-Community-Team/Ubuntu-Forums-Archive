---
title: "Ubuntu 10.10 and Boss GT-10"
date: 2010-10-17
forum: General Help
---

### Post by phpalpha on 2010-10-17
Hello,
This is my first post on these forums so I might as well say a warm hello to everyone here :)

I used the Boss GT-10 Guitar Effects Processor with Ubuntu 10.04 without any trouble until I upgraded to 10.10 a few days ago. The GT-10 connects through a USB Port and 10.04 recognized it as an audio device, but 10.10 does NOT. It simply does not do anything when I plug the USB in, it does not show up in the audio devices list.

I am currently running Linux Mint 9 x64 (just want to test it) so, for a while, I will be unable to try the possible solutions you guys can offer, but I WILL reply with the results ASAP.


P.S.
The unit works well on Mint 9.

P.P.S.
On 10.04, as well as on Mint 9, the unit showed up as: GT-10.


Thank you :guitar:

---

### Post by phpalpha on 2010-10-19
Bump

---

### Post by phpalpha on 2010-10-28
Bump

---

### Post by phpalpha on 2010-10-30
I'm back to Ubuntu 10.04 and everything is working perfectly. Is there anyway to see the name of the driver currently being used for GT-10?

```
lsusb
```
gives me the following
```
Bus 002 Device 005: ID 0582:00da Roland Corp.
```

the same device was listed in 10.10

---

### Post by cchhrriiss121212 on 2010-10-30
If I were you I would just stick with 10.04, as 10.10 is still a new release right now so it is still buggy.

Regarding your question, audio devices in Linux will not use drivers, they will have functionality built into the system with kernel modules. Your device will likely use the snd-usb-audio module, which is the generic module for USB devices.

If you want to try out 10.10 again, then follow step four of this guide with the module name snd-usb-audio.

---

### Post by fosf on 2010-11-10
Maybe that's the same problem as the one described here: [http://www.spinics.net/linux/fedora/alsa-user/msg09219.html](http://www.spinics.net/linux/fedora/alsa-user/msg09219.html)

---

### Post by fosf on 2011-02-20
Looking at kernel code ([http://lxr.linux.no/#linux+v2.6.35.5/sound/usb/endpoint.c#L276]("http://lxr.linux.no/#linux+v2.6.35.5/sound/usb/endpoint.c#L276")) it seems that the problem should disappear with > 2.6.35.4 kernel upgrade. I hope it will get pushed to public repos soon ;)

---

### Post by fosf on 2011-02-20
I just checked it and GT10 once again works out of the box with updated Ubuntu 10.10

---

### Post by phpalpha on 2011-02-20
> **fosf said:**
> I just checked it and GT10 once again works out of the box with updated Ubuntu 10.10
Thanks, dude! Going back to the latest Ubuntu.

---

