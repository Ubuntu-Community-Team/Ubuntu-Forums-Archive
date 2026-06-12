---
title: "No wireless on toshiba sat p108 notebook"
date: 2010-08-29
forum: General Help
---

### Post by hatewindows on 2010-08-29
Just installed 10.04 on a clean HD-i cant get the wireless to work--Any fixes? I see that i have an intel wireless card WM3945ABG--Worked in windows--Thanks for any help---have a great day!!!!

---

### Post by meditatingfrog on 2010-08-29
> **hatewindows said:**
> Just installed 10.04 on a clean HD-i cant get the wireless to work--Any fixes? I see that i have an intel wireless card WM3945ABG--Worked in windows--Thanks for any help---have a great day!!!!

Hey, hatewindows.  You might have to try using a program called "ndiswrapper".  You can use it to install a windows driver for your intel chip.  I know, it's kind of messed up, but you may have to wait until a developer gets around to writing a driver for your wireless chipset.  

You could search google for "intel wireless wm3945abg linux driver".  Maybe intel has a linux driver that you can install.

I'm not sure about your specific wireless card, but I have a toshiba u305-s7448, and my atheros chip didn't have a native linux driver until intrepid.  So, you may have to use ndiswrapper if intel hasn't written a linux driver for your wireless chip.  

So, to recap:

1.  check if intel has a linux driver for your wireless chip.  If they do, try installing.
2.  If not, install ndiswrapper, and use a windows driver until a linux driver becomes available.

---

### Post by hatewindows on 2010-08-29
Thanks for all the info!!!! I'll give it a try--and you have a great eve!!!! Thank you!

---

