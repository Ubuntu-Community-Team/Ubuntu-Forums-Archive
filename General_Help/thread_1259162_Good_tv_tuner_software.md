---
title: "Good tv tuner software"
date: 2009-09-06
forum: General Help
---

### Post by bulls_eye on 2009-09-06
Can someone tell me a good tv tuning software for ubuntu 9.04...

Previously i was using KTv in windows but apparently they don't have a linux version...

not i have switched completely over to ubuntu and am unable to fine a fitting software...

i have tried tvtime but either i am unable to configure it properly or something else but it is not detecting any video signal...

---

### Post by buntunub on 2009-09-06
There are many. TvTime is usually a favorite. Mythtv is also pretty awesome, and in many cases will work where TvTime may require some configuring. In any case, getting your card setup in Linux is usually not all that difficult with a little bit of Googling and following a guide/Wiki. In some few cases though, rarely now, some cards or usb devices can be a real bear to get working in Linux if the vendor has not provided a Linux driver or if one has not yet been reverse engineered.

---

### Post by lovinglinux on 2009-09-06
I also use TVtime for watching.

If you want a lightweight media center, you could try [FoxMediaCenter]("http://fmc.isgreat.org") extension for Firefox. It has a PVR that can schedule single programme or weekly series recordings, reminders, playlist manager, xmltv support and much more. Any feedback would be much appreciated, so I can improve it.

---

### Post by bulls_eye on 2009-09-06
the problem with tvtime is wierd...
i just get a blue screen with "no signal" written in top middle and "No video" and time settings on top right...
in setup if i try to configure input i don't get any further options in the "change video source" option...
in ktv i was using pal-b as the television standard but it is not available here..

I am using a lenovo y-500 series laptop with inbuilt tv-tuner card...

please let me know if my hardware cant support it so that i dont waste any more time on this...

thanks for your responce...

---

### Post by lovinglinux on 2009-09-06
> **bulls_eye said:**
> the problem with tvtime is wierd...
i just get a blue screen with "no signal" written in top middle and "No video" and time settings on top right...
in setup if i try to configure input i don't get any further options in the "change video source" option...
in ktv i was using pal-b as the television standard but it is not available here..

I am using a lenovo y-500 series laptop with inbuilt tv-tuner card...

please let me know if my hardware cant support it so that i dont waste any more time on this...

thanks for your responce...

I have configured my card [this way](http://ubuntuforums.org/showpost.php?p=5971890&postcount=2).

---

### Post by bulls_eye on 2009-09-06
what is modprobe?
i dont understand...
when i wrote that code a blank text file opened...
i guess that means that i dont have this thing installed...

please guide me further...

---

### Post by lovinglinux on 2009-09-06
> **bulls_eye said:**
> what is modprobe?


> [modprobe](http://en.wikipedia.org/wiki/Modprobe) is a Linux program written by Rusty Russell used to add/remove a module to/from the Linux kernel (to add/remove a loadable kernel module).

> **bulls_eye said:**
> when i wrote that code a blank text file opened...

It shouldn't be blank. You must have entered the wrong code. Just copy and paste it into a terminal.

> **bulls_eye said:**
> please guide me further...

There isn't anything else to guide you, except that you need to find out your card and turner numbers, but the link to do it is broken. So you might need google your card model.

---

### Post by bulls_eye on 2009-09-06
its 100% empty...

i m not a great typing fan and if i have an option to copy paste something i love it... :-)

so how do i install modprobe??

---

### Post by lovinglinux on 2009-09-06
> **bulls_eye said:**
> its 100% empty...

i m not a great typing fan and if i have an option to copy paste something i love it... :-)

so how do i install modprobe??

Sorry. I just realized it was empty in Jaunty, but not in Hardy Heron. So, just open the that blank file and add the line suggested in the other thread. Keep in mind that the card number and the tuner won't be the same as shown in that thread. You need to find out the correct card number and tuner number according to your TV card model, otherwise it won't work. Google for your card model to find out.

You could also try to scan your channels first. If the card is already recognized, you won't need to mess with modprobe. To do that...

> Configure TVTime with the OSD menu. Some important settings:

Input Configuration > Change video source: Television
Input Configuration > Television standard: NTSC, PAL-M....
Channel Management > Change Frequency table: Cable

Then do a channel scan:

Channel Management > Scan channels for signal

This should be enough to make TVTime tune some channels.

---

### Post by Barafu Albino Cheetah on 2009-09-06
Here you go : [http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)

---

### Post by fragos on 2009-09-06
TVtime is way easy to set up if you answer the few questions presented during the install. This is the best info on TVtime I've seen [http://tvtime.sourceforge.net/](http://tvtime.sourceforge.net/).

---

### Post by bulls_eye on 2009-09-07
Oh thanks a lot lovinglinux...

you got me real worried by saying that the text file shouldn't be empty...

Only a week ago have i upgraded to 9.04 and i dont expect such errors so soon...

I will try your advice...

---

