---
title: "screen freeze"
date: 2010-11-12
forum: General Help
---

### Post by taojian on 2010-11-12
I'm using 10.10 on a Lenovo Zhaoyang laptop, 64-bit. The screen freezes up every once in a while, the pattern seems to be every ten minutes or so, I'll have a minute where it locks up briefly and repeatedly.

While it's doing this, the screen does not refresh, and the mouse (trackpad) won't move. If I don't touch it, it generally comes back within a few seconds. Input during those few seconds is lost: the computer seems to actually not be running at all. The keyboard can usually make it responsive again: what I've found works best is to use the desktop switching keys to bounce in and out of the current desktop, usually that works. Sometimes just typing does it.

I've got the system monitor applet running. While it's having a locking fit, CPU usages goes way up (two cores), but top or iotop don't show anything unusual. After a minute or two CPU usage goes back down, and the computer returns to normal.

This happens with any combination of applications running. I've noticed this particularly with the terminal: I can have nothing but the terminal running, and it will get into this thing where the result of each keypress isn't displayed until the next keypress, so the screen is always one keypress behind. I've also seen it in emacs, no other applications that I can think of. I just noticed that, when it's really freezing, I can hold down a key (any key, a modifier key is nice), and everything continues to progress so long as I keep the key depressed. I can let it up, and it freezes. Press again, and it continues. Again, it actually seems to be the processors locking up, not just the screen failing to refresh.

It's actually happened to me while shutting down the computer: it logs me out, starts the shutdown process, freezes, and then needs me to bang on the keyboard to get it all the way there. It's even hung at the Ubuntu logo, with the five dots below: I have to press random keys for the dots to fill in and the computer to shut down.

Some stuff:

```

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```

```

$ sudo lshw -C display
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:f4000000-f43fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f4400000-f44fffff

```

```

$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

In case it's a trackpad related thing, these "mouse" related packages are installed:

xserver-xorg-input-mouse
xserver-xorg-input-vmmouse

dmesg is too large to attach here. I've looked through it, and while I don't know what I'm looking for there are a bunch of suspicious looking lines like this:

```

[11831.087031] psmouse.c: GlidePoint at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[11833.781878] psmouse.c: resync failed, issuing reconnect request

```

Hopefully all this will be enough to sniff out a problem… Thanks in advance!

Eric

---

### Post by taojian on 2010-11-15
Monday morning bump, sorry&#8230;

---

### Post by taojian on 2010-11-15
Can't delete this...

---

