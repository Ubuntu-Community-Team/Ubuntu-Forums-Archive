---
title: "Super dark laptop screen"
date: 2010-07-18
forum: General Help
---

### Post by Built_Well on 2010-07-18
I've had Windows XP installed on a Dell Inspiron 6000 laptop with 1 gig of ram and 70 gig hard disk.  Today I decided to install Ubuntu 10.04 desktop edition to ext3 partitions I made on the laptop's hard disk.  The Ubuntu installation went fine, and Ubuntu was up and runnning.  Then for fun, I checked the available WiFi networks in this apartment building.  Six were secure but one WiFi was open, so I clicked it out of curiosity.  Within seconds, my laptop's 15-inch screen went super-dark, nearly jet black.  I couldn't read anything on the screen. Pictures and words were still on the screen, but just way too dark to read or to see with any clarity at all.  

I don't have a WiFi card in the laptop.  Instead I use Verizon's usb727 air card on Verizon EVDO Mobile Broadband (3G)

I don't know if the free Wifi network hosed me in some way with a nasty trick (I don't have a WiFi card in the laptop--just the usb727 dongle which is an EVDO aircard), or if it was just coincidental that the screen went super dark seconds after clicking the open Wifi network in Ubuntu's network manager applet.  

When I reboot, I don't see anything anymore, not the POST, not Windows XP booting up, or Ubuntu booting up.  The only way I see anything now is to connect the laptop to an external monitor using the laptop's blue video connector.  And even then, I still can't see the boot-up POST process, or the BIOS screen.  I can only see Ubuntu or Windows XP after they've finished loading, and only on an external monitor. 

Did the new installation of Ubuntu hose my Dell Inspiron 6000 laptop's screen, or was it the Wifi network, or did the screen just coincidentally go bad minutes after I installed Ubuntu and seconds after I clicked the open Wifi connection?  

Never had this problem in Windows XP.  It all happened today after the installation of Ubuntu, which I like a lot more than Windows XP.

---

### Post by Built_Well on 2010-07-18
After reading this page:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 

I'm beginning to think Ubuntu 10.04 hosed my laptop's screen (maybe permanently).

---

### Post by The Cog on 2010-07-18
Those bug reports refer to driver problems that cause the laptop to freeze. This would be fixed by a reboot. In your case, the laptop isn't freezing because you can see it's still working with an external monitor. So I don't think that bug report has anything to do with your problems. It sound to me as though your back-light has failed. I really can't imagine that Ubuntu could cause backlight failure, so I think it's probably coincidence.

---

### Post by Built_Well on 2010-07-18
> **The Cog said:**
> Those bug reports refer to driver problems that cause the laptop to freeze. This would be fixed by a reboot. In your case, the laptop isn't freezing because you can see it's still working with an external monitor. So I don't think that bug report has anything to do with your problems. It sound to me as though your back-light has failed. I really can't imagine that Ubuntu could cause backlight failure, so I think it's probably coincidence.

Thanks for the faulty backlight suggestion, but I still can't shake the thought that Lucid Lynx is responsible for possibly pushing the backlight to extremes or jerking it around somehow.  I did notice that after I plugged the A/C adapter in after a reboot that the screen got super bright for a couple seconds, then super dark again, never to return to normal, and it all followed the installation of Lucid Lynx within minutes.

I have to say the backlight started showing a slightly red tint to it weeks before installing Lucid Lynx (all colors were shifted to the red part of the specturm a bit).  Maybe Lynx's graphic acrobatics pushed the screen to the edge and finally breaking point.  I dunno.  Just not pleased because everything else works great on this Dell Inspiron 6000.  I can't shake the idea that the Lynx pounced on me.

---

### Post by The Cog on 2010-07-19
> I can't shake the idea that the Lynx pounced on me.
You probably never will. 

Inventing the numbers, let's suppose that backlights fail on average once in 10 years. That's about a 1/3650 chance of a backlight failure on any given day. A 1/3650 chance of a backlight failure within 24 hours of your first ever Linux install. Maybe 10 million people have installed Linux. More than two thousand people will have had a backlight failure within 24 hours of their first ever Linux install. More than a hundred had a failure within an hour of installing Linux, and most of those are convinced that Linux broke their laptop.

Was it coincidence? Probably, but we can really only talk probablilities. If improbably large numbers of people had the same issue then we could infer a general problem with linux and backlights. It almost becomes an exercise in statistics and epidemiology.

Someone will probably correct my stats - I'm rubbish at stats. But I do think your fault is probably coincidence, and I also know there will always be some doubt.

---

### Post by Built_Well on 2010-07-21
Thanks, I guess it was just the backlight's time to go, and the Lynx is innocent.

---

