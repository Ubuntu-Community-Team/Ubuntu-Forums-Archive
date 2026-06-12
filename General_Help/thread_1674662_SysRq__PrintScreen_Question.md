---
title: "SysRq / PrintScreen Question"
date: 2011-01-24
forum: General Help
---

### Post by teejay17 on 2011-01-24
Hello all, quick question on the ALT+SysRq REISUB command: 
Is it SysRq or PrintScreen that does the trick? The reason I ask is because I have a new ThinkPad Edge, and low-and-behold, one of the cost-saving measures was to remove the SysRq button. There's still a Print Screen button, but it is now down at the bottom, between the right-hand ALT and CTRL.
Just thought I'd inquire, and also send out a heads-up on this weird cost-saving measure.

---

### Post by AlphaLexman on 2011-01-24
> **teejay17 said:**
> the ALT+SysRq REISUB command: 
Is it SysRq or PrintScreen that does the trick? 
The Alt+SysRq key sequence is built into the kernel. I would just give it try and see if the SysRq is still mapped and just not labeled on the PrtScn button.

---

### Post by teejay17 on 2011-01-24
Yeah, I tried it out using a live CD, and it works as-per-usual. I just wanted to make 100% sure before installing that this function worked.

---

### Post by psusi on 2011-01-24
Yes, technically it is SysRq, and the kernel feature is called "the magic sysrq key".  It does not surprise me that some keyboards drop the label since the magic sysrq key is the ONLY use for it that I have ever heard of.  I still wonder why we have the scroll lock key, which to my knowledge, has never done anything either.  It would be nice if it did though.

---

### Post by skibrianski on 2011-04-23
> **psusi said:**
> Yes, technically it is SysRq, and the kernel feature is called "the magic sysrq key".  It does not surprise me that some keyboards drop the label since the magic sysrq key is the ONLY use for it that I have ever heard of.  I still wonder why we have the scroll lock key, which to my knowledge, has never done anything either.  It would be nice if it did though.

Scroll lock is for locking the scroll! When things are scrolling by too fast, hit scroll lock and take a look. The BSDs do this, probably DOS or some other old OSes too.

---

### Post by psusi on 2011-04-25
> **skibrianski said:**
> Scroll lock is for locking the scroll! When things are scrolling by too fast, hit scroll lock and take a look. The BSDs do this, probably DOS or some other old OSes too.

Neither DOS, Windows nor Linux do this.  I never tried BSD, but if they managed to actually implement it that is pretty cool.  It has irked me for 15 years now that the key has never done anything.

---

