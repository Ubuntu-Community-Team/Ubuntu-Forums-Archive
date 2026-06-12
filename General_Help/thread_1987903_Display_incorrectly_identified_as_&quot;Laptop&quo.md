---
title: "Display incorrectly identified as &quot;Laptop&quot;"
date: 2012-05-26
forum: General Help
---

### Post by CoreyB. on 2012-05-26
Ubuntu 12.04 identifies the monitor on my desktop pc as "Laptop", which is incorrect.  It also doesn't shut off the monitor like it is supposed to, it just fades to black but the monitor stays on.

I am not sure what changed to make this occur, but I think it started fairly recently.  I think it used to work correctly in 12.04.  Is there any way to "reset" how Ubuntu identifes displays?

I am on a Dell Dimension 2400 with a Nvidia GeForce 8400GS PCI graphics card using the proprietary graphics card with an Asus 19" VE198T monitor connected through DVI.

Thanks!

---

### Post by CoreyB. on 2012-05-26
I suspect it has something to do with installing the gnome-fallback session and running it.  I uninstalled it but that didn't fix anything.  My monitor used to be called "Ancor Communications" or something like that.

---

### Post by kurja on 2012-05-26
My display is falsely identified as "laptop" as well.

---

### Post by CoreyB. on 2012-05-26
I unistalled the proprietary Nvidia drivers and then checked and it was labelled correctly under the open-source drivers, reinstalled the proprietary drivers and it went back to "laptop".

Is there some way to completely uninstall the proprietary drivers and all of its configs and settings to make sure it isn't using something from before?

---

### Post by PhantomTurtle on 2012-05-26
I believe it has something to do with DVI, mine is listed as laptop as well. When I use VGA it knows the name of my monitor. After it fades to black after a couple of seconds to a minute it will turn off. On mine it turns off after a few seconds. It will eventually turn off.

---

### Post by CoreyB. on 2012-05-26
> **PhantomTurtle said:**
> I believe it has something to do with DVI, mine is listed as laptop as well. When I use VGA it knows the name of my monitor. After it fades to black after a couple of seconds to a minute it will turn off. On mine it turns off after a few seconds. It will eventually turn off.

Yup, too antsy I guess.  It turned off after 30 seconds-ish. Thanks!

---

