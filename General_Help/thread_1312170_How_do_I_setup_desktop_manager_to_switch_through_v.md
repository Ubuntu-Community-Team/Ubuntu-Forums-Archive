---
title: "How do I setup desktop manager to switch through virtual desktops via mouse scroll?"
date: 2009-11-02
forum: General Help
---

### Post by rkham11 on 2009-11-02
After upgrading from Jaunty to Karmic, I noticed that I cannot go between virtual desktops using the mouse scroll wheel any more. This is pretty frustrating considering how frequently I use this feature. Does anyone know how to configure the default desktop manager to respond to mouse scroll?

---

### Post by Pan_Synaptic on 2009-11-06
I've noticed the same thing happen, rather annoying and haven't found a way to reverse it yet (not very clued up on ubuntu, i just google stuff lol)

If anyone knows how to enable it again i'd be very grateful :D

---

### Post by tyven on 2009-11-08
You can configure it in CompizConfig-->Desktop Wall-->Bindings.
Button 4 - Down Scroll
Button 5 - Up Scroll

---

### Post by travelling.steve on 2009-11-13
> You can configure it in CompizConfig-->Desktop Wall-->Bindings.
Button 4 - Down Scroll
Button 5 - Up Scroll 	

This will make the viewport change with the scroll wheel no matter where your mouse pointer is on the screen - that behaviour doesn't work for me at all.

To restore the behaviour that you probably had in Jaunty, try using
CompizConfig Settings Manager -> Viewport Switcher -> Desktop-based Viewport Switching
Set "Move Next" to Button 4
Set "Move Prev" to Button 5

---

### Post by Philip Farrugia on 2009-11-13
Thanks to traveling.steve. Your tip worked for me. I'd be looking for the solution for a few weeks!

---

### Post by Pan_Synaptic on 2009-11-15
Thanks steve, wanted to get the easy way to grab files off my desktop again for ages!

---

### Post by Porcupines on 2009-11-24
Many thanks to travelling.steve for the solution.

Just wanted to say that for me on 9.04 was 

"Move Next" to **Button 5**
"Move Prev" to **Button 4**

---

