---
title: "when my laptop is booting..."
date: 2010-03-31
forum: General Help
---

### Post by jedlacks on 2010-03-31
I get a message that says : Udevd-work {336} open /del/null/ failed file not found

As far as I can see the laptop works great from that point onwards with no issues

Any thoughts what that could be?

---

### Post by iskarion on 2010-05-02
Same problem here. Fresh install of the final Kubuntu 10.04 version on an Intel board with G33 chipset. The number after udevd-work varies on each reboot. Though always something in the 3xx range.
It's a Kubuntu install just with default options. No encrypted home partition or other exotic stuff.
The only obvious side effect of this error message is, that on most boots it's visible for so long that the nice Plymoth boot screen doesn't show up, but KDM appears right away. So it's not a big issue, just an annoyance.

Any idea where this error message might come from and how I can get rid of it?

Google came up with some launchpad bugreports also referring to the udevd-work ... /dev/null ... message. Though these serm to be unrelated to my problem. They are already marked as fixed and/or show different symptoms (e.g. computer not booting at all...).

Oh, well I just discovered that Plymouth not showing up is not the only side effect of this error message. Now and then (not very often) the whole computer is locking up with a kernel panic message while booting.

---

