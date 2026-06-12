---
title: "Gnome-Do is crazy at startup"
date: 2009-11-15
forum: General Help
---

### Post by nostra16 on 2009-11-15
Hi,

I've updated to 9.10 last week, and have one simple problem : Gnome-Do goes CRAZY on startup!

[IMG]http://s2.directupload.net/images/091114/ywbe3y39.jpg[/IMG]

The only way of stopping this is to patiently access system monitor (10sec to open menu, 10 more to get to system monitor, and a good 20 to open Sys Monitor...).

This does not always happen, and happens randomly (tried to find a pattern or something, but none appears...).

How can I stop him doing this? I imagined turning off the "load on startup" and the "hide first launch", but that's like loosing a useful plugin/tweak!

Thanks, 
nostra16

---

### Post by frankob on 2009-11-16
Same problem here. Although, I found out on my computer it acts like this only on first start of the Gnome session, i.e. when I turn on, or reboot my computer. When I restart X, or logout/login, it doesn't. So it turns out that the faster fay to stop this is to kill the X session (ctrl-alt-backspace, if you have this option enabled), or logout (which is a bit slower way, 10'' to open menu...) and then login again.

I tried to solve this by updating Gnome-Do, but it turned out that the version in the official Karmic repos was already the newest one. I added the Gnome Do ppa repo anyway, just in case...

Anyway, still no solution found... :-/ Any help would be useful.

---

### Post by Bunnybugs on 2009-11-16
Well, Gnome-Do made my Gnome-Panels grey-out... so, it's removed...

---

### Post by arnab_das on 2009-11-16
use cairo dock. and use the classic panel of gnome do.

sudo apt-get install cairo-dock

---

### Post by Bunnybugs on 2009-11-16
> **arnab_das said:**
> use cairo dock. and use the classic panel of gnome do.

sudo apt-get install cairo-dock


Cairo-dock is not the best dock available;)

I have Avant Window Manager, that's by far the best available;)

I'm not sure about the terminal command, but it's sure available from the net

---

### Post by fabounet on 2009-11-16
> that's by far the best available
--> which I find to be the best available (but you probably didn't test Cairo-Dock since a while ;-)  )

---

### Post by arnab_das on 2009-11-16
> **Bunnybugs said:**
> Cairo-dock is not the best dock available;)

I have Avant Window Manager, that's by far the best available;)

I'm not sure about the terminal command, but it's sure available from the net

i know avant is the best available but one who is using gnome do docky is more likely looking something like cairo dock than awn.

---

### Post by Bunnybugs on 2009-11-16
> **arnab_das said:**
> i know avant is the best available but one who is using gnome do docky is more likely looking something like cairo dock than awn.


Huh?:s

Gnome Do doesn't even look a bit like Cairo Dock, AWN and all the docks available:s

So, AWN is the simplest to configure etc, etc!

---

### Post by Bunnybugs on 2009-11-16
> **fabounet said:**
> --> which I find to be the best available (but you probably didn't test Cairo-Dock since a while ;-)  )

Just removed cairo-dock last night;)

Had AWN already installed on another system;)

Cairo is filled with bugs, like greying out your panels etc, etc

---

### Post by nerdy_kid on 2009-11-16
maybe turn off DO's plugins?? does it still do it then?

---

### Post by arnab_das on 2009-11-16
> **Bunnybugs said:**
> Huh?:s

Gnome Do doesn't even look a bit like Cairo Dock, AWN and all the docks available:s

So, AWN is the simplest to configure etc, etc!


it does. the zoom effect etc.

anyway the real similarity is that both are extremely light weight. unlike Avant, which consumes a lot more memory than these.

---

### Post by Bunnybugs on 2009-11-16
Well. have memory in overload:P

I use 700MB of my 2GB... that's when all the usual programs are at their jobsides:P

---

