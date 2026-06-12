---
title: "projector set up with ubuntu?"
date: 2009-09-10
forum: General Help
---

### Post by abhilashm86 on 2009-09-10
hi all, I'm giving a talk on Ubuntu with projector on screen. I've never worked with this projector, i want like this projector set up with Ubuntu,

when i start using/typing i should see the laptop, and users in front of me should see screen, how to do this?
i've a HP laptop, some said control+F4 will work, but please tell me how to do this,
thanks a lot......

---

### Post by abhilashm86 on 2009-09-10
bump!! need help

---

### Post by Chronon on 2009-09-10
Every projector I have used just behaves like an external monitor.  Can you explain what trouble you're having?  Some laptops have a key combination (on my netbook it's Fn+F8 ) that's supposed to switch the monitor configuration.  If this doesn't work you should be able to manually go into Preferences > Display and configure the monitor setup there.  You want to mirror monitors.

---

### Post by abhilashm86 on 2009-09-11
> **Chronon said:**
> Every projector I have used just behaves like an external monitor.  Can you explain what trouble you're having?  Some laptops have a key combination (on my netbook it's Fn+F8 ) that's supposed to switch the monitor configuration.  If this doesn't work you should be able to manually go into Preferences > Display and configure the monitor setup there.  You want to mirror monitors.

will Function F8 will work in ubuntu? or its hardware specfic??
i want to see display both on laptop and projector?
please first time i'm giving a demo using Ubuntu, so i don't want to things to mess up............
tell me ways to set up projector? its HP laptop

according to u, now i need to connect Screen projector,
then press F8,
or go to system->preferences->display......
is this correct........

---

### Post by The Cog on 2009-09-11
I always have to log out and in again after connecting the projector before X will admit that it's there.

---

### Post by abhilashm86 on 2009-09-11
> **The Cog said:**
> I always have to log out and in again after connecting the projector before X will admit that it's there.

can you tell in detail? does this means, when u plug in projector, then log out and restart ubuntu? then both laptop and projector will work??

---

### Post by The Cog on 2009-09-12
In System->Preferences->Screen you get a chance to choose whcih display to use, or both, or resize them etc. But I found that the Detect Monitors button still wouldn't show the newly commected projector (or tv). I had to log out and in again (not a full reboot, just restarting X) and then the screen preferences showed both screens without having to hit the Detect Monitors button.

---

### Post by abhilashm86 on 2009-09-13
> **The Cog said:**
> In System->Preferences->Screen you get a chance to choose whcih display to use, or both, or resize them etc. But I found that the Detect Monitors button still wouldn't show the newly commected projector (or tv). I had to log out and in again (not a full reboot, just restarting X) and then the screen preferences showed both screens without having to hit the Detect Monitors button.

oh thanks, this was one i needed, so after booting into ubuntu, connect plug of projector pin, log out and log in, then disaply-> detect display, hmm i'l try and leave a reply........

---

### Post by ricardisimo on 2009-09-15
Here's a somewhat related question: I want one signal for the projector, and another for the monitor. On the latter I'd like to see toolbars and video adjust options, etc. On the former (projector) just the image, period. Whatever I'm playing - powerpoint, slideshow, DVD, whatever - I'd like to be able to make adjustments on-the-fly to the presentation (brightness, color, contrast) without anyone else seeing the control panel or toolbars, just the image.

Can this be done? What app, and what configuration of connections? I'm assuming I will need a card with multiple outputs, perhaps several DVIs or an HDMI or another option. Correct? Thanks in advance for any help.

---

### Post by spiceminesofkessel on 2009-10-27
> **The Cog said:**
> I always have to log out and in again after connecting the projector before X will admit that it's there.

Thanks a lot! I have been searching high and low to get an external monitor working on a laptop using an SiS 661/741/760 or SiS 662/761Gx graphics chip/adapter. I'm a bit abashed that the solution was so simple. :D

---

### Post by P4man on 2009-10-27
> **ricardisimo said:**
> Here's a somewhat related question: I want one signal for the projector, and another for the monitor. On the latter I'd like to see toolbars and video adjust options, etc. On the former (projector) just the image, period. Whatever I'm playing - powerpoint, slideshow, DVD, whatever - I'd like to be able to make adjustments on-the-fly to the presentation (brightness, color, contrast) without anyone else seeing the control panel or toolbars, just the image.

Can this be done? What app, and what configuration of connections? I'm assuming I will need a card with multiple outputs, perhaps several DVIs or an HDMI or another option. Correct? Thanks in advance for any help.

what you describe would be the default behavior. Of course you will need a card with 2 ports (dont they all these days?)

---

