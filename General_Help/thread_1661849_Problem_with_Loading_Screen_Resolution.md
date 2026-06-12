---
title: "Problem with Loading Screen Resolution"
date: 2011-01-07
forum: General Help
---

### Post by mattbrand on 2011-01-07
Hey everyone.

I just got a new laptop and installed 32-bit Ubuntu 10.10 on it, alongside Windows. I also installed Ubuntu Studio. Everything is working wonderfully, except a small issue that is not affecting performance or utility at all really, just aesthetics, but it's kinda driving me a little crazy.

On the Ubuntu loading screens, where it shows "Ubuntu" with the 4 white dots underneath on startup and shutdown, the screen resolution looks like ascii-resolution only, no graphics. And the startup and shutdown messages that appear (the ones prefixed by asterixes) show in a fixed-width font instead of the normal font that I see on my other computer, which has the same exact setup with no problems.

Anyone have any ideas?

---

### Post by coffeecat on 2011-01-07
Do you mean you installed Ubuntu Studio as a separate OS on a separate partition to Ubuntu, or did you install Ubuntu Studio within Ubuntu?

Whichever, what is your graphics card and what video driver are you using in Ubuntu (and in Ubuntu Studio if separate)? There is a known issue with the proprietary nvidia and ATI video drivers that spoils the Plymouth splash - which is what you describe. Since these are closed-source binary blobs there is nothing the Ubuntu devs can do, but there are workarounds.

---

### Post by mattbrand on 2011-01-07
I installed Ubuntu Studio within Ubuntu.

My graphics card is ATI Radeon Mobility HD 5850, and I believe that my video driver is a proprietary driver that I see in the "Additional Drivers" from the Admin. It says "ATI/AMD proprietary FGLRX graphics driver".

---

### Post by coffeecat on 2011-01-07
You have the fglrx driver. That is what is causing the issue. Have a look at this thread, post 2:

[http://ubuntuforums.org/showthread.php?t=1460324](http://ubuntuforums.org/showthread.php?t=1460324)

If that doesn't work for you, there are plenty of threads about this issue on the forums. Searching with various combinations of 'Plymouth fglrx ugly graphics' and any other way you can describe the problem will probably bring you relevant hits. I avoid the issue by using the open-source ATI driver which, with my HD4350 card, probably works better anyway.

---

### Post by mattbrand on 2011-01-07
Great. I was able to deactivate the driver through Additional Drivers, and now it looks correct.

Thanks so much for your help!

---

