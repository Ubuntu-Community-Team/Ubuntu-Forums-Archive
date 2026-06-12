---
title: "wifi kernel question"
date: 2010-06-05
forum: General Help
---

### Post by benner on 2010-06-05
I just bought 45 ASUS Eee1005PE netbooks for my school and am creating an image to load on all of the machines using Ubuntu Netbook Remix.
 
Wifi doesn't work out of the box and so I followed this thread to get them working:

[http://ubuntuforums.org/showthread.php?t=1424295&page=2](http://ubuntuforums.org/showthread.php?t=1424295&page=2)

It works fine.  But the author reminds us that we will need to run the script again each time there is a kernel update.  Well, as soon as I installed, there was a kernel update, So I am guessing that will happen a lot.  Is this driver likely to make its way into the kernel sooner or later or am I going to have problems every time we download updates?

I tried Jolicloud, Meego and a few others that had the drivers working out of the box but I think UNR is the best choice (the users will be elementary school kids.)

Thoughts?

---

### Post by Bachstelze on 2010-06-05
> **benner said:**
> Is this driver likely to make its way into the kernel sooner or later or am I going to have problems every time we download updates?

All kernels in Lucid will be based on the 2.6.32 kernel, so if a driver is not included in the Lucid kernel, it will never be.

What you can do, if you want to get rid of the "need rebuild after every update" caveat, it to use the Windows driver via ndiswrapper instead of the native Linux driver. Since ndiswrapper is just an interface between the Linux kernel and the Windows driver, it will probably not be affected by updates, so such a setup will be more update-friendly.

---

### Post by Autodave on 2010-06-05
> **benner said:**
> I just bought 45 ASUS Eee1005PE netbooks for my school and am creating an image to load on all of the machines using Ubuntu Netbook Remix.
 
Wifi doesn't work out of the box and so I followed this thread to get them working:

[http://ubuntuforums.org/showthread.php?t=1424295&page=2](http://ubuntuforums.org/showthread.php?t=1424295&page=2)

It works fine.  But the author reminds us that we will need to run the script again each time there is a kernel update.  Well, as soon as I installed, there was a kernel update, So I am guessing that will happen a lot.  Is this driver likely to make its way into the kernel sooner or later or am I going to have problems every time we download updates?

I tried Jolicloud, Meego and a few others that had the drivers working out of the box but I think UNR is the best choice (the users will be elementary school kids.)

Thoughts?

Before you do that, you might want to take a look at EEEBUNTU.  It is UBUNTU 9.04 compiled especially for Asus netbooks.  The wifi, sound card, video drivers are all there.  Also, the screen is better sized for a netbook.  I have been usuing it for a year now with no problems whatsoever.

---

