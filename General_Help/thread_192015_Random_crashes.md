---
title: "Random crashes"
date: 2006-06-08
forum: General Help
---

### Post by burzum on 2006-06-08
My Ubuntu crashes randomly after just 5mins of working with it up to 1 1/2 hours of working before it crashes. I can't do anything then, it's completly frozen. I can't remote login via SSH from another pc, i can't get back out of X, i can't move the mouse - nothing. Only reset :(

I think this is an Ubuntu problem because gentoo works good without crashing.

Im using an Asus A8N32-SLI Deluxe and a Asus Geforce 7800 GT Extreme, no pci or any other cards are running in this system. Are there known problems with this hardware components? If not any idea where to look for an errormsg?

Note: I've set "RenderAccel" already to "false" in my Xorg.conf!
This should help according to another posting but it did not.

Thank you!

---

### Post by thingy on 2006-06-08
You'll have to narrow down the problem. Specifically a way to replicate it.

1) Rule out X first. To do this, either switch to a non X runlevel or /etc/init.d/gdm stop to kill X. Then wait for the 2 hours or so, to find out if the system still froze.

2) Rule out sound card/network card next to find out if the problem is happening when these two are in use.

The standard response to freezes is usually hardware problems, like memory/graphics card. This could simply be heat/Power supply issue in the case of g'cards.

jin

---

### Post by burzum on 2006-06-08
[QUOTE=thingy]
The standard response to freezes is usually hardware problems, like memory/graphics card. This could simply be heat/Power supply issue in the case of g'cards.
jin[/QUOTE]

Ok, i'll try it over the night because i have to do work atm.

I've checked the memory already and it's also no heat or power supply problem. Checked it and as i said, gentoo works fine and XP also, even while doing stress-tests.

---

