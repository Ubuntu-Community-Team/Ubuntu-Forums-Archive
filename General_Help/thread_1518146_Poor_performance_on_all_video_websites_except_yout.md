---
title: "Poor performance on all video websites except youtube"
date: 2010-06-26
forum: General Help
---

### Post by haider.malik on 2010-06-26
I don't want to go back to Windows! Help! :(

- all videos on all websites except YT lag - 90%+ CPU utilization
- few(i think older) videos on YT lag - 90%+ CPU
- a lot of(i think newer) videos on YT run fine - 50%-60% CPU
  - these lag too on switching to full screen - 90%+ CPU

Ubuntu 10.04 LTS.
Same behavior on Firefox and Chrome with latest player from Adobe.
Same behavior on Chrome 5.0.375.86 with integrated player.

---

### Post by haider.malik on 2010-06-27
bump!

---

### Post by Oolongtea on 2010-06-27
I also seem to be having this problem with video sites. I was fine on Xubuntu 8.10 but It has become unbearable since I've upgraded to 10.04.

---

### Post by stderr on 2010-06-27
This is almost certainly the same issue as you posted about in [this]("http://ubuntuforums.org/showthread.php?t=1518726") thread. It looks like, post upgrade, your video driver hasn't fared well. lshw output will tell us what video card you're running and what graphics driver (proprietery, open source, etc) you're currently running.

---

### Post by haider.malik on 2010-06-27
*-display UNCLAIMED     
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:e8000000-efffffff(prefetchable) memory:ff680000-ff6fffff

I did not do an upgrade. It was a clean install.

---

### Post by stderr on 2010-06-27
Yeah, from [your xorg.conf]("http://ubuntuforums.org/showpost.php?p=9516570&postcount=6") you're running the intel driver. You will probably find that the vesa driver is stable, but that'll give poor performance, poor resolutions and no 3d acceleration.

Edit: many others seem to be having similar issues [http://janvandevoort.wordpress.com/2010/03/27/ubuntu-9-10-with-vga-intel-82845gglbrookdale-gge/]("http://janvandevoort.wordpress.com/2010/03/27/ubuntu-9-10-with-vga-intel-82845gglbrookdale-gge/")

Possible workarounds: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes")

---

### Post by haider.malik on 2010-06-27
These workarounds are not working for me. :(
I hate it. I've decided to switch to some other distro.

---

