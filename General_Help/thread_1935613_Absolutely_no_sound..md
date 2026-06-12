---
title: "Absolutely no sound."
date: 2012-03-04
forum: General Help
---

### Post by Ladders on 2012-03-04
So today my laptop suddenly stopped playing any and all sound. I've tried the mixers and I've been through the audio debugging guide on the wiki and nothing has worked.

Please help?

---

### Post by Gremlinzzz on 2012-03-04
Try live cd and see if you get sound,

---

### Post by BBQdave on 2012-03-04
> **Ladders said:**
> Please help?

So depending on the type of notebook, some have a manual volume dial that can get set to **0**.
This effectively mutes the hardware.

---

### Post by Ladders on 2012-03-05
I get sound when booting to the live CD.

And, other than the Fn keys which I have already tried, there is no manual control for volume that I can see.

---

### Post by Ladders on 2012-03-06
Having done some more research, I attempted to install the latest alsa driver snapshot as outlined here:

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

Everything appeared to go as it should, but after entering:

```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```I got this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-alsa-driver-modules-3.0.0-16-generic-pae
E: Couldn't find any package by regex 'linux-alsa-driver-modules-3.0.0-16-generic-pae'
```
I hope this information is helpful because I have no idea what to do.

---

