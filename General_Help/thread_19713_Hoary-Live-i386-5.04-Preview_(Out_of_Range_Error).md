---
title: "Hoary-Live-i386-5.04-Preview (Out of Range Error)"
date: 2005-03-13
forum: General Help
---

### Post by mseney on 2005-03-13
At work we have Dell Optiplex GX270's with Intel 82865G Integrated Graphics. I was trying to show a few co-workers how neat Ubuntu is w/ the Hoary-Live-i386-5.04-Preview CD however after GDM starts I get the error "Out of Range". I was able to get it somewhat going after doing a $sudo dpkg-reconfigure xserver-xorg but the resolution still wasn't correct after I told it to make it 1024x768@75. I checked from within Gnome and it was set to 800x600@56. I had my Linux box in here yesterday w/ a Matrox Card attached to the same monitor and it worked fine w/ the same Live-CD. I'm guessing this is something to do w/ the Integraded Intel Graphics but how can I solve the issue so I can demo ubuntu to a few people here without luggin my PC in?

---

### Post by zorba64 on 2005-03-13
I have one of those cards and I had to change my /etc/X11/xorg.conf Section "Monitor" VertRefresh from this

VertRefresh "50-150"

to this

VertRefresh "85"

to match the refresh rate I needed for the monitor. 
I have had to do this for both installed and live versions of "Hoary"

So change it to suit the ideal refresh rate for the particular monitor and restart X and you should be good to go.

Michael

---

### Post by mseney on 2005-03-13
Okay thanks for the tip. I'll try it at work tommorow. Thanks dude! ~ Mike

---

### Post by mseney on 2005-03-14
It worked!!!!  8)

---

