---
title: "Just installed on a Toshiba Satellite A105 - very slow"
date: 2010-09-12
forum: General Help
---

### Post by linuxmonkey on 2010-09-12
Just installed Ubuntu and it is very, very slow.  For instance, I click on "System" pull-down menu and it takes about 2-3 seconds for the menu to display.  Opening Firefox takes a bit, once loaded, I start typing and noting happens.  Then the letters I typed start displaying one by one, slowly.

Any ideas?  

Specs for my system:

Toshiba Satellite A105-S1013
Processor Intel Celeron M 380 / 1.6 GHz
Chipset Type ATI Radeon Xpress 200M
512.0 MB RAM

ubuntu-10.04.1-desktop-i386

---

### Post by Lukas666 on 2010-09-12
I bet you need more RAM! Can you run "free" right after the start/boot and post it here?

---

### Post by linuxmonkey on 2010-09-12
> **Lukas666 said:**
> I bet you need more RAM! Can you run "free" right after the start/boot and post it here?

Why would WinXP run just fine but not Ubuntu?

---

### Post by Lukas666 on 2010-09-12
> **linuxmonkey said:**
> Why would WinXP run just fine but not Ubuntu?

A clean Win XP after installation takes up to 100MB of RAM. Ubuntu up to 300-400MB (tried it on my netbook a week ago).

And is your video card with shared memory?

And post here the output from "free" then we'll see.

---

### Post by linuxmonkey on 2010-09-12
> **Lukas666 said:**
> A clean Win XP after installation takes up to 100MB of RAM. Ubuntu up to 300-400MB (tried it on my netbook a week ago).

And is your video card with shared memory?

And post here the output from "free" then we'll see.

So the claims that Ubuntu can run on older hardware faster than Windows is false I guess...

---

### Post by Lukas666 on 2010-09-12
> **linuxmonkey said:**
> So the claims that Ubuntu can run on older hardware faster than Windows is false I guess...

I have both Lucid and WinXP on my 1GB netbook and WinXP is definitely faster. But still, linux has other advantages.

And keep in mind that now Ubuntu primarily competes with Windows Vista/7, not XP. In my tests and on my hardware XP is still the fastest amongst those 4. But I only mean clean installation, after a year of use this of course changes...

Sorry for this OT.

---

### Post by JoeEndUser on 2010-09-12
I am not a new linux user. I have this exact machine A105 S1013. Ubuntu 10.04 does not play well with it (Jaunty does). I've been trying like crazy to get wireless working (an atheros card). 

No fix here just wanted to give a shout that sometimes it's a particular machine that doesn't run well. Xp runs brilliantly on it.

BTW, I love Ubuntu, just not on that machine (so far).

---

### Post by JoeEndUser on 2010-09-12
Oops, BTW playing with 2 Gig of Ram here.

---

### Post by Lukas666 on 2010-09-12
> **JoeEndUser said:**
> Oops, BTW playing with 2 Gig of Ram here.

Yeah, and he has 0.5GB shared with video memory...

---

### Post by iiiears on 2010-09-12
An earlier version of Ubuntu might be a little faster.
Try disabling compiz for now and google around to see if the new open source ATI driver includes optimizations for your video card in xorg.conf

---

