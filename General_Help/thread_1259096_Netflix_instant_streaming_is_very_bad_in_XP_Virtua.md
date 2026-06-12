---
title: "Netflix instant streaming is very bad in XP VirtualBox"
date: 2009-09-05
forum: General Help
---

### Post by hansamurai on 2009-09-05
I've got a beefy computer: AMD Phenom 2 3Ghz Quad Core, 4GB RAM, Geforce 9800 GTX+, Ubuntu 9.04, and I have a Windows XP VirtualBox installation with these settings:

1.5GB RAM
1 Processor
VT-x/AMD-V Enabled
Nested Paging Enabled
PAE/NX Disabled
128MB Video Memory with 3D acceleration enabled

Video is very slow and choppy, probably about 5 frames per second and totally unwatchable.  Audio may not work at all but I'm worrying about that later.  My internet connection is fast enough to handle the streaming to my Xbox 360.

If anyone has had luck with this, that would be awesome. Thanks!

:popcorn:

---

### Post by ckonestroh on 2009-09-06
ADD RAM ?????


Virtual box never had a problem streaming video????

what was the size of the virtual hard drive?????

your settings are on a bit of the slim side...

should only be running the virtualbox emulator at time of watching movie....

Would tax the system to much on ram...????

What type of connection??? should be cable or higher...

check connection speed watch a Youtube video if its choppy your speed is to slow....

---

### Post by hansamurai on 2009-09-06
I set it to 2GB RAM and all four processors, but that still didn't help.  But then I disabled Nested Paging and all of a sudden things seem really smooth.  I'm going to keep working on it.

---

### Post by Stone_Soup on 2009-09-06
I'm running XP on a 2.5Ghz Dual Core 4850e with only 1G allocated to the VM and it streams awesome. In fact it starts up faster than when its actually installed as an individual "real" machine. Its so wierd watching a streaming movie in XP while I do work on the Ubuntu host but thats what makes this so awesome.

I haven't done any tweaking to my virtual installation of XP (except sound host controller) and everything worked at default. I don't think it could be your connection because it would just go to the Netfilix buffer screen. Perhaps its a video adapter issue? Maybe check device manager and your adapter status. It sounds a lot like the chop I'd get prior (in Windows at least) to installing my video driver.

---

### Post by hansamurai on 2009-09-06
Really seems like it had to do with the Nested Paging thing, once it was disabled, Netflix and Youtube ran smoothly, even after clocking it back down to 1.5GB and 1 CPU.  Odd, but I'll take it.

---

