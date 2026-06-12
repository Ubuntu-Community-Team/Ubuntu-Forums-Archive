---
title: "Black screen booting Natty Narwhal"
date: 2011-05-09
forum: General Help
---

### Post by erick404 on 2011-05-09
I upgraded today my Maverick to Natty Narwhal, and now I'm getting a black screen after choosing Ubuntu from the grub menu.  It goes totally black, no message or anything. Same with recovery mode.

However, grub also had an option "previous Linux versions", and this one worked (actually I'm using my Natty Narwhal right now thanks to it). 

I suspected it could have something to do with Macbuntu, since it changes so many things, but it didn't keep the said "previous Linux version" from booting. What could be wrong?

---

### Post by StepNjump on 2011-05-09
Yep, I upgraded too but even though I don't get a black screen, everything is messed up now. Cannot load my profile.. Ah! Next time it will be a clean install!

Sorry I can't help you.


> **erick404 said:**
> I upgraded today my Maverick to Natty Narwhal, and now I'm getting a black screen after choosing Ubuntu from the grub menu.  It goes totally black, no message or anything. Same with recovery mode.

However, grub also had an option "previous Linux versions", and this one worked (actually I'm using my Natty Narwhal right now thanks to it). 

I suspected it could have something to do with Macbuntu, since it changes so many things, but it didn't keep the said "previous Linux version" from booting. What could be wrong?

---

### Post by erick404 on 2011-05-10
I thought I should have done a clean install, but I just run update-manager and selected update Ubuntu version. Since it didn't ask me anything about clean install, I let it go.

---

### Post by wilee-nilee on 2011-05-10
> **erick404 said:**
> I upgraded today my Maverick to Natty Narwhal, and now I'm getting a black screen after choosing Ubuntu from the grub menu.  It goes totally black, no message or anything. Same with recovery mode.

However, grub also had an option "previous Linux versions", and this one worked (actually I'm using my Natty Narwhal right now thanks to it). 

I suspected it could have something to do with Macbuntu, since it changes so many things, but it didn't keep the said "previous Linux version" from booting. What could be wrong?

Lets assume it may be a graphics problem in that recovery gui is a safe boot low graphic boot 3rd, 4th or 5th line down you will see it boot in. If you get a cli login and the run startx to startup the desktop.

do a update and upgrade, the go to the additional drivers and look for any available.

If hyou havce had to load graphic drivers in the past then you will again probably, or the update upgrade may fix it, at least you will be able to get in.

There is a low graphic boot by editing the kernel at the grub menu.... hit e use the arrow keys to navigate to the word splash at the end of the first kernel, insert nomodeset, hit crtl-x to boot and follow the same above at the cli boot in run startx.

Hmm I missed the maverick is still there inspite, of a upgrade, this shouldn't be. 

The instructions I give though are a per-session  they don't stay. I would be careful here your description is a little on the impossible side. The only thing that could change your set up is loading any graphics drivers, from my initial instructions.

Post a screen shot of gparted I'm a bit curious if you can.

---

### Post by erick404 on 2011-05-10
> **wilee-nilee said:**
> 
Hmm I missed the maverick is still there inspite, of a upgrade, this shouldn't be. 

The instructions I give though are a per-session  they don't stay. I would be careful here your description is a little on the impossible side. The only thing that could change your set up is loading any graphics drivers, from my initial instructions.

Post a screen shot of gparted I'm a bit curious if you can.

You misunderstood: Maverick isn't there. The previous version refers to the kernel.
This upgrade is being quite a headache...

---

### Post by wilee-nilee on 2011-05-10
> **erick404 said:**
> You misunderstood: Maverick isn't there. The previous version refers to the kernel.
This upgrade is being quite a headache...

It helps to read closer sorry about that.;)

You might list the kernel that doesn't work and the one that does.

Did you try the low graphic boot-ins I described with that main kernel? Try the e=edit with a nomodeset in the kernel line at the grub menu right before of after the quiet splash.

When in natty did you run a update/upgrade, and have you also run a sudo update-grub

---

### Post by erick404 on 2011-05-10
> **wilee-nilee said:**
> It helps to read closer sorry about that.;)

You might list the kernel that doesn't work and the one that does.

Did you try the low graphic boot-ins I described with that main kernel? Try the e=edit with a nomodeset in the kernel line at the grub menu right before of after the quiet splash.

When in natty did you run a update/upgrade, and have you also run a sudo update-grub

Ok, so the first kernel in the list (which doesn't work) is 2.6.38 generic, and the working one is 2.6.35 generic.

I tried to edit the problematic entry. I wrote "nomodeset" right after "quiet splash", and nothing changed, I got a black screen (or rather purple screen). 

Now, I don't think I completely understand what you mean by update/upgrade (nor cli login). I did run sudo update-grub, and there was also update-grub2, I don't know if this means that there could be a conflict.

---

