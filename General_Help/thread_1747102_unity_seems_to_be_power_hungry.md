---
title: "unity seems to be power hungry"
date: 2011-05-02
forum: General Help
---

### Post by Spyderkid on 2011-05-02
Since the upgrade Unity seems to be very power crazed and graphics don't run smoothly. When the launcher comes out from the side its not a smooth action, wobbly windows aren't wobbly there more like shakey windows :S. Also my screensaver doesn't run very smoothly, its quite a graphics heavy one but still none of this happened after the upgrade.
 
I have 4 cores there all running at about 20-25% min.
I have 4GB RAM
I'm not sure about the graphics card, its built in and i don't think its great.
 
 
any suggestions which will help.
I don't really won't to disable wobbly windows.

---

### Post by blitzd on 2011-05-02
> **Spyderkid said:**
> Since the upgrade Unity seems to be very power crazed and graphics don't run smoothly. When the launcher comes out from the side its not a smooth action, wobbly windows aren't wobbly there more like shakey windows :S. Also my screensaver doesn't run very smoothly, its quite a graphics heavy one but still none of this happened after the upgrade.
 
I have 4 cores there all running at about 20-25% min.
I have 4GB RAM
I'm not sure about the graphics card, its built in and i don't think its great.
 
 
any suggestions which will help.
I don't really won't to disable wobbly windows.

I have a similar issue, but it only seems to happen when my machine comes back from sleep/hibernate. My graphics card definitely should not be slowing down from any of the desktop effects, as it's fairly high end. I think the problem lies elsewhere, but I have not yet been able to track it down. I'm going to try and get rid of Unity today and see if the problem still exists with the classic desktop.

---

### Post by Spyderkid on 2011-05-02
I get it even just after i switched on the computer?!

---

### Post by collisionystm on 2011-05-02
> **Spyderkid said:**
> I get it even just after i switched on the computer?!


It sounds like theres a bug in the graphics driver. Probably the kernel in 11.04.

I suggest rolling back to 10.04 or 10.10 until 11.04 stabilizes.

---

### Post by sanderj on 2011-05-02
> **Spyderkid said:**
> Since the upgrade Unity seems to be very power crazed and graphics don't run smoothly. When the launcher comes out from the side its not a smooth action, wobbly windows aren't wobbly there more like shakey windows :S. Also my screensaver doesn't run very smoothly, its quite a graphics heavy one but still none of this happened after the upgrade.
 
I have 4 cores there all running at about 20-25% min.
I have 4GB RAM
I'm not sure about the graphics card, its built in and i don't think its great.
 
 
any suggestions which will help.
I don't really won't to disable wobbly windows.

I don't understand that last sentence, but have your tried the 11.04 "Classic Ubuntu (no effects)" login, which you can select at the bottom after you selecting your login-name (but before entering your password)?

---

### Post by []Milo on 2011-05-02
It certainly seems slow. I'm using a fairly old-ish laptop, never had problems with 10.10 and now that I've switched off Unity, everything is fine again.  Pity, as I didn't really get much of a chance to experiment with it.

---

### Post by blitzd on 2011-05-02
> **Spyderkid said:**
> I get it even just after i switched on the computer?!

The best I can offer is to suggest you do a bit of analysis on your log files. Watch for any messages that are repeating in kern.log or syslog with very short intervals between them. I did notice on at least one occasion that my slow down was because a USB device which was no longer connected kept getting polled.

If I find anything else about my own issue I'll post it back here.

---

### Post by Spyderkid on 2011-05-02
still spersists in classic, and its not phiseable to use no effects classic


and on the last line sanerj, i mean't i don't really won't to disable effects like wobbly windows to stop this problem.

---

### Post by K4NEB on 2011-05-02
mine runs fine. side bar smooth, wobbly windows all good

i only have a low end pc dual core.

the only problem i have is gwibber wont work properly

---

### Post by swappa on 2011-05-02
If you by power hungry refer to battery usage, I can confirm. My battery life has been reduced to 50% of what it is with Win7 and what it was with Maverick (dual booting). Noticed a launchpad entry on it, so I guess they're looking into it.

---

### Post by Spyderkid on 2011-05-02
no i have a desktop so i don't worry about battery

---

### Post by Spyderkid on 2011-05-07
found the solution under the compiz OpenGL plugin disable sync to Vblank

---

### Post by dino99 on 2011-05-07
[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

---

