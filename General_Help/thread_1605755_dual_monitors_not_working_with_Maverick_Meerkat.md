---
title: "dual monitors not working with Maverick Meerkat"
date: 2010-10-25
forum: General Help
---

### Post by squidgy45 on 2010-10-25
Hi, I have been using ubuntu for a year or so with little trouble until now. I have done a fresh install of 10.10 and my second monitor doesnt work. I have Intel G31 graphics. It was working fine with 10.4 and previously 9.4, it displays the bios splash  screen and then nothing. System>preferences>monitors does not show it as present at all. Here is my lshw -C video:

 *-display:0             
       description: VGA compatible controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:fe980000-fe9fffff ioport:dc00(size=8) memory:d0000000-dfffffff memory:fe800000-fe8fffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82G33/G31 Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fe780000-fe7fffff

Any help appreciated, thanks.

---

### Post by squidgy45 on 2010-10-26
no help here then?

---

### Post by squidgy45 on 2010-10-28
Well thanks guys, problem still exists and noone can be bothered to help. Looks like its back to Win 7 until ubuntu can get its act together. At least there is plenty of help and support there!

---

### Post by jacky.alcine on 2010-10-30
I had an issue with getting a dual mointor setup on Maverick (10.10).

I looked at this site:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Configure_Dual_Monitors_with_nVidia](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Configure_Dual_Monitors_with_nVidia)

and it worked like a charm.
just make sure both monitors are on.

---

### Post by squidgy45 on 2010-11-01
Thx for the reply but my graphics are Intel not nVidea, but appreciate the respnse.

---

### Post by gmargo on 2010-11-01
Post #4 on this thread give info on a xorg fix: [http://ubuntuforums.org/showthread.php?t=1594087&highlight=dual+monitors](http://ubuntuforums.org/showthread.php?t=1594087&highlight=dual+monitors)

---

