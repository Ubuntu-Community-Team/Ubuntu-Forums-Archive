---
title: "Boot/Shutdown Messages Appearance"
date: 2010-12-21
forum: General Help
---

### Post by awp2513_ on 2010-12-21
Hi,

I'm using Ubuntu 10.04 Netbook Remix (but I'm hoping the "Netbook Remix" part won't affect the answers to my question).

During boot, reboot, and shutdown I see messages in white text with a black background, printing out information about the boot process or the process being killed, etc. 

My understanding is that this information is actually being printed by printk to /dev/console (am I way off? I haven't been able to find much info on it). 

I was wondering if it is possible to change the text color or background color, or even to set a background image during boot and shutdown. 

Some additional information:

- I'm not looking to use Plymouth, Usplash, Splashy, etc. to create a splash screen. I know it's possible to route system messages to Plymouth (at least), for display. I don't want to hide the text that appears, just change how it looks.
- I'm most interested in being able to modify the text color, but I'l take any information I can get.

I would certainly be interested to know what actually produces the messages during boot and shutdown and how that text is printed to the screen if anybody can explain it.

Thanks in advance!

---

