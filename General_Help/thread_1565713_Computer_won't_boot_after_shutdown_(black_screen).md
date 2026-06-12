---
title: "Computer won't boot after shutdown (black screen)"
date: 2010-09-01
forum: General Help
---

### Post by jcd29 on 2010-09-01
I have an 80GB HDD where I installed Windows XP first and then Ubuntu. The thing is that whenever I shut down my computer and then turn it back on (wether it's right away or a few hours later, or the next day), I get the GRUB screen where you have to choose Ubuntu, but after that just a completely black screen. I then have to force a shutdown, then turn it back on, and it works.

Whenever I restart it works too, this seems to happen only after a shutdown.

Specs:

Dell Dimension 4600
P4 2.8 GHz procesor
2GB RAM
ATI Radeon x1650 video card
80GB HDD

---

### Post by Rubi1200 on 2010-09-01
You might want to check the Power Management settings under System > Preferences.

Also, take a look here for booting with parameters and see if that helps:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

Perhaps also a BIOS issue?

---

### Post by jcd29 on 2010-09-02
The weird thing is it doesn't seem to happen all the time.

Right now I just got home, turned it on, and it happened. Forced a shutdown, turned it on, happened again.

Then by the third try it worked. Also, when it happens, the keyboard seems to be unresponsive. No lights, no caps lock, etc.

What could I check under power management settings?

---

### Post by Rypervenche on 2010-09-02
I had this problem on my computer when I had installed Ubuntu with Wubi on a computer with Vista. Every now and then I would get a black screen with a blinking bar at the top left and it would sit there for a long time. Sometimes when I pressed some buttoms it would explain that it wasn't working, so I would have to hard reset then it would usually work after that. I never found out why it did this though...and it wasn't all the time.

---

### Post by jcd29 on 2010-09-02
> **Rypervenche said:**
> I had this problem on my computer when I had installed Ubuntu with Wubi on a computer with Vista. Every now and then I would get a black screen with a blinking bar at the top left and it would sit there for a long time. Sometimes when I pressed some buttoms it would explain that it wasn't working, so I would have to hard reset then it would usually work after that. I never found out why it did this though...and it wasn't all the time.

This one doesn't even have the blinking bar. When I see that bar it means the splash screen is coming in a few seconds.

And this is completely unresponsive, no error message either. I don't want to keep hard resetting since I don't think that's good for my computer.

---

### Post by bcbc on 2010-09-02
I have something similar on my dell (ati x1300 card). It started happening with Lucid and it seems completely random, but with some kernels it happens frequently and others hardly ever.

I don't get a black screen, it's a band of smooshed colours, but other than that same idea - no response other than hard shutdown.

Anyhow - I believe that supplying nomodeset as a boot option avoids the problem, but can't say for sure since I kept karmic and just run lucid/maverick for testing off an external drive.

---

### Post by jcd29 on 2010-09-05
Yeah it's a little annoying. I'm trying some stuff and I'll report back to tell you what happens.

---

### Post by perspectoff on 2010-09-05
> **jcd29 said:**
> I have an 80GB HDD where I installed Windows XP first and then Ubuntu. The thing is that whenever I shut down my computer and then turn it back on (wether it's right away or a few hours later, or the next day), I get the GRUB screen where you have to choose Ubuntu, but after that just a completely black screen. I then have to force a shutdown, then turn it back on, and it works.

Whenever I restart it works too, this seems to happen only after a shutdown.

Specs:

Dell Dimension 4600
P4 2.8 GHz procesor
2GB RAM
ATI Radeon x1650 video card
80GB HDD

This has happened to me ever since they went to Plymouth as the Splash screen manager. Plymouth doesn't work with a number of graphics cards, so the screen just sits there blank and responseless for almost a minute, until the errorcode in Plymouth is generated and then it moves on. On 3 of my computers it does it to this day, although if I am patient for an extra minute or so, they eventually boot up ok.

This is a very well-known problem with the Plymouth splash screen manager, which was developed for Red Hat (like Network Manager) and forced onto Ubuntu by the Ubuntu MOTU.

Red Hat stuff doesn't always work reliably on Debian systems (another example being Kickstart), yet Ubuntu tries to use them anyway.

Add your voice to the hue and cry to fix Plymouth and Network Manager.

---

