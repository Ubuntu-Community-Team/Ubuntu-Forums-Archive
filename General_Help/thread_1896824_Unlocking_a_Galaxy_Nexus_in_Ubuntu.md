---
title: "Unlocking a Galaxy Nexus in Ubuntu"
date: 2011-12-17
forum: General Help
---

### Post by happyisland on 2011-12-17
Hey guys!

Christmas came early this year, and i have a beautiful Galaxy Nexus to play with. I'm having a hard time finding straightforward guides to rooting/unlocking the bootloader though. 

Does anyone out there in Ubuntuland have a Galaxy Nexus and had any success with this?

Thanks!

It's starting to get annoying because of all the descriptions of how easy it is to do with a windows PC...

---

### Post by Mike Brennan on 2011-12-18
I have not tried this myself, so I cannot attest to it, but found it on the web:
[http://forum.xda-developers.com/showthread.php?t=883032]("http://forum.xda-developers.com/showthread.php?t=883032")

If it works out for you, let me know. I'm getting my Galaxy Nexus next week and want to try this myself.

Also found the following:
[http://android.modaco.com/topic/348161-30-nov-r3-superboot-rooting-the-gsm-lte-galaxy-nexus/]("http://android.modaco.com/topic/348161-30-nov-r3-superboot-rooting-the-gsm-lte-galaxy-nexus/")
[http://forum.xda-developers.com/showthread.php?t=1352413]("http://forum.xda-developers.com/showthread.php?t=1352413")

---

### Post by elliotn on 2011-12-18
your best bet is [www.dxa-developers.com](www.dxa-developers.com)

---

### Post by satanselbow on 2011-12-18
> **elliotn said:**
> your best bet is [www.dxa-developers.com](www.dxa-developers.com)

Think there a typo there ;)

The link should be [www.xda-developers.com](www.xda-developers.com)

A quick search there found you: [http://www.xda-developers.com/android/chainfires-cf-root-for-galaxy-nexus-released/](http://www.xda-developers.com/android/chainfires-cf-root-for-galaxy-nexus-released/)

---

### Post by happyisland on 2011-12-18
Thanks for the links everybody. I've been all over the xda, modaco, and related sites for days, and still no luck! Frustratingly, it seems like if you are using windows it is a total piece of cake, but I am unable to get fastboot to recognize my phone. Dang!

I tried the "Odin" solution in Wine and that didn't do anything either. 

I'm kind of stuck right now, and hoping there's another linux user out there with a GN that will know what works. Help!

---

### Post by elliotn on 2011-12-18
post a new thread at XDA in the nexus forums and u will get quick help

---

### Post by satanselbow on 2011-12-18
Ask on xda - there is a linux binary in the download so the dev must expect to support linux users ;)

edit: I would post in the thread I linked before as it directly relates to your issue ;)

---

### Post by happyisland on 2011-12-18
since I have fewer than 10 posts on xda forum rules won't let me post there. :(

Anyway, I'm getting to the point in the process where it seems like I need to follow this: 

"Note: If you are using a retail Galaxy Nexus, you may need to unlock the bootloader first, using './fastboot-windows oem unlock' (or the appropriate version for your machine). Note that the OEM unlock sequence wipes your device."

but when I do that (substituting fastboot-linux) with the phone connected as described, the terminal just says 'waiting for device' and doesn't do anything more. In the windows discussions it seems like there are some device drivers required to connect the phone correctly to a windows computer via usb. Might this be the problem in Ubuntu too?

---

### Post by happyisland on 2011-12-18
when connected in fastboot mode (power on while holding both volume keys) the phone is recognized in lsusb:

Bus 002 Device 040: ID 18d1:4e30 Google Inc. 

Why doesn't fastboot oem unlock work?

---

### Post by happyisland on 2011-12-18
Holy crap! I got it to unlock!

The problem was that the laptop wasn't recognizing the phone properly. When I followed the instructions here: [http://developer.android.com/guide/developing/device.html](http://developer.android.com/guide/developing/device.html) it worked first try!

SOLVED

---

### Post by nisith on 2012-05-23
Your solution is great - what's more, it probably solves a dozen more problems that I have been having with fastboot!
Thanks!

---

### Post by jacksenechal on 2013-04-18
> **happyisland said:**
> Holy crap! I got it to unlock!

The problem was that the laptop wasn't recognizing the phone properly. When I followed the instructions here: [http://developer.android.com/guide/developing/device.html](http://developer.android.com/guide/developing/device.html) it worked first try!

SOLVED

Thanks, that's exactly what I needed!

For those who want the quick answer, create a file called [FONT=Courier New]/etc/udev/rules.d/51-android.rules[/FONT] with the following content, and then run [FONT=Courier New]chmod a+r /etc/udev/rules.d/51-android.rules[/FONT].

```
SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", MODE="0666", GROUP="plugdev"
```

(Note, that's the solution for the Galaxy Nexus, but other phones may need the same treatment with slight modifications.)

---

