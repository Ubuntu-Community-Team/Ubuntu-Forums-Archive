---
title: "Auto-brightness in Ubuntu? Like Android does."
date: 2012-08-28
forum: General Help
---

### Post by kamiller42 on 2012-08-28
Is there a program which can set my notebook's brightness based on the light in the room, like my phone does? I am using a Dell XPS 17.

I know about this idea...
[http://brainstorm.ubuntu.com/idea/13811/](http://brainstorm.ubuntu.com/idea/13811/)

Red-shift sounds almost like what I am looking for, but it changes temperature only.

---

### Post by Toz on 2012-08-28
How about f.lux ([http://stereopsis.com/flux/]("http://stereopsis.com/flux/"))? It changes the brightness based on the time of day.

---

### Post by jim_deadlock on 2012-08-28
EDIT: sorry you already tried redshift

---

### Post by Szor3n on 2012-08-28
I'm also really interested in adjusting the keyboard backlight / main screen brightness based on the ambient light sensor in my laptop.  The horribly bloated windows driver was able to do it, I just wish I could get it working with Ubuntu. D:

---

### Post by Szor3n on 2012-08-28
Better yet, I'm a fairly competent c++ programmer, how would I go about adding this functionality? or figuring out what to read from / write to to adjust the light values?

---

### Post by Toz on 2012-08-28
> **Szor3n said:**
> Better yet, I'm a fairly competent c++ programmer, how would I go about adding this functionality? or figuring out what to read from / write to to adjust the light values?

For screen backlight, you would echo values between 0 and the contents of max_brightness in your backlight interface file found at /sys/class/backlight/<interface>

For keyboard ambient backlight, there should also be a brightness file that you can manipulate (sorry I can't test it), but the location of this file would be somewhere in the /sys/devices/platform/*/leds/ directory. If you have an asus laptop, this ppa might help: [https://launchpad.net/asus-keyboard-backlight]("https://launchpad.net/asus-keyboard-backlight"). If for nothing else, the source code to accomplish this on asus laptops.

---

### Post by Szor3n on 2012-08-28
Toz, thanks for the insight,  I'm going to check that out now.  I have a Samsung laptop so that ASUS site, probably won't help, but thanks for pointing me in the right direction!

EDIT: Also, where would I look to find the sensor that reads ambient light?

---

### Post by Toz on 2012-08-28
This may not be the samsung model that you have, but check the location identified in post #15 here: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/902332]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/902332").

This might be helpful as well: [http://jablonskis.org/tag/samsung/]("http://jablonskis.org/tag/samsung/").

EDIT: And in case you didn't know, there is a samsung-specific PPA that helps fix a number of issues with samsung notebooks including brightness here: [https://launchpad.net/~voria/+archive/ppa]("https://launchpad.net/~voria/+archive/ppa")

---

### Post by Szor3n on 2012-08-28
Not the same laptop, but I can write to that file and change my keyboard backlight.  I'm going to poke around some more.  Thanks for the help!

---

### Post by kamiller42 on 2012-08-29
> **Toz said:**
> How about f.lux ([http://stereopsis.com/flux/](http://stereopsis.com/flux/))? It changes the brightness based on the time of day.
It seems focused on changing display temperature. I tried it, but it's not working on my 12.04.

I figure there was something that would read room lighting using the webcam and set the display brightness accordingly, like Android's Auto Brightness. I adjust my display manually a lot as I move from office to lower lit rooms.

---

### Post by bLaCkMeTaLL on 2012-09-08
> **kamiller42 said:**
> It seems focused on changing display temperature. I tried it, but it's not working on my 12.04.

I figure there was something that would read room lighting using the webcam and set the display brightness accordingly, like Android's Auto Brightness. I adjust my display manually a lot as I move from office to lower lit rooms.

Hi,

I installed the f.lux applet from the ppa repos and I noticed it doesn't work :)

---

