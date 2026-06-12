---
title: "Graphics help"
date: 2011-05-01
forum: General Help
---

### Post by memsb on 2011-05-01
Hi guy's i'm pretty clueless when it comes to setting up ubuntu. I've done my best with regards to getting the graphics to work properly, but i've reached my limit and need help!

Everything i try to do in 3D runs very slowly despite my laptop being good. Many 3D things dint render properly and are missing colours and textures.

Laptop spec:
Intel I7 620M
8GB DDR

Running glxgears gives me

```
3603 frames in 5.0 seconds = 720.463 FPS
3706 frames in 5.0 seconds = 741.034 FPS
3670 frames in 5.0 seconds = 733.989 FPS
3538 frames in 5.0 seconds = 707.510 FPS
3540 frames in 5.0 seconds = 707.815 FPS

```

Which is WELL down on what other people are getting with much older and slower hardware.

[http://ubuntuforums.org/showthread.php?t=39349](http://ubuntuforums.org/showthread.php?t=39349)

```
lspci|grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```

```
glxinfo|grep render
direct rendering: Yes
OpenGL renderer string: Software Rasterizer
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_fragment_program,
```

I've tried adding the edgers PPA and updating my no effect. Many places recommend doing things with the /etc/X11/xorg file, but i don't seem to have one... Could this be the problem?

Thanks

---

### Post by memsb on 2011-05-01
lshw

```
pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:8080(size=8)

```

So is i915 the intel integrated graphics? Or is that the driver currently being used?

---

