---
title: "Screen blinking on boot, after fresh install"
date: 2011-07-03
forum: General Help
---

### Post by abemanden1 on 2011-07-03
Hey there ubuntu community..

I have this problem with my desktop, i installed ubuntu 11.04 on it (i tried both from live cd and usb)

Installation went smooth, but when i then try boot the computer this happens

I get the screen where i can choose

ubuntu
ubuntu recovery mode
Memory test
and so on

when i then choose to boot ubuntu

it loads the ubuntu background and then starts blinking and just freeze, the only way to stop this is by cutting the power...

i have no idea on what is causing this, so help is very appreciated.

Tell me if you need any information

Thanks

---

### Post by drs305 on 2011-07-03
abemanden1

Welcome to the Ubuntu forums.

Try selecting the recovery mode, then safe graphics. If it boots to a desktop, click on the icon at the top left of the screen. That should open "Dash". Type in "Additional Drivers" (or part of it), click on the "Additional Drivers" icon, and try to install the driver for your graphics card, if found.

If that doesn't work, reboot, press "e" to edit the top entry. Cursor to the end of the 'linux' line, remove "quiet splash vt7.handoff" or whatever is there and add **nomodeset**. Then press CTRL-x to boot and follow the procedures above to try and install a video driver.

---

### Post by abemanden1 on 2011-07-04
Thanks alot, this actually worked....

i entered graphic safe mode, and downloadeded the latest driver for my video card, and now its working like a charm :)

---

### Post by drs305 on 2011-07-04
Glad it's working. 

Marking a thread SOLVED via the 'Thread Tools' link near the top right of the first post will let helpers concentrate on unresolved issues and also point others having difficulty find threads with known solutions. Should the need arise, the 'SOLVED' tag can be removed by the original poster as well.

Happy Ubuntu-ing !

---

