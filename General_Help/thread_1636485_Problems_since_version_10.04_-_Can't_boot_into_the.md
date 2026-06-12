---
title: "Problems since version 10.04 - Can't boot into the OS at all"
date: 2010-12-03
forum: General Help
---

### Post by andrept on 2010-12-03
Good morning, Ubuntu community!  I come here with a question regarding a problem I have with Ubuntu on my laptop. 

It's quite worrying actually, I can't boot the installer (I can boot the Live CD/DVD though) nor my updated system from 9.10, which worked perfectly.

I tried searching around in the Internet for help, read the release notes and tried boot flags when booting the system, such as noapic, nolapic and nodomoset. None work properly. I get either a blinking cursor or a screen that's turned off.

I should stress that version 9.10 of Ubuntu works like a charm, apart from having packages that are all out-of-date, meaning it's a pain to keep my system up-to-date and install new programs.

Ubuntu 10.10 Maverick Meerkat also doesn't work (properly, 10.04 doesn't work at all). When I set the boot flags needed for the system to boot (I use nolapic and noapic), 10.10 does boot but it's hopeless. It only detects 1 core of the CPU and I get 80% CPU load when the system's idle, not to mention it's slower than Windows Vista. A lot slower.

So, my question is: Is there anything I can do (other than wait and pray for Natty to fix things and downgrade back to Karmic while that's fixed), or should I just quit using Ubuntu, (which is something I just can't accept)? :(

My system has an Intel Pentium Dual-Core CPU @2 GHz, an nVidia geForce 9300m GS and 4 GB of RAM.

---

### Post by andrept on 2010-12-03
update: I booted the old 9.10's kernel, 2.6.31-22-generic-pae, and it booted just fine! So, is this a kernel issue?

---

