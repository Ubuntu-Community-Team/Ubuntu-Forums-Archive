---
title: "Terminal screens are garbage"
date: 2010-11-12
forum: General Help
---

### Post by pteri498 on 2010-11-12
When I try to view one of the terminal screens (for example, via alt-F1), the screen shows garbage:

[Photo of Monitor]("http://imgur.com/UbbmM.jpg")

The startup splash shows up in much the same way.

I imagine it has something to do with my resolution/video card. The default resolution is 1366x768. My hardware is as follows:

```

$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Manhattan [Mobility Radeon HD 5000 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:36 memory:c0000000-cfffffff(prefetchable) memory:d4000000-d401ffff ioport:4000(size=256) memory:d4040000-d405ffff(prefetchable)

```

Any advice?

---

### Post by TeoBigusGeekus on 2010-11-12
Add these lines in your /etc/default/grub file.
```
GRUB_GFXMODE=1024x768x32
GRUB_GFXPAYLOAD_LINUX=keep
```
Fiddle with different resolutions until you find the maximum supported one.
Don't forget to update grub afterwards
```
sudo update-grub
```
Reboot and post back with the outcome.

---

