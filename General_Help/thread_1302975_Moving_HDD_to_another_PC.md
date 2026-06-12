---
title: "Moving HDD to another PC?"
date: 2009-10-27
forum: General Help
---

### Post by chargersfan420 on 2009-10-27
Good day everyone,

I have two nearly identical laptops (Lenovo Ideapad Y710), with the only difference that I am aware of being processors (one is a T9300 and the other has something in the T line, lower than 9300, not sure which one yet).  

I need to send in one of them for repairs and will be without it for a couple of weeks.  What i was wondering is, can I pull the hard drive out of the one with the T9300 in it, and drop it into the other laptop and boot without any major disasters?  Keep in mind this setup will only be temporary until the repair is complete, so i don't want to have to jump through major hoops to keep this instance of Ubuntu going.

Also, are there any other critical components i should check that could cause me issues if they're not identical?

Any help or suggestions will be greatly appreciated.  Have a great day!

---

### Post by 1nooodlse on 2009-10-27
Actually, this can be accomplished very easily. If it's just one hard drive just move it over to the other computer and see if it boots up. At any rate, it won't break it.

---

### Post by chargersfan420 on 2009-10-27
Thank you for the quick reply 1nooodlse.  Yes, my biggest concern was breaking something if i tried, so it is good to know that it should be okay to try.

Actually, there are two HDD's in this laptop, but i would be ensuring that the boot order would stay the same.  I plan to move both HDD's.  

I've got a dual boot on this machine with XP, and i realize this isn't the place to ask, but i can't help but wonder if i could do the same with XP.  My gut feeling was "no, don't try it!", and if i'm restricted to Ubuntu for the two weeks, that'll be just fine, since i barely boot XP anyway.  I'm sure my XP VM in Ubuntu won't notice the difference anyway.

Thanks again!

---

### Post by chargersfan420 on 2009-10-29
Ok, I tried it and it worked great, with a couple of minor hitches:
- My network ports renamed themselves eth1 and wlan1 instead of eth0 and wlan0.  I only noticed because I use them with conky, and because my vbox VM was bridged to wlan0.  There might be a different networking chipset in this laptop, not really sure.
- XP (on vbox) started okay, but froze during shutdown, and then BSOD'd on me.  It was an easy fix with a little help from Google.

Awesome!

---

### Post by sickly on 2009-10-29
I think the thing with the wlan1 and eth 1 is that wlan0 and eth0 are still there,jst not being used cause they are the same thing with different names. and for the xp, it should work but you might have to change some drivers.

---

