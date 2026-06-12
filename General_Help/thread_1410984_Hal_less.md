---
title: "Hal less"
date: 2010-02-19
forum: General Help
---

### Post by ETbluez on 2010-02-19
Lucid Alpha 2 sports full removal of the hal package, making Ubuntu faster to boot and faster to resume from suspend. If it.s obsolete then what will replace it? can it safely be removed from karmic?One of those questions that might make me mess up my system.

---

### Post by Tibuda on 2010-02-19
> If it.s obsolete then what will replace it?
DeviceKit I guess.

> can it safely be removed from karmic?
I'm not sure, but I guess it may harm your system.

---

### Post by Psumi on 2010-02-19
From what I hear, HAL is not being replaced, and that the kernel will be handling what HAL did.

Some programs have been rewritten a bit (IE: xfburn) because hal isn't implemented fully in karmic.

---

### Post by ETbluez on 2010-02-19
> **danielrmt said:**
> DeviceKit I guess.


I'm not sure, but I guess it may harm your system.
that was my guess too just wanted second opinion.
Thanks

---

### Post by ETbluez on 2010-02-19
> **Psumi said:**
> From what I hear, HAL is not being replaced, and that the kernel will be handling what HAL did.

Some programs have been rewritten a bit (IE: xfburn) because hal isn't implemented fully in karmic.
Really i installed lucids kernel wonder if i should give a try and purge hal?
yeah its a young system nothing worth backing up im going to try it.
ill report back of any ill effects. if i can find my post address. i been moved some where! lol brb maybe.

---

### Post by Psumi on 2010-02-19
> **ETbluez said:**
> Really i installed lucids kernel wonder if i should give a try and purge hal?

Please don't. If you want to try lucid, get lucid; don't make a frankenstein.

---

### Post by ETbluez on 2010-02-19
well so far so good have to fix some broken packages but everything seems the same.
but now i dont trust my system lol. have to check all programs.

---

### Post by ETbluez on 2010-02-19
> **ETbluez said:**
> well so far so good have to fix some broken packages but everything seems the same.
but now i don't trust my system lol. have to check all programs.
  well frankies working with no problems must be my updated kernel.
but i don't see much of a improvement not even in the boot.
guess ill have to wait for lucid. thanks for your concern but like i said its a young system which i can reinstall easily .

---

### Post by falconindy on 2010-02-19
HAL's functionality is being replaced by libudev, udisks, and upower (the latter 2 of which are currently called devicekit-{disks,power}). In order to run X without HAL, you currently need to:
- Configure your input devices manually via xorg.conf
- Use a patched Xserver which uses libudev for input hot plugging

I've been running with a [patched Xserver]("http://aur.archlinux.org/packages.php?ID=32428") for about 3 months now. Tastes great, less filling. The upcoming release of XServer 1.8 will have the libudev patch merged in.

> **ETbluez said:**
> well frankies working with no problems must be my updated kernel.
Highly dubious. While udev exists in kernelspace, it doesn't know/care about what happens to Xorg, hence the point of libudev to act as a bridge between the two.

---

### Post by ETbluez on 2010-02-19
> **falconindy said:**
> HAL's functionality is being replaced by libudev, udisks, and upower (the latter 2 of which are currently called devicekit-{disks,power}). In order to run X without HAL, you currently need to:
- Configure your input devices manually via xorg.conf
- Use a patched Xserver which uses libudev for input hot plugging

I've been running with a [patched Xserver]("http://aur.archlinux.org/packages.php?ID=32428") for about 3 months now. Tastes great, less filling. The upcoming release of XServer 1.8 will have the libudev patch merged in.

Thanks for the info.

---

