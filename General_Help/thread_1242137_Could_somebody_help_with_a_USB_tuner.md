---
title: "Could somebody help with a USB tuner?"
date: 2009-08-16
forum: General Help
---

### Post by cptrohn on 2009-08-16
If they have the time?

I got a Hauppage WinTV-HVR 950Q that I am having trouble getting to work in linux.

I had read that someone used it with Kaffeine, but I have not been able to get it working as of yet...  When I plug it in through Kaffeine I get this error ```
DVB client: can't bind info socket
```

I have also tried to get it working with Me TV and on start up I get this error ```
Failed to scan: scanning is only supported for DVB-T and DVB - C devices
```
Ubuntu seems to recognize the device since in both apps it is listed as ```
Device: Auvitek AU8552 QAM/8YsB Frontend
```

Is there a driver that I need to install to get this configured and working in Ubuntu?

Thanks for taking the time to read..

---

### Post by cptrohn on 2009-08-17
shameless bump lol

---

### Post by cptrohn on 2009-08-17
Ok I found this at linux tv

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q)

So if I add this firmware to the device it should work correct?

---

### Post by cptrohn on 2009-08-17
Ok so I am trying to  get the firmware that works with the LinuxTV driver working as it is already in the Kernel according to the article  I put the steps listed to upgrade the firmware into a terminal as listed but when I get to this part of the terminal commands ```
cp dvb-fe-xc5000-1.1.fw /lib/firmware
```  I get this error in terminal back ```
cp: cannot create regular file `/lib/firmware/dvb-fe-xc5000-1.1.fw': Permission denied

```

So why would permission be denied to get this firmware working so I can use my device?  Any ideas?

---

### Post by cptrohn on 2009-08-17
Ok I now have the proper firmware upgrade etc....

I have scanned for channels in Kaffeine, but I haven't been able to figure out how to actually WATCH channels with it yet.... LOL

So has does anybody use this device that can recommend a good application for watching TV with it?

---

### Post by cptrohn on 2009-08-17
OK working fine in Kaffiene now...

---

### Post by cptrohn on 2009-08-19
Grrrr had it working great and then the latest Kernel upgrade just killed it....

Damn...

---

