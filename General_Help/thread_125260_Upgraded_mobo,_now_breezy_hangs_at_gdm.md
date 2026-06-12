---
title: "Upgraded mobo, now breezy hangs at gdm"
date: 2006-02-03
forum: General Help
---

### Post by shawndoggy on 2006-02-03
So I put breezy on the old P3 machine in my garage, and after getting through the wireless networking woes with ndiswrapper, it ran just great.  So great, that I decided to upgrade the mobo and processor (MSI mobo, Celeron D) to get a little more juice.

Now, ubuntu tries to boot, but hangs at the gdm screen.

I tried recovery mode, and I get this message:

```
[4297962.41500] r8169: eth0: PHY reset until link up
```

Thoughts?

---

### Post by dcstar on 2006-02-03
[QUOTE=shawndoggy]So I put breezy on the old P3 machine in my garage, and after getting through the wireless networking woes with ndiswrapper, it ran just great.  So great, that I decided to upgrade the mobo and processor (MSI mobo, Celeron D) to get a little more juice.

Now, ubuntu tries to boot, but hangs at the gdm screen.

I tried recovery mode, and I get this message:

```
[4297962.41500] r8169: eth0: PHY reset until link up
```

Thoughts?[/QUOTE]
Reinstall Ubuntu so it has a chance to find (and work with) the new hardware.

Don't reformat, so hopefully all of your data (and configuration) will be preserved.

---

### Post by shawndoggy on 2006-02-24
David,

Belated reply... so that's what I did (reinstalled), but now when GRUB comes up I have two different ubuntu installs to chose from (the bad, nonworking one and the new, albeit with no programs or data, working one).

How do I get all of the stuff that was in the old install into my new install?

---

### Post by slux on 2006-02-24
Probably the easiest is to just copy the new xorg.conf to the old install. Would've been possible to reconfigure X in the old install without reinstalling and that's what I suspect your only problem was.

---

