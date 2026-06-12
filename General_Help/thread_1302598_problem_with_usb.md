---
title: "problem with usb"
date: 2009-10-27
forum: General Help
---

### Post by cobra90nj on 2009-10-27
Hi, I have a problem with usb when I insert my mouse, output of lsusb is:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```and it not work, why? how to fix this problem?
thanks.

---

### Post by Giblet5 on 2009-10-27
What kind of mouse is it? Does it have a PS/2 to USB adapter hanging off of it?

Does the mouse work anywhere else?

Is that USB port working? Does it recognize a USB memory stick?

---

### Post by cobra90nj on 2009-10-27
The model of mouse is Trust, it work on other my pc.
no, when insert my pen drive usb, it not work, ubuntu doesnt mount it, but led on pen drive is lights. not use an adapter hanging.
thanks.

---

### Post by Giblet5 on 2009-10-27
> **cobra90nj said:**
> The model of mouse is Trust, it work on other my pc.
no, when insert my pen drive usb, it not work, ubuntu doesnt mount it, but led on pen drive is lights. not use an adapter hanging.
thanks.

It sounds like that USB port still has power but the data lines are dead.

That can happen from a static electricity discharge or just a general failure on the motherboard.

Try plugging the mouse into each of the USB ports on your system and testing to see if it works.

If this is a laptop and none of the USB ports seem to work, you might have to buy another USB adapter for it (micro-xd, pcmcia, etc). The good news is that the add-on USB ports are often much faster than the builtin USB ports.

---

### Post by cobra90nj on 2009-10-27
You have an advice? my pc is a Compaq nx6110:
[http://www.xbitlabs.com/images/mobile/budget-notebook/3p8s.jpg](http://www.xbitlabs.com/images/mobile/budget-notebook/3p8s.jpg)

---

### Post by Giblet5 on 2009-10-27
> **Giblet5 said:**
> It sounds like that USB port still has power but the data lines are dead.

That can happen from a static electricity discharge or just a general failure on the motherboard.

**[COLOR="DarkRed"]Try plugging the mouse into each of the USB ports on your system and testing to see if it works.[/COLOR]**

If this is a laptop and none of the USB ports seem to work, you might have to buy another USB adapter for it (micro-xd, pcmcia, etc). The good news is that the add-on USB ports are often much faster than the builtin USB ports.

Here's a [cardbus USB adapter]("http://www.google.com/products/catalog?q=cardbus+usb+adapter&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a&um=1&ie=UTF-8&cid=13063931434563969635&ei=LRDnSqGKGcGllAe-45SDCA&sa=X&oi=product_catalog_result&ct=result&resnum=4&ved=0CCAQ8wIwAw#ps-sellers") for $16US that should work.

I'd borrow someone else's mouse and double-check first...

---

