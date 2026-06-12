---
title: "lm-sensors graphics cards"
date: 2009-07-11
forum: General Help
---

### Post by nice_like_rice on 2009-07-11
Hello :)

I'm trying to get lm-sensors to detect my nvidia hd4850 graphics card, I first ran sudo sensors-detect, but the only sensors detected were those on my CPU. How would I go about manually adding the sensors for my graphics card, I just need a push in the right direction...

thanks,

david

---

### Post by tgalati4 on 2009-07-11
I did a google search and the hd4850 is an ati (AMD) card.  Why don't you send them an email and post the results.

It has a thermal sensor:

Central thermal management &#8211; on-chip sensor monitors GPU temperature and triggers thermal actions as required

So you should be able to peek at the register to see it's value.  Maybe AMD will tell you.

---

### Post by nice_like_rice on 2009-07-11
Oops lol so it is :oops: rather embarrassing considering I built the computer myself (I just replaced the fan, I'm worried it may overheat). 

Thanks for the info - I was sure there were some kinds of sensors on there, I'll try sending them an email, I'll post any results I find.

david

---

### Post by nice_like_rice on 2009-07-11
Aha :D all a needed was that little push - searching for nvdia when I meant ati was not very good lol - the info is still well hidden though. I have found a workaround, I'm still working on getting the lm-sensors working though.

[http://ubuntuforums.org/showthread.php?t=952374](http://ubuntuforums.org/showthread.php?t=952374)

Basically, it's possible to read the values through aticonfig, but so far no luck with lm-sensors, I'll keep trying.

```
aticonfig --adapter=0 --od-gettemperature

```

---

### Post by tgalati4 on 2009-07-11
ATI was never friendly to open source developers.  Since AMD bought them, there seems to be more interest in the open source community.  Perhaps AMD will provide what is needed to the lm-sensors project to get a decent driver for it.

That ati python app looks neat.  There may be a way to feed the temperature to a file that the gnome sensors-applet can read so it will display like the rest of your temps.  You'll have to get into the details of the sensors-applet to see how they pull temperatures from lm-sensors.

It may already show up in the sensors-applet sensors list.  You have to go through and expand each one to see what sensors it picked up.  

Don't forget to add your hard disk temps using hddtemp.

---

### Post by fragos on 2009-07-12
The sensors software examines your hardware for sensors that can be monitored. I run the Hardware Sensors applet and had only been monitoring my CPU temp. My FX5200 didn't have a temp sensor. When I replaced it with an FX6200 and ran Hardware Drivers Admin a temp icon for the FX6200 GPU appeared next to my CPU temp icon. I've no idea what the ATI driver provides.

---

### Post by bobo38_fr on 2009-07-17
I'm seeking for the same thing ! Maybe you should have a look to this thread:
[http://ubuntuforums.org/showthread.php?t=952374](http://ubuntuforums.org/showthread.php?t=952374)
It seems there is a python method at the #7 !!

I'm going to try it !

---

### Post by Arup on 2009-07-17
Unless you install the proprietary drivers from the ATi site, lm-sensors won't read your card temp.

---

