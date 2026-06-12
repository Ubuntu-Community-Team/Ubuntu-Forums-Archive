---
title: "Mouse problems"
date: 2010-01-16
forum: General Help
---

### Post by Cobra_MX5 on 2010-01-16
Hello everyone,

I am posting here because of a problem I seem to be having lately.  First of all, a bit of background history: I moved from Windows to Ubuntu three or four months ago, so I do not have a lot of Ubuntu (or linux in general) experience, but I know my way around a PC more or less.

So some symptoms of the problem I am having two or three days now is the following:
- Clicking twice on a tab on the lower bar to minimize and maximize a window causes the mouse to move to the center of the screen most of the times
- Super (Windows key) + mouse wheel has stopped zooming in o the desktop and instead seems like it "freezes" the mouse where it is for about a second (actually the pointer moves only a cm and returns to its initial position)
- Some times the mouse moves to random places on the screen on its own.

I cannot identify the cause of the problem, since after some search in the forums I found some similar cases (but each only mentioning one of the symptoms I have) but nothing seems to work. For the "freezing mouse" bit (2nd symptom) I read it could be related to a joypad connected, which I don't have, and for the first symptom I saw some blaming TwinView. Truth is I did actually activate twinview on my pc some days ago, but neither changing some of the settings to what worked for others nor disabling twinview altogether seems to fix the problem...

So what could it be? 
 Sorry for the long post!!!

---

### Post by Cobra_MX5 on 2010-01-16
And it seems it is happening more often now, yesterday it was barely noticeable (I just happened to try and zoom in when I noticed it didn't work), but now the mouse moves on its own much more often...

---

### Post by khelben1979 on 2010-01-16
What's the exact model of the mouse?

---

### Post by Cobra_MX5 on 2010-01-16
It's a Logitech LX7...

I don't think it is a problem of the device, although I will check if it could be caused by low battery level (it started blinking red about half an hour ago)...

Could this be the case? I mean, I have never seen this happening in windows... It is the first time I get a low battery signal since I installed Ubuntu, so there is a possibility that it is in fact the problem).

---

### Post by khelben1979 on 2010-01-16
Let it get recharged fully, then test again. If the problem remains, it could be that Linux isn't using the correct driver for the mouse.

---

### Post by Cobra_MX5 on 2010-01-16
Ok so the problem is not related to battery level or mouse driver, but to Compiz Fusion and more specifically the "Enchanced Zoom Desktop" feature.

Resetting the monitor settings to Separate X Display instead of Twinview fixed the problem (I only had disabled the second screen)...

Wow, talk about strange behavior...!

Problem solved, then, since it is the same case as others, and is considered a bug...

P.S. Thanks for the interest, though! :)

---

