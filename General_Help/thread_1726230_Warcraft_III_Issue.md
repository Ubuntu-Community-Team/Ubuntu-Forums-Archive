---
title: "Warcraft III Issue"
date: 2011-04-10
forum: General Help
---

### Post by UnknownDiety on 2011-04-10
I provided a picture below. (Keep in mind this happened after a fresh install of wc3.)

Also I'm running Ubuntu 10.10
I have the non-beta wine.
[img]http://i56.tinypic.com/1tpqq0.png[/img]

---

### Post by fdm on 2011-04-10
I'm unsure what your setup is like but I have never had too much trouble with Warcraft w/ online play on any of my Linux boxes.

First thing to try:
Make sure you are launching it with the "-opengl" switch.

If you already did that:
Update to the latest wine via ppa:ubuntu-wine/ppa.
Update your graphics drivers via the appropriate ppa/repo/installer(ex. ppa:glasen/intel-driver for Intel chipsets).

These could fix your issue too:
Rename the movies folder(crashed in the past, don't think it is needed anymore)
Update the game to a recent version to remove the cd protection.

If none of that works, some info on hardware/software configurations you have tried would be helpful.

---

### Post by UnknownDiety on 2011-04-10
> **fdm said:**
> I'm unsure what your setup is like but I have never had too much trouble with Warcraft w/ online play on any of my Linux boxes.

First thing to try:
Make sure you are launching it with the "-opengl" switch.

If you already did that:
Update to the latest wine via ppa:ubuntu-wine/ppa.
Update your graphics drivers via the appropriate ppa/repo/installer(ex. ppa:glasen/intel-driver for Intel chipsets).

These could fix your issue too:
Rename the movies folder(crashed in the past, don't think it is needed anymore)
Update the game to a recent version to remove the cd protection.

If none of that works, some info on hardware/software configurations you have tried would be helpful.

Usually WC3 works on Ubuntu without -opengl (Recently reformatted which is why I had to install wc3 again lol)

I tried the -opengl after reading your post, but to no avail it still isn't working.

I've tried playing windowed mode aswell.

I used the downloaded version of wc3 from blizzard.com/account

I am using the latest NVIDIA drivers (NVIDIA GeForce Go 7400 Gfx Card) downloaded from their site.

Also tried the 3 different ones in the System > Administration > Additional Drivers (Yes I restarted after installing each one)

---

