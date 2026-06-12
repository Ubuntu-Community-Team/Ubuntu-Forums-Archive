---
title: "Trouble locking package for patched kernel"
date: 2011-09-15
forum: General Help
---

### Post by josejuan05 on 2011-09-15
I'm currently using a patched version of the 2.6.38-11 kernel under natty in order to deal with [a bug in vgaswitcheroo]("https://bugs.launchpad.net/bugs/727620"). While the patched version works, every time I do a software update (apt-get update && apt-get upgrade) I am asked to re-install the channel version of the kernel packages, since they are apparently a higher version than the patched version.

I have tried locking the version of these packages in synaptic, but this doesn't appear to stop apt from attempting to upgrade them anyways.

So far my workaround is to do a normal upgrade and then to reinstall the patched kernel packages.

Is there a proper way to do this?
If it helps, my patched kernel version is 2.6.38-11.48~lp727620v201108261554, while the channel version is 2.6.38-11.48

---

### Post by drs305 on 2011-09-15
For whatever reason, locking the version in Synaptic doesn't lock it using apt-get, and vice versa. I assume it applies to your kernel as well.

I've never understood why it continues to operate this way, or if I just misunderstand, but from my testing, you have to do both (lock in Synaptic, hold in APT for command line ops).

Check out this community document:
[https://help.ubuntu.com/community/PinningHowto]("https://help.ubuntu.com/community/PinningHowto")
It has the commands.

---

### Post by dcstar on 2011-09-17
> **drs305 said:**
> For whatever reason, locking the version in Synaptic doesn't lock it using apt-get, and vice versa. I assume it applies to your kernel as well.
.........

This is an ancient bug with many (many) reports in Launchpad, basically Synaptic uses a different database for Pinning that APT doesn't use and the respective developers don't seem to want to do anything about it.

---

