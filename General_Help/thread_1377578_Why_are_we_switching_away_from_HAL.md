---
title: "Why are we switching away from HAL?"
date: 2010-01-10
forum: General Help
---

### Post by MES5464 on 2010-01-10
To clearify my question, why are we leaving HAL? It is only now (Ubuntu Karmic) working right with my Lenovo X61 Tablet, and now we a switching to something else? What are we switching to? Will it support the Wacom tablet?

---

### Post by gsmanners on 2010-01-10
It looks like the decision came from upstream. See:

[http://lists.freedesktop.org/archives/hal/2009-June/013429.html](http://lists.freedesktop.org/archives/hal/2009-June/013429.html)

---

### Post by Favux on 2010-01-10
Hi MES5464,

HAL was a temporary solution to get us usb hot plugging.  Basically it duplicated a lot of udev stuff.  It became messy and DeviceKit replaced it.  Since the urgent problems were solved they've been making a "slow" transition.  HAL in Intrepid and Jaunty.  DeviceKit in Karmic.  Right now they're moving HAL/DeviceKit to udev-extras.  So I think Lucid will be udev with the extra configuration stuff in udev-extras.
> Will it support the Wacom tablet? 
Good question.  I'm sure it's suppose to.  We'll see.  Right now the big thing is getting the linuxwacom driver to support Xserver 1.7.

---

