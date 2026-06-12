---
title: "Video Drivers?"
date: 2010-11-20
forum: General Help
---

### Post by v8skittles on 2010-11-20
I'm having a problem with my laptop. Whenever I try to open a fullscreen program my screen becomes distorted and artifacts. I am on a Dell Latitude C640 Laptop with a P4 2.0GHZ, Radeon 7500m 32mb, and 1gb of Ram. I looked around and apparently drivers are already included for my card in Ubuntu 10.10, which I am using. What could be the problem?

---

### Post by sikander3786 on 2010-11-20
> I looked around and apparently drivers are already included for my card in Ubuntu 10.10, which I am using.

Proprietary drivers are not included by default in Ubuntu. You'll need to activate the Recommended/Current ones from System > Administraion > Additional Drivers if not already done that.

---

### Post by v8skittles on 2010-11-20
I tried that, and there were not any drivers available. Do you know where I can find some open source drivers or something?

---

### Post by sikander3786 on 2010-11-21
Proprietary drivers for Radeon 7500M are not available in Maverick.

You can install the open source drivers as described here.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by v8skittles on 2010-11-27
Ok I followed those steps, but whenever I open a program and it goes to fullscreen mode the screen distorts. If I run it in windowed then it exits immediately after it starts. (Was unable to get to computer for a few days)

---

### Post by sikander3786 on 2010-11-27
> **v8skittles said:**
> Ok I followed those steps, but whenever I open a program and it goes to fullscreen mode the screen distorts. If I run it in windowed then it exits immediately after it starts. (Was unable to get to computer for a few days)
Try reconfiguring your graphics by

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

And hope it improves.

Or some "ATI mate" would have to jump in.

---

### Post by v8skittles on 2010-11-27
Nothing changed. Thanks for all the help, do you think I would have better chances switching back to 10.04?

---

### Post by sikander3786 on 2010-11-28
> **v8skittles said:**
> Nothing changed. Thanks for all the help, do you think I would have better chances switching back to 10.04?
I am not sure if it would improve with 10.04 or not. Opensource mesa drivers should have worked with 10.10 equally well :-k.

This recent thread might give you some pointer's though. Keep an eye, there are some ATI guys involved there.

[http://ubuntuforums.org/showthread.php?t=1632094](http://ubuntuforums.org/showthread.php?t=1632094)

---

