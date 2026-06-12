---
title: "Ubuntu on Compaq x1000 laptop: brightness keys not working"
date: 2006-04-21
forum: General Help
---

### Post by biosphere on 2006-04-21
I am a newb to Ubuntu and I just got it installed on my laptop.  ACPI power management is working ok but my function keys to change the brightness do not work.  When my laptop is plugged in (on AC power) my brigthness is full.  When im on battery power it switches to minimum brightness.

So I can see that ubuntu is capable of changing my brightness.  My question is where/how can I set the brightness manually, or fix my function keys?  I've searched the forums and google a bit and nothing so far has helped me.

I would settle for just a console command or somesuch to set the brightness level, getting the keys to work isnt that important to me.

---

### Post by biosphere on 2006-04-23
bump

---

### Post by riverfr0zen on 2006-08-08
bumpy bumpy

---

### Post by naitram on 2006-12-15
i know this is a bit dated, but figured an answered post is always better than a non-answered post.

my laptop controls this through /proc/acpi/video/GFX0/LCD/brightness

if you: cat /proc/acpi/video/GFX0/LCD/brightness

you should get a response telling you available options as well as current.

if you: "echo  0 > /proc/acpi/video/GFX0/LCD/brightness"  your backlight should go off

and: "echo 8 > /proc/acpi/video/GFX0/LCD/brightness"  puts my backlight to high.

hope it helps someone

---

