---
title: "Freetalk USB Headset profile in Pulseaudio"
date: 2010-04-24
forum: General Help
---

### Post by craig100 on 2010-04-24
Hi,

System Ubunutu 9.10x64

I've been using a Freetalk USB Headset for a while on my Sony Vaio.  It worked fine.  Did a bit of travelling and used a different USB headset.  Returned home, plugged in the Freetalk headset and find that Pulseaudio only sees the microphone part and not the speaker part.  Using PAV Volume Control Configuration, against the Freetalk headset I only get the profile options of "Analog Mono Input" or "Off". When I first set it up, ages ago, I remember getting a load of options here and set the one for input and output. How to I get more options to set up the headset properly?

Cheers,

Craig

---

### Post by P4man on 2010-04-24
Did your dog play with it while you were traveling :)

See if its still detected:

```
lsusb
```

```
aplay -l
```

---

### Post by craig100 on 2010-04-25
It's not listed by lsusb but I get the following for aplay -l:-=

card 1: Headset [FREETALK Wireless Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I don't have a dog:)  I had to adjust settings to make a different headset work while I was away, which is probably where the problem started.

---

### Post by craig100 on 2010-04-26
So is there no way to change the profile pulseaudio assigns to hardware?  It's got it wrong in this case so need to be able to set it somehow.

---

