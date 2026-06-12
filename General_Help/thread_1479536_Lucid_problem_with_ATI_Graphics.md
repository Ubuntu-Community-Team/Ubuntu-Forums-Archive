---
title: "Lucid problem with ATI Graphics"
date: 2010-05-10
forum: General Help
---

### Post by Elliotal on 2010-05-10
Just upgraded to Lucid,

its not a major problem, but, every time i restart the computer the visual effects keep resetting.:confused:  no idea why at all. so every time i turn it on i have to reset the visual effects. 
Any ideas on how to fix this would be very appreciated.

Cheers

---

### Post by zvacet on 2010-05-11
In applications>accessories>terminal type

```
lspci | grep VGA
```

and post output here,so somebody with same graphic card can help you.

---

### Post by Elliotal on 2010-05-11
This is what I got,


01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]


Any ideas?

---

### Post by zvacet on 2010-05-11
I´m not an expert but did you tried under system>administration>hardware drivers to install driver for your graphic card?

---

### Post by Elliotal on 2010-05-12
yeah i have my graphics card installed. the visual effects work fine. just my computer doesnt seem to save these settings and when i restart it goes back to normal.

when i start the pc, all the buttons are completely missing, i.e the close minimise and maximise. and i cannot move windows about. as soon as i put the advance visual effects on it solves all these problems. but then the restart resets them again.

---

### Post by Vakman on 2010-05-12
Try posting the output of
```
glxinfo | grep direct
```
And show us what you get. Also how did you install the drivers and from where

---

### Post by Elliotal on 2010-05-12
I get this message:

direct rendering: Yes

I installed the drivers from system>Administration>hardware drivers

Cheers for helping.

---

### Post by ryan858 on 2010-05-12
Do you have the '3D Windows' option enabled? Should be in custom settings in the Appearance app... or Compiz settings if you have that installed.

Anyway, when I enabled that option, my windows were glitched out once I rebooted... The effect doesn't work right with my ATI Radeon card, makes it look like there's no buttons, just blank spots where they should be.

So try disabling that, see if it fixes the problem...

---

### Post by Talon2 on 2010-05-12
I have a radeon 4550 card.  During alpha and beta testing of Lucid I tested with the automatically selected open source driver and with the ATI binary blob driver.  My conclusion was that I prefer the open source driver.  I run dual displays and compiz on extra.  The open source driver is totally stable here,  The performance is more than adequate.

Open source support for the radeon 4xxx cards is pretty darn good.  The one things that does need to be improved in the open source driver is power management support.  That does appear to be on the way.  The only reason I would run the binary blob driver for the 4xxx cards is if you are a gamer and need max performance or if power management is an issue.

---

### Post by webified on 2010-05-13
I have the same problem with my dell laptop.

I have tried both the open and proprietary drivers and regardless of which, each time I restart I find compositing is "temporarily disabled" and I have to re-enable. I cleaned out the drivers and reinstalled the latest from the ATI site (ati-driver-installer-10-4-x86.x86_64.run) last night but the problem persists.

This only started after upgrading to 10.04 64bit(Kubuntu).

```
$ glxinfo | grep direct
direct rendering: Yes

```

```
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
```

Any suggestions/solutions?

---

### Post by sandyd on 2010-05-13
add "compiz --replace" to the gnome startup apps.

---

### Post by spydeyrch on 2010-05-13
> **Elliotal said:**
> when i start the pc, all the buttons are completely missing, i.e the close minimise and maximise. and i cannot move windows about. as soon as i put the advance visual effects on it solves all these problems. but then the restart resets them again.

From your statement above, to me it appears that it isn't a graphics driver but actually the windows manager is not loading. So it isn't that the windows manager is "forgetting" your settings but that it isn't starting on login or boot. That is what the symptoms sound like to me.

What windows manager are you using by default? Typically, at least in my experience, ubuntu comes with the metacity windows manger. Then when you install the compiz windows manager/effects, it should take over. Also, there is the emerald themes manager.

Have you installed the compiz fusion icon? You can chose what windows manager you want active easily from that little icon/menu.

In the past, I have had a similar issue where the windows boarders and close/minimize/maximize buttons were all gone. It didn't happen during the startup but for some random reason. I had to just restart the windows manager while logged in and a couple seconds later, viola! everything good.

It sounds to me like you might need to set the deafult windows manager. I know that it should have happened automatically but things happen right.

Then again ..... I could be completely off but that is what I think it is.

-Spydey :guitar:

---

