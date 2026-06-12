---
title: "can't shut down"
date: 2010-03-02
forum: General Help
---

### Post by tombaugh on 2010-03-02
Hi,

I just did a fresh install, and installed the NVIDIA drivers and some software. At first I had some problems with the graphics drivers failing to load and USB mouse and keyboard not working, but that seems to be resolved now. There is still another problem however: the shutdown button is grayed out, and there is no shutdown option in the menu. 

Any thoughts?
Thanks

---

### Post by zeroseven0183 on 2010-03-02
>  the shutdown button is grayed out, and there is no shutdown option in  the menu.Odd. Hmmm gotta think about it first.

But if you need an alternative, open Terminal and type 
```
sudo shutdown now
```or
```
sudo reboot now
```

---

### Post by tombaugh on 2010-03-02
I know, but I'm looking for a permanent solution, and it would also be nice to know why this happened...

---

### Post by tombaugh on 2010-03-02
Some extra information: strangely enough, the same problem now also affects my other Ubuntu system which is on a completely different drive. 

Other problems since the fresh install: the motherboard splash screen stays on for quite a while, the network/ubuntu one/etc icons come up rather slowly after booting, and USB mouse and keyboard don't work right away but only after everything has loaded on the desktop...

---

### Post by tuxlord on 2010-03-02
I have some of the same issues with ATI Drivers... its seems its just a compatibility issue, and that there is no resolve. You may want to just remove that driver.


Tuxlord

---

### Post by tombaugh on 2010-03-02
I just managed to locate the problem: when I shut my printer down during boot everything works well, it boots really fast and I can shut down.

Before I tag this as "solved", does anyone know what is going on here?

---

### Post by dino99 on 2010-03-02
> **tombaugh said:**
> I just managed to locate the problem: when I shut my printer down during boot everything works well, it boots really fast and I can shut down.

Before I tag this as "solved", does anyone know what is going on here?

many people have this problem and bugs have been reported too on launchpad, so devs still at work, wait and hope

---

