---
title: "Gnome-shell / clutter unusably slow."
date: 2009-10-19
forum: General Help
---

### Post by gianpa on 2009-10-19
I really can't find anything that helps me over the internet.

I just upgraded to karmic  beta and I wanted to try gnome-shell.

I installed it with no problems but when i tried to do:

gnome-shell --replace

the gnome shell showed up but it was unusably slow. I figured out it's a clutter problem because gnometris is unplayable as well. What can it be?
How can I fix clutter?

---

### Post by Giblet5 on 2009-10-19
> **gianpa said:**
> I really can't find anything that helps me over the internet.

I just upgraded to karmic  beta and I wanted to try gnome-shell.

I installed it with no problems but when i tried to do:

gnome-shell --replace

the gnome shell showed up but it was unusably slow. I figured out it's a clutter problem because gnometris is unplayable as well. What can it be?
How can I fix clutter?

Can you be more specific? What clutter?

Do you have an accelerated graphics chip? Which one? What CPU?

ALL eye candy uses resources. When the resources are used up (or not there at all) performance is poor.

---

### Post by lovinglinux on 2009-10-20
Gnome-shell concept sucks really bad IMO, but it works perfectly in regard to performance. So I guess you are using it without installing the latest graphics drivers. Go to "System >> Administration >> Hardware Drivers" and activate the proper driver for your graphics card.

---

### Post by gianpa on 2009-10-20
I use compiz so I don't think is a driver issue.

I have a geforce4 ti 4200

I'd love to be more specific but I don't know how...

I know that gnome shell uses clutter as well as gnometris and they're both as slow as hell (supposing hell is really slow). :(

---

### Post by P4man on 2009-10-20
I guess they are using sone videocard properties not supported by your videocard or driver (you have to be using the legacy nvidia drivers with that card). If you're feeling adventurous you could try the nouveau drivers.


As much as I think the concept is huge leap backwards, performance is absolutely perfect on my geforce 7 card.

---

### Post by Giblet5 on 2009-10-20
> **gianpa said:**
> I use compiz so I don't think is a driver issue.

I have a geforce4 ti 4200

I'd love to be more specific but I don't know how...

I know that gnome shell uses clutter as well as gnometris and they're both as slow as hell (supposing hell is really slow). :(

The Geforce4 ti cards were very capable cards in their day (> 5 years ago), but I suspect that this is a problem you'll have to live with until you get a card with more muscle.

Gnome-shell is smooth and fast here.

Quad-core extreme, overclocked, nvidia 280 GTX.

In a dark and musty basement somewhere - right this second - there is an ugly little troll-looking guy who's writing code that will slow my kick-butt hardware to a crawl.

And I bet it's written in Java.

---

### Post by lovinglinux on 2009-10-20
I agree with Giblet5 about your card. I forgot to mention that I have a P4 3.06 Ghz HT, 2 Gb RAM and a nvidia 7300 GT. So it's an old rig, but gnome-shell works perfectly. I guess the graphics card makes the difference. Although mine is not high-end either, the Geforce 4 series probably does not cope well with most recent demands.

---

### Post by gianpa on 2009-10-20
I guess that could be the problem. I don't have money to buy a new pc so... I'm screwed :(

Thank you for your replys.

P.S. Compiz is smooth as wather and I built gnome shell 6 months ago and it worked fine :(

---

### Post by Giblet5 on 2009-10-20
> **gianpa said:**
> I guess that could be the problem. I don't have money to buy a new pc so... I'm screwed :(

Thank you for your replys.

P.S. Compiz is smooth as wather and I built gnome shell 6 months ago and it worked fine :(

If it worked fine six months ago, maybe you have old configuration conflicts...

Try creating a new user eg, "TestGS". Log in as TestGS and start gnome-shell.

That will eliminate any old configuration garbage that you might still have in your home directory. If it works for TestGS, try to find out where gnome-shell stores its config data and move it somewhere else.

---

### Post by Yohandrys on 2009-12-12
Hey guys I am new to the linux and ubuntu software but this happens when ur Graphics card is not up to date or Ubuntu is missings the drivers...or if your card cannot handle it. It happens to me too

---

### Post by nbubis on 2010-03-06
Experiencing this problem as well - It is definitely **not** a hardware problem, since gnome-shell worked just fine in the past on my current (pretty old Intel GM965) hardware.

It seems that some upgrade broke some element of clutter or Xorg.

---

### Post by madmed on 2010-04-30
I have exactly the same problem. I filed a bug here [https://bugs.launchpad.net/ubuntu/+source/clutter-1.0/+bug/572465](https://bugs.launchpad.net/ubuntu/+source/clutter-1.0/+bug/572465) If someone could help.

---

### Post by Shutter4U on 2010-05-01
It was working for me a month or so ago and got unusably slow after an update. They must have changed something in Clutter that doesn't play well with certain (Intel atleast) graphics cards.

Anyway, on their "stuff that should work but doesn't" page, they mention a workaround for Intel-based graphics cards:

type:
```
export CLUTTER_VBLANK=none
```

before typing:
```
gnome-shell --replace
```

Worked for me, I'm now using it and it's not slow. Still not sure if I like yet.

---

### Post by P4man on 2010-05-01
Im not convinced either, but i see some good idea's. I just wonder, i can add desktop (or should that be workspaces) by clicking the + icon, but how do I remove desktops?

---

### Post by conorsulli on 2010-05-07
Well the export CLUTTER_VBLANK=none trick worked for me. But gnome shell is really annoying the way everthing is bloody jammed into that activities button :mad: a bit like windows start button... except I need to click it when I want to switch applications as well....  and it all crammed into a side pane.... :-/

Hopefully things improve... Im sure it has potential.

---

### Post by grwilmoth on 2010-05-08
gnome-shell is ridiculously slow for me as well. Running an ATI 3850. I tried the work around mentioned above for the heck of it; no dice.

---

### Post by trowe on 2010-05-10
Same here, incredibly slow, clutter_vblank=none doesn't work for me, and gnome-shell worked on the exact same system up to about a month ago.  GeForce 5200 FX card.

---

### Post by Nr90 on 2010-05-19
I realize this thread is a week old, but I just wanted to say that the export CLUTTER_VBLANK=none
workaround works for me. Not sure if I like gnome-shell so far. Looks like it has potential though.

---

### Post by federa on 2010-05-28
hey guys!
i'm using the gnome shell since two months ago and i think it's great!
only one thing..the animation are really "strange" compared to the animations with the compiz. With compiz they're fast, clean, precise...exactly the opposite with the gnome shell: rough, "slow"..
i suppose is a clutter/mutter problem...my video card (intel gma 4500HD) seems to work great so far.
the "export CLUTTER_VBLANK=none" does change nothing for me..

i'm using ubuntu 10.04, gnome shell from ppa (2.31.2), kernel 2.6.32-22, gnome 2.30.

anyone could explain to me something?

thanks!

---

### Post by sonicb00m on 2010-06-04
I have an intel chipset for my laptop graphics and the export command fixes the issue for me. I hate to disable compiz first. On my other system that didn't seem to be a prerequisite.

---

### Post by line72 on 2011-06-30
> **Shutter4U said:**
> It was working for me a month or so ago and got unusably slow after an update. They must have changed something in Clutter that doesn't play well with certain (Intel atleast) graphics cards.

Anyway, on their "stuff that should work but doesn't" page, they mention a workaround for Intel-based graphics cards:

type:
```
export CLUTTER_VBLANK=none
```

before typing:
```
gnome-shell --replace
```

Worked for me, I'm now using it and it's not slow. Still not sure if I like yet.

Thank you. This finally made gnome-shell usable on my laptop! As a note, I made this a little more permanent be creating the following file:

**/etc/profile.d/clutter.sh**
containing
```

# fix for slowness in gnome-shell
export CLUTTER_VBLANK=none

```

---

