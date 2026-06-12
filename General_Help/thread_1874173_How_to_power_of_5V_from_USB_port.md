---
title: "How to power of 5V from USB port?"
date: 2011-11-02
forum: General Help
---

### Post by robgr85 on 2011-11-02
Hi!

I need to controll external device from my PC's USB, which will deliver power suply (+5V). I was looking for a way to controll it from bash (turning 5V on and off in USB socket). I've found solution for turning on and of plug-n-play usb devices:
> 
echo on|suspend >  /sys/bus/usb/devices/device/power/level


And it works like a charm, but when I connect my usb 'dummy' plug which works just as a supply of 5V current it is worthless. Do You guys know any other way of turning on/off usb line, that will work with 5V power supply from USB socket?
 
I've tried to find solution for quite a long time, but nothing works :(

---

### Post by hailtothethief on 2011-11-02
Very interesting. I love playing around with small electronics projects, particularly regarding the usb ports on my computer :)

Perhaps you need to disable wakeup as well?

```
echo disabled > /sys/bus/usb/devices/device/power/wakeup 

```

---

### Post by robgr85 on 2011-11-04
Thanks for Your suggestion, but it also didn't work. 

I've finaly decided to buy one of those simple devices, that allow to turn on and off two external devices by USB. It's based on FT232B chip and is controlled by windows software... but I believe, that I will find a way to use it under linux :>

Cheers,
Robert

---

### Post by pqwoerituytrueiwoq on 2011-11-04
this would be nice to know but not sure if possible my usb ports have power even after shut down as proven by my usb fan yet my ipod shuffle (2ed gen i think) will not charge while the computer is off

---

