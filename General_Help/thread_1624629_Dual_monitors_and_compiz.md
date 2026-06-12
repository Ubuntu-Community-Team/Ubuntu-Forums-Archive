---
title: "Dual monitors and compiz"
date: 2010-11-18
forum: General Help
---

### Post by w1ll1am on 2010-11-18
Hello I have dual monitors setup and if I try to enable visual effects it will not work I am not sure why if anyone does please let me know thanks.

---

### Post by amauk on 2010-11-18
Are you using the nvidia binary driver?
(see system > admin > drivers)

---

### Post by jacob.david on 2010-11-18
I have the same problem with my lenovo laptop. Basically to enable the visual effects it needs the NVIDIA driver which screws it up. If you don't enable it then with the default driver it works fine. Sorry I don't have any solution. May be someone else can help.

---

### Post by w1ll1am on 2010-11-19
> **amauk said:**
> Are you using the nvidia binary driver?
(see system > admin > drivers)

did you mean system>Admin>additional drivers ?

if so then yes i have run that and i have the nVidia driver enabled it is the recommended one.

---

### Post by afonteijn on 2010-12-13
There is nothing wrong with your nvidia drivers, it is a compiz issue. The problem is that compiz runs at a maximum resolution of 2048x2048. If you add a second monitor the screen size is calculated over both screens. So if you got two screens of 1280x1024 next to each other, you got a total resolution of 2560x1024. That is too big for compiz. However, if you stack them on top of each other you get a resolution of 1280x2048. That will work for compiz. If your screens are bigger? Bad luck!

It is not a pretty solution, but it works. I got a 1280x1024 and a 1024x786 screen stacked on top of each other (virtually) while they are actually next to each other. It's a bit weird moving your cursor up and then seeing it on the other screen... but heck, I got compiz working!

---

### Post by amauk on 2010-12-13
Compiz /does not/ have a maximum resolution

I'm running compiz horizontally across a 1600x1200 & 1280x1024 monitor...

There are issues with older graphics cards, however.
See this bug
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/555641](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/555641)> Compiz displays the desktop as a 3D texture. The maximum texture size is determined by the hardware capabilities of the particular graphics card. Some older or lower end cards have a limitation of 2048x2048

This is a hardware issue
(graphics card not having enough VRAM)

---

### Post by afonteijn on 2010-12-13
You're right. I must have been misinformed. This maximum resolution is a limitation of my integrated intel card. Supposedly, newer nVidia (and probably ATI as well) cards have the ability for larger 3d resolutions. I guess it is time for a new video card.

---

