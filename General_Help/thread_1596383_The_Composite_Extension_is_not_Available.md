---
title: "The Composite Extension is not Available"
date: 2010-10-14
forum: General Help
---

### Post by Kingmilo on 2010-10-14
Installed Ubuntu 10.10, 64bit, been working flawlessly for a week.

I have 2 nVidia Corporation G96 [GeForce 9400 GT] Graphics Cards and 2 LG Monitors. I installed the nVidia drivers from the website and everything is working very well. Using Xinerama to extend my desktop.


The problem comes in when I add an additional user to the system. It doesn't matter if it's 1 or 2 users, if they are added into the administrator group or as a desktop user, I can delete re-add them, create a completely different user but the problem persists.


As soon as I login as the new user and go to System | Preferences | Appearance | Visual Effects and try and enable either 'Normal' or Extra' I get the following error;

"The Composite Extension is not Available"


This is strange to me because composite, everything, is working fine for the default user, I have no problems whatsoever, but any additional user I setup it seems the graphics is borked, like it's not picking up the correct drivers or something.


Any ideas out there would be most appreciated, I have included a screenshot of the error attached.

Many Thanks,
milo

---

### Post by f0rcegr0wn on 2010-11-24
Same here with 32bit driver, 3 monitors and 2 nvidia cards (8800 GT & 210)

---

### Post by Kingmilo on 2010-11-24
I subsequently found out that with Xinerama enabled the composite effects do not work, this is a known bug. So to enable composite effects you need to disable Xinerama.

Cheers,
milo

---

