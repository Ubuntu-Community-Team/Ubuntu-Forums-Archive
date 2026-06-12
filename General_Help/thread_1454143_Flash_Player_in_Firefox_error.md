---
title: "Flash Player in Firefox error"
date: 2010-04-14
forum: General Help
---

### Post by mtothem on 2010-04-14
Hello! i got a small problem.
My flash player doesn't work with firefox, for example youtube, it does load and all that but i cant use the controllers and when i go into flash settings controllers there does not work either.
Ive tried to re-install both firefox and flash but it still won't work.

Does anyone know what could be wrong?

OS: Ubuntu 9.10 64bit
Firefox: 3.6.3
Flash: npwrapper.libflashplayer.so // Version:   Shockwave Flash 10.0 r45

---

### Post by philinux on 2010-04-14
> **mtothem said:**
> Does anyone know what could be wrong?

OS: Ubuntu 9.10 64bit
Firefox: 3.6.3
Flash: npwrapper.libflashplayer.so // Version:   Shockwave Flash 10.0 r45

I'm using 64 bit but with the 64 bit flash plugin.

Uninstall flashplugin-nonfree and get the 64 bit version from here.

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

Extract the file libflashplayer.so and move or copy it to /home/yourusername/.mozilla/plugins

You'll have to create the plugins folder.

Thats it. Restart firefox.

---

### Post by mtothem on 2010-04-14
> **philinux said:**
> I'm using 64 bit but with the 64 bit flash plugin.

Uninstall flashplugin-nonfree and get the 64 bit version from here.

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

Extract the file libflashplayer.so and move or copy it to /home/yourusername/.mozilla/plugins

You'll have to create the plugins folder.

Thats it. Restart firefox.

it worked! :grin: Thank you very much!  :wink:

---

### Post by tom3k493 on 2010-05-08
Hi,

I have this problem but in Ubuntu 10.04, and i tried to copy the file into the directory you stated, but i realised that i dont have the 'plugins' folder.. could this be because im running 10.04 ?

And how do you un-install the current flash i have, -  through firefox itself, or ubuntu software centre ?


Thanks very much =]

---

### Post by lidex on 2010-05-08
> **tom3k493 said:**
> Hi,

I have this problem but in Ubuntu 10.04, and i tried to copy the file into the directory you stated, but i realised that i dont have the 'plugins' folder.. could this be because im running 10.04 ?

And how do you un-install the current flash i have, -  through firefox itself, or ubuntu software centre ?
Thanks very much =]

The easy answer is to go here:
[http://ubuntuforums.org/showthread.php?t=1414595]("http://ubuntuforums.org/showthread.php?t=1414595")
and use the installer

---

