---
title: "Volume Notification Display Changed?"
date: 2011-01-31
forum: General Help
---

### Post by sushman007 on 2011-01-31
When I first installed Maverick on my Dell Laptop, I had a slick-looking notification display when I changed the volume via the media buttons.

However, I made some changes to get the media buttons to control the PCM volume channel, and it now seems I'm stuck with this ugly notification that I cannot figure out how to get rid of:

[[IMG]http://i.imgur.com/3JlYR.png[/IMG]](http://imgur.com/3JlYR)

I'm not entirely sure this is what borked my original volume notification, but it was around this time I noticed the change.

Any ideas on how to get the nice display back?

---

### Post by drewsus on 2011-01-31
It might help to share exactly what you did to your computer.

---

### Post by sushman007 on 2011-01-31
Maybe!

I edited /etc/pulse/default.pa

-uncommented load-module module-alsa-sink
-added control=PCM to the above line
-added ignore-dB=1 to the line load-module module-udev-detect

I also forgot that I installed Compiz; I'm not sure if that matters...

---

### Post by sushman007 on 2011-02-04
Still looking for an answer, anyone experience something similar?

---

### Post by sushman007 on 2011-02-05
I was able to determine that Compiz is overriding NotifyOSD.  When I switch to Metacity, I get a different indicator, but not the stock one out of the box for Maverick.  Still trying to figure out how to get compiz and notify osd to play nice.

---

