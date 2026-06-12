---
title: "Screen cut off with Nvidia GeForce 6150"
date: 2010-09-10
forum: General Help
---

### Post by cisasteelersfan on 2010-09-10
I have an Nvidia GeForce 6150 integrated video card, and I just installed Ubuntu on my computer. I have the computer connected to a 32" LCD TV. The native resolution, according to the book, is 1366x768. I installed the latest recommended driver from the Hardware Drivers. When I open the utility, I can select 1360x768, which is pretty close I thought. I selected this and hit apply, but it cuts off both the right and left side of the screen. I can't see the Applications in the upper left corner. I went in to the TV menu and auto-adjusted, but it still cuts off both sides. Can anybody tell me what I'm doing wrong?

---

### Post by ubulal on 2010-09-10
Probably nothing.  Unfortunately many (most?) TVs don't play well with PC signals.  XGA (1024x768) works most of the time.  Could also try VGA connection if currently using HDMI or vice versa...

---

### Post by cisasteelersfan on 2010-09-10
I have a VGA connection. I had it working perfectly in Windows XP (the screen resolution was fine.) 

If I buy a discrete video card, will that fix my problem? I could hook up using HDMI.

---

### Post by ubulal on 2010-09-10
> **cisasteelersfan said:**
> I have a VGA connection. I had it working perfectly in Windows XP (the screen resolution was fine.) 

That's good! What resolution did you use in XP?  You could try another refresh rate, if possible.

> 
If I buy a discrete video card, will that fix my problem?

No one can say for sure.

---

### Post by cisasteelersfan on 2010-09-10
I'm pretty sure it was 1280x720 or 768 but it looked good. In the nvidia utility, I only have 2 options for refresh rates- 60hz or auto. Nothing changes when I change this. I have been looking around on the forums, and apparently it is called overscanning. Do you know how to correct an overscan?

---

### Post by ubulal on 2010-09-10
Can you set the resolution to 1280x720 or anything else smaller than 1366x768?  Because maybe setting the resolution to the same value as with XP makes it look as good as with XP.  But be prepared that it'll may still be not as nice as with XP, different drivers (XP vs. Linux) often use slightly different timings resulting in completely different interpretation by the display device.  You pretty much have to play around with the settings and see if any are satisfactory to you.  X Windows gurus might even be able to craft  a custom modeline that fixes all your problems.  I'm not one of them.

Overscan typically isn't limited to the horizontal dimension.

If all else fails you might try a different graphics card.

---

### Post by cisasteelersfan on 2010-09-10
Okay, thanks for your help ubulal. I'll look into modelines and timings; hopefully I can fix this.

---

### Post by Kir_B on 2010-09-10
I too, had the 6150 card integrated into my computer. It caused a similar problem; I could see the bottom right quarter of the desktop in the top left quarter of my monitor. This occurred with pretty much every Linux that I tried. I eventually installed an Nvidia 9600gt, and that solved the issue.

I hope that helps. Kirby

---

### Post by cisasteelersfan on 2010-09-11
Thanks for the responses. I actually created another thread, [http://ubuntuforums.org/showthread.php?t=1572268]("http://ubuntuforums.org/showthread.php?t=1572268"), but it was not needed. I figured it out on my own. It was a little tricky but now everything is perfect! Thanks for the responses guys.

---

