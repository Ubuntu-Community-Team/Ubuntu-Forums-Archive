---
title: "Bcm4312 hardware on/off switch"
date: 2010-06-17
forum: General Help
---

### Post by Rinnblack on 2010-06-17
I realize that a lot of people are having issues with this card, I appologize if another thread is overkill.
 
I recently made the switch over to ubuntu 10.4 after getting hit with a pretty bad virus on my xp dellmini9. I switched the wlan into off mode in xp, fought with the virus for a month and decided that ubuntu was a better option, but I never turned the wireless back on. I loaded ubuntu from a usb, formating the system in the process leaving me with a healthy system, but no wireless support.
 
My wired [FONT=Lucida Console]eth0 [/FONT][FONT=Verdana]port is working but wireless still isn't after using alot of the most recent help thread's advice. I was wondering if anyone knows how to turn that kind of thing back on with out gnome's app support for the [FONT=Lucida Console]fn+2[/FONT] wireless function?[/FONT]
 
Sorry about the wall of text, I'm new to the programming side.

---

### Post by Rinnblack on 2010-06-18
bump

---

### Post by kerry_s on 2010-06-19
did you check system-> hardware drivers
some like mine needs firmware.

you need to be connected to the net for it to download & install.

---

### Post by Shazzam6999 on 2010-06-19
In a terminal 
```
iwconfig
```
figure out what interface your wireless is using (ie: wlan0)
```
iwconfig wlan0 power on
```

You might not have the correct firmware though. As far as I know 10.04 and some Broadcom cards are not that friendly.

---

