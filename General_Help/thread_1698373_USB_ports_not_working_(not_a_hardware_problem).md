---
title: "USB ports not working (not a hardware problem)"
date: 2011-03-02
forum: General Help
---

### Post by auh2o on 2011-03-02
The two integrated USB ports on a laptop of mine running Ubuntu 10.10 mysteriously stopped working a while back after some random updates. They still have power, and they are still recognized by the system, as per lsusb:

```
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

But although the ports still power up any connected appliances, they won't actually function. Any mouse I've tried so far won't work, nor will any external USB drive mount when connected.

I don't even know where to begin to look. I believe the problem arose after an update to the xorg server, but I'm not sure. I just updated the kernel to 2.6.35-27, but that didn't solve the problem. Any suggestions welcome.

---

### Post by blueridgedog on 2011-03-02
Have you looked at lsusb when the devices were plugged in?

---

### Post by auh2o on 2011-03-03
Yes. No matter what I plug in, the message above is invariably given.

---

### Post by blueridgedog on 2011-03-03
If you boot on a LiveCD, is the issue the same?  How about if you use one of the older kernel options at boot time?

---

### Post by auh2o on 2011-03-03
I have tried every kernel from 2.6.35-23 onward with no luck. Haven't tried a Live CD, I'll get back to you on that!

---

### Post by auh2o on 2011-03-09
No mouse will work in either of the ports with the Live CD either... I'm assuming things just went from bad to worse, since this would vastly increase the risk that it's an internal hardware problem?

---

### Post by blueridgedog on 2011-03-09
That is the indication at this point, especially since it no longer works with kernel versions that you know once worked.  Perhaps another forum member can suggest additional troubleshooting steps.

---

