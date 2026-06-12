---
title: "disable keypad while typing not work"
date: 2012-06-29
forum: General Help
---

### Post by chapra on 2012-06-29
Hi, I just installed ubuntu 11.10 on my hp laptop as a dual boot, and I can't get it to disable my keypad while typing.  I went to system settings ->mouse and touchpad->disable touchpad while typing and it's checked, but the touchpad doesn't get disabled, either the buttons, the tap function, or the scrolling with fingers.  

I thought maybe it was an issue of the time delay, but when I try to access syndaemon through my command screen, the screen just freezes, and I need to press control-C to regain control.

This may be a related issue, but with this laptop, I originally had ubuntu 10.04 installed, and I had a similar situation with getting the numeric keypad to control the pointer: i could check off the box, but it didn't actually work.  That was part of the reason I replaced it with 11.10

---

### Post by sudodus on 2012-06-29
I use touchpad-indicator in Lubuntu 12.04 and it works nicely. See this link (the link is old, but touchpad-indicator is alive and works in 12.04)

[[COLOR="Red"]_http://ubuntuguide.net/quickly-enabledisable-laptop-touchpad-with-touchpad-indicator-in-ubuntu-10-10_[/COLOR]]("http://ubuntuguide.net/quickly-enabledisable-laptop-touchpad-with-touchpad-indicator-in-ubuntu-10-10")

---

### Post by chapra on 2012-07-02
Hi, thanks for the reply.  

I actually have Ubuntu 10.04, and I was trying to only disable the touchpad after a typing break.  I tried the command syndaemon -i 2 , and it said "unable to locate a synaptic device."  Isn't the mouse pad the synaptic device?

Chapra

---

### Post by chapra on 2012-07-11
Well, I did find a solution.  It's not very scientific, but it works.  I had wanted to only disable the touchpad while typing, but I never use it anyway, so I just took a thick piece of cardboard and taped it over the touchpad! Problem solved!

Chapra

---

### Post by GreatDanton on 2012-07-11
> Well, I did find a solution. It's not very scientific, but it works. I had wanted to only disable the touchpad while typing, but I never use it anyway, so I just took a thick piece of cardboard and taped it over the touchpad! Problem solved!

LOL.

 +1 sudodus. That's the solution for disabling touchpad. I have the same installed on my laptop.

---

