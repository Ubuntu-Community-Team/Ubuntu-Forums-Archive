---
title: "Xorg.conf for my machine"
date: 2009-10-30
forum: General Help
---

### Post by Living2007 on 2009-10-30
I'm looking to modify my Xorg.conf file because I think it is causing the Ubuntu boot splash screen to stretch out to 1280x1024, and for a 1680x1050 monitor, it doesn't look pretty.

I prefer the splash screen on 1024x768 but I don't know how to add to my systems properties to the file properly. Here is a quick run through:

Monitor: 20" Dell LCD Monitor 2009Wt?
Display: nVidia GeForce4 MX 4000

---

### Post by kaibob on 2009-10-30
You used to be able to change the resolution of the splash screen by modifying /etc/usplash.conf. I don't know if this works with 9.10.

---

### Post by Living2007 on 2009-10-30
i'm using 8.04

---

### Post by kaibob on 2009-10-30
> **Living2007 said:**
> i'm using 8.04

Sorry--I missed that in your original post. I don't know if the usplash.conf file is used in 8.04.

---

### Post by Living2007 on 2009-10-30
> **kaibob said:**
> I don't know if the usplash.conf file is used in 8.04.
Thanks, this is the solution. Usplash.conf does exist in 8.04!

---

