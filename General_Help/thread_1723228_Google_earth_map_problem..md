---
title: "Google earth map problem."
date: 2011-04-06
forum: General Help
---

### Post by haudace on 2011-04-06
Basically, I am having a huge problem with Google Earth (and some games, vendetta online for instance), just take a look at the attached map picture hehehe. It could be an issue with the graphic card (ati radeon x1200) which is no longer supported by its company :( but maybe not. Anyone come across this problem and fixed it?:confused:

Running Ubuntu 10.10, and default open source driver for ATI. I also noticed I don't have direct rendering for OpenGL using hardinfo GUI. I tried to google how that might affect google earth and gaming, and I didn't find anything useful on how to enable it. Any help will be very appreciated.


```
description: VGA compatible controller
       product: RS690M [Radeon X1200 Series]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64
       resources: irq:18 memory:d0000000-dfffffff memory:f0100000-f010ffff ioport:9000(size=256) memory:f0000000-f00fffff

```

Edit: Everything works fine now. I just played vendetta a few minutes ago.

---

### Post by haudace on 2011-04-13
This ubuntu [page]("https://help.ubuntu.com/community/RadeonDriver") could help some people.

---

### Post by mwacky on 2011-04-15
I have the same problem.  Turns out my laptop cannot deal with the proprietary driver: ATI Radeon Xpress 200M in 10.04+  so I'm limited to the open source driver which works great for all cases but Google earth Shattering problem.

---

### Post by haudace on 2011-05-03
Fixed with upgrade to 11.04 natty. Must be the new promised graphic driver hehehe. Thank you Canonical. Solved?

---

