---
title: "Stretch Out App-Start at Boot"
date: 2010-07-30
forum: General Help
---

### Post by pSYcl0Ne on 2010-07-30
I'm curious to know if there is any way to perhaps set start up applications to begin after a set time. The purpose is to speed up my boot time - from login to actually system use, but I don't want to turn off anything I have starting currently. 

To give a better example, I want things that perhaps aren't as important to begin say 10 or 20 seconds after others... like a delay prefix so that things like gnome-do starts asap, but AWN a little later, as I won't need that right away. Is there some way to edit the start-up applications in this way? Some sort of cli scripting?

I hope this question makes sense, appreciate any help.

I'm using Gnome and 10.04

---

### Post by viralmeme on 2010-07-30
> **pSYcl0Ne said:**
> I'm curious to know if there is any way to perhaps set start up applications to begin after a set time. The purpose is to speed up my boot time

[Make Ubuntu Faster]("http://www.techmetica.com/howto/make-ubuntu-boot-faster-by-running-boot-time-scripts-in-parallel/")

[Use Prelink to make applications start faster]("http://ubuntuforums.org/showthread.php?t=189192")

---

### Post by pSYcl0Ne on 2010-07-30
Thanks for that, reading them all now.. but it's not exactly what I meant.

I'm using an MSI Wind which has aa Atom CPU - only 1.6 Ghz - and the links you gave me are for dual core and the like. 

What I actually want to do is slow down the boot process in a way so I could say; start browsing internet right away, while other things are booting one by one in the background. 

I find that compiz and emerald and other services are slowing the thing down and whilst I want them running asap I find I am waiting too long before I can do anything.

Is there possibly a prefix to a command that will cause a pause before execution ie.

$glx-dock --purge-10-seconds

or some such?

---

### Post by pSYcl0Ne on 2011-06-03
Nearly a year later and I learn about bash scripts for my startup applications

Eg.

#!/bin/bash
#start Conky with a 20 second delay
sleep 20
conky -c ~/Conky/.conkyrc
#conky -c ~/Conky/conky-countdown
conky -c ~/Conky/conky-email
sleep 1
avant-window-navigator
exit

---

