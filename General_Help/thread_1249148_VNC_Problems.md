---
title: "VNC Problems"
date: 2009-08-25
forum: General Help
---

### Post by bordot on 2009-08-25
Hello, I am currently running a VNC server on my ubuntu computer and I have tried UltraVNC and TinyVNC on my Windows Vista installation to connect to the Ubuntu VNC server. I'm able to connect to the server, but when I try to open any windows or the Ubuntu menu from the VNC client, it shows up on the ubuntu computer, but not the VNC clients.

I hope that makes sense... any ideas how to fix this?

---

### Post by XCan on 2009-08-25
It is a known bug in Jaunty. The less suckiest workaround is to disable visual effects, there are also patches out for vino that disable xdamage, as well as a patch in X that's supposed to fix the issue altogether. See more details here [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126) .

---

### Post by bullka on 2009-11-10
> **XCan said:**
> It is a known bug in Jaunty. The less suckiest workaround is to disable visual effects, there are also patches out for vino that disable xdamage, as well as a patch in X that's supposed to fix the issue altogether. See more details here [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126) .

Hi,

Has this been solved or not?
Seems that in Ubuntu Desktop 9.10 the problem still persists: you need to disable Visual Effects (appearance preferences  -> visual effects -> none) to get your screen refreshed in vncviewer.

Is there a fix available?

My GPuy if it makes sense: ATI HD4850 with Ubuntu suggested ATI drivers.

---

### Post by bullka on 2009-11-10
Well..
I see that it's still in the known problem list ([http://ubuntuforums.org/showthread.php?t=1145967](http://ubuntuforums.org/showthread.php?t=1145967)) with the same workaround (disable effects).

Too bad :(

---

### Post by XCan on 2009-11-10
Not really solved. The best thing we all can do is probably to click on the "This bug affects me too" button on the bugs.launchpad page(s).

---

### Post by bullka on 2009-11-10
> **XCan said:**
> Not really solved. The best thing we all can do is probably to click on the "This bug affects me too" button on the bugs.launchpad page(s).

Just did that and subscribed to this bug.
Thanks!

---

