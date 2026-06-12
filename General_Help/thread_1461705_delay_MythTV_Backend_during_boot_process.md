---
title: "delay MythTV Backend during boot process"
date: 2010-04-24
forum: General Help
---

### Post by LowSky on 2010-04-24
When I reboot my computer I cannot see my Tuner card until I manually restart the MythTV backend.

the problem is that the backend is being started before the drivers to the tuner card (HVR-2250). is there a way to change this, thanks

I figure I should ask here as more people know there way around start up commands. I figure the easiest thing to do is to edit this file:

```
/etc/init/mythtv-backend.conf
```

I would think adding a sleep or wait command would do the trick?

Any ideas?

---

### Post by dcstar on 2010-04-25
> **LowSky said:**
> When I reboot my computer I cannot see my Tuner card until I manually restart the MythTV backend.

the problem is that the backend is being started before the drivers to the tuner card (HVR-2250). is there a way to change this, thanks
........

Look in /etc/rc2.d 

All items are started in the order you see them, change the appropriate number if you want it started later.

---

### Post by LowSky on 2010-05-01
> **dcstar said:**
> Look in /etc/rc2.d 

All items are started in the order you see them, change the appropriate number if you want it started later.

ok so I changed it to s99, instead of S20 but still no good. Can I go higher say S300?

---

### Post by snaildarter on 2010-05-18
I too am having this specific problem (running Lucid).  Would someone be kind enuf to more explicitly describe this solution?  I see no entry for mythbackend in /etc/rc2.d to alter.

---

### Post by snaildarter on 2010-05-23
So.  I'm guessing if you have upgraded from earlier versions of Ubuntu, you may not have any mythbackend entries in [COLOR="Red"]/etc/rc.2[/COLOR], like me!  At least that's my best guess as to why it's not there.

To fix this, I had to do as LowSky originally thought, and to modify [COLOR="Red"]/etc/init/mythtv-backend.conf[/COLOR].

Found the line
```
/usr/bin/mythbackend $ARGS
```
and changed it to
```
sleep 4; /usr/bin/mythbackend $ARGS
```

A sleep value of 4 was the smallest that would work for me.  Surely there is a better way to do this, but being no expert, I've spent hours on this already.  Hope this helps someone.

---

### Post by paddlehappy on 2011-05-16
> **snaildarter said:**
> 
To fix this, I had to do as LowSky originally thought, and to modify [COLOR=Red]/etc/init/mythtv-backend.conf[/COLOR].

Found the line
```
/usr/bin/mythbackend $ARGS
```and changed it to
```
sleep 4; /usr/bin/mythbackend $ARGS
```A sleep value of 4 was the smallest that would work for me.  Surely there is a better way to do this, but being no expert, I've spent hours on this already.  Hope this helps someone.

Hi,

Yep that seems to cure it for me too. Again, running lucid.  At one point I wondered if it was due to the firmware loading for the tv card (added manually to /lib/modules as tv card did not work out of box). Not sure though as this issue is recent  and didnt happen to begin with (i think). Don't know cause but the short sleep seems to sort it.

My thanks to snaildarter + lowsky

---

