---
title: "Weird yellow/orange areas everywhere"
date: 2011-10-27
forum: General Help
---

### Post by aylons on 2011-10-27
This is very, very weird: random triangles and rectangles appears in my Ubuntu screen, regardless of the applications currenly running.

They are not the maximize orange rectangle, and they keep changing as I type, move the mouse or anything else changes in screen, eg. an animated gif.

Sometimes, they are related to the current event (as a whole paragraph changing color as I type), but the colors also change in apparently unrelated areas, even outside the current application screen.

I have already tried installing Gnome 3, with no success. However, the problem had stopped for a few days last week, and I though it was gone, but it has come back.

This is not an intermitent problem - every time I logged in this week it has happened. I attached some screenshots so you can see the nature of the problem.

---

### Post by decoherence on 2011-10-27
That's weird! Is this a laptop? I haven't seen that before -- at least, not due to software.

I would suggest seeing if the problem is still there if you boot from a live CD to rule out a hardware issue (it can happen!)

Might also be useful to know what kind of video card you have and which driver you're using.

```
sudo lshw -C video
```

---

### Post by aylons on 2011-10-27
sudo lshw -C video

```
  *-display               
       description: VGA compatible controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:41 memory:fe980000-fe9fffff ioport:dc00(size=8) memory:d0000000-dfffffff memory:fe800000-fe8fffff

```

This is not a laptop, this is a desktop computer. However, I have just ran an 11.04 live CD for a few minutes on it, and there is the problem again.

I would guess hardware, however, the problem didn't show up until I installed Ubuntu. While I was using Fedora, it didn't happen. I tried to run a Fedora 14 CD, but it also happens it isn't a Live CD. :cP

The installer screen for Fedora didn't show any glitches, though.

I think I will download another Live CD for trying, but it will have to wait until tomorrow.

---

### Post by decoherence on 2011-10-27
Could just be co-incidence that it started happening when you installed Ubuntu. Then again, it could also be that the Ubuntu live CD and your install are using the same video driver and it really doesn't like your video chip, so trying a completely different distro's liveCD is a good idea.

---

