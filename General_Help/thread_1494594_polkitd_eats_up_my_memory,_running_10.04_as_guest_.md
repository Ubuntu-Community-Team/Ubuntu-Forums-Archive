---
title: "polkitd eats up my memory, running 10.04 as guest in VMWare fusion"
date: 2010-05-27
forum: General Help
---

### Post by hasinee on 2010-05-27
Hi,

i am running Ubuntu 10.04 as a guest in VMWare Fusion running on a Unibody MacBook
Pro. So far everything had been fine. Yesterday i have updated VMWare Fusion from
3.0.2 to 3.1. After that update (more precisely: after installing the VMWare Tools in
the guest) my Ubuntu guest went crazy: the polkitd demon generates a load of 100%
and eats up all my memory. Killing this thing is neither recommendable (it is used by
DBus) nor possible (it is always respawned). I have checked these forums and the
only practical tip i found was to delete .dbus/ and .pulse/. Of course i did that and
nothing happened.

Am i the only one with this problem? And: WHAT CAN I DO?

Cheers,

Hasinee

---

### Post by crazy ivan on 2010-07-15
Same problem here:
1) At first I could not control sound volume via panel
2) Later there was no sound whatsoever
3) I come back in the morning and 3 GB RAm + 1GB swap are cluttered up by polkitd
4) 
```

sudo killall polkitd

``` 

and the tricks from 

[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

got me to free swap again but still no sound.. I'll get back to you if restart doesn't fix it.

---

### Post by basich on 2011-02-03
something renamed /etc/pulse/default.pa to /etc/pulse/default.pa.old.0

renamed this back and rebooted and all works

---

