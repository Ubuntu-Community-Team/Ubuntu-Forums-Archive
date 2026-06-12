---
title: "this is pretty cool"
date: 2010-09-21
forum: General Help
---

### Post by ihatetryingtopickaloginna on 2010-09-21
I bought a Logitech wireless keyboard and a mouse. Both will work in Win7 but wouldn't work with Ubuntu 8.04. So I tried plugging the small usb adapters into a kvm switch that I was using with both computers and they work under Linux now. I'm not going to argue with success, but it does seem strange that they will work this way. I just tried it to see, not expecting it to.

Oh yeah, windows had to load the drivers but Ubuntu never did. It just worked without a hitch this way.

---

### Post by bodhi.zazen on 2010-09-21
A more recent version of Ubuntu, with a newer kernel, may have the drivers you need.

---

### Post by BobVila on 2010-09-21
> **ihatetryingtopickaloginna said:**
> I bought a Logitech wireless keyboard and a mouse. Both will work in Win7 but wouldn't work with Ubuntu 8.04. So I tried plugging the small usb adapters into a kvm switch that I was using with both computers and they work under Linux now. I'm not going to argue with success, but it does seem strange that they will work this way. I just tried it to see, not expecting it to.

Oh yeah, windows had to load the drivers but Ubuntu never did. It just worked without a hitch this way.

If your logitech devices are at all like mine, they present (or at least they did...) as USB devices to ubuntu. I'm guessing that's why they're working for you through a kvm.

---

### Post by ihatetryingtopickaloginna on 2010-09-21
> **BobVila said:**
> If your logitech devices are at all like mine, they present (or at least they did...) as USB devices to ubuntu. I'm guessing that's why they're working for you through a kvm.

Tiny things that plug into USB slots. Ubuntu didn't even see them until I plugged both into the kvm. Strange to me.

---

### Post by BobVila on 2010-09-22
> **ihatetryingtopickaloginna said:**
> Tiny things that plug into USB slots. Ubuntu didn't even see them until I plugged both into the kvm. Strange to me.

That's odd. Could be that your devices were showing up as bluetooth devices when plugged directly into the machine, but are now showing up as usb hids now that the kvm is between them and the box.

---

