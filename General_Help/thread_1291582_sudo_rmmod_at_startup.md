---
title: "sudo rmmod at startup?"
date: 2009-10-14
forum: General Help
---

### Post by hvymtlsteve on 2009-10-14
Hi guys.. I have a laptop whose touchpad drives me absolutely nuts with my hands on the palmrest. Unlike my last one, there is no hardware on/off button for the touchpad :(

I use an external mouse 100% of the time so I would like to just disable it. 
I couldn't get gsynaptics to work, it kept giving me some crap about needing to set SHMconfig to 'True' which I did, and still no dice. 

For some reason the touchpad loads as a ps2 mouse, so I'm not sure if gsynaptics would work anyway, but I can disable it by opening a terminal and running:
sudo rmmod psmouse

I tried adding this command to startup programs, but no luck with that. 
I tried adding it to CRON (as root) with @reboot, no luck there either. 

Is there some other way I can reliably get this to happen on startup so I don't have to keep opening a terminal and type it in? 

cheers,

Steve

---

### Post by Rocket2DMn on 2009-10-14
You should just be able to blacklist the driver:
```
gksudo gedit /etc/modprobe.d/blacklist
```
Add in:
```
blacklist psmouse
```
Save, close, and reboot and the touchpad should be disabled.

---

### Post by hvymtlsteve on 2009-10-15
Ahh, why didn't I think of that... thank you!

If I ever want to use the touchpad I guess I'd have to undo that, but it's really not likely. 

Anyway thanks again! I'll do that when I get home. :P

---

### Post by uopjohnson on 2010-08-22
For others who find this thread it looks like this file is now:
```

/etc/modprobe.d/blacklist.conf

```

---

