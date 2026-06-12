---
title: "Dell Inspiron screen resolution, Help!"
date: 2006-04-21
forum: General Help
---

### Post by quincyjones on 2006-04-21
Hi, Please please help!
I have installed breezy badger on my Inspiron notebook (Intel 910GML chipset) but I can not get the correct screen resolution. In my preferences>screen resolution I only have the option for 1024x768. In my xorg.conf file there is absolutely no mention of 1024x768! 
It mentions all the correct resolutions in the correct places (as far as I can tell) ie: Section "Monitor" >Modeline and SubSection "Display" >Modes.

I have also run dpkg-reconfigure xserver-org (from the command line with xorg stopped), it seems to run perfectly and recognise everything but it makes no difference.

Where is the 1024x768 resolution coming from?
:confused:

---

### Post by tigrux on 2006-04-21
[QUOTE=quincyjones]Hi, Please please help!
I have installed breezy badger on my Inspiron notebook (Intel 910GML chipset) but I can not get the correct screen resolution. In my preferences>screen resolution I only have the option for 1024x768. In my xorg.conf file there is absolutely no mention of 1024x768! 
It mentions all the correct resolutions in the correct places (as far as I can tell) ie: Section "Monitor" >Modeline and SubSection "Display" >Modes.

I have also run dpkg-reconfigure xserver-org (from the command line with xorg stopped), it seems to run perfectly and recognise everything but it makes no difference.

Where is the 1024x768 resolution coming from?
:confused:[/QUOTE]

I guess your laptop has wide screen.

Use 915resolution to patch the modes the bios reports.

It's quite easy to use.
Don't forget to set /etc/default/915resolution after install it.

---

### Post by quincyjones on 2006-04-23
Thanks Tigrux,
It basically worked but this (from Peacepunk) sorted me out:
**[http://users.skynet.be/thomasvst/linux-on-laptop/](http://users.skynet.be/thomasvst/linux-on-laptop/)**
clearly other ways will work too!

---

