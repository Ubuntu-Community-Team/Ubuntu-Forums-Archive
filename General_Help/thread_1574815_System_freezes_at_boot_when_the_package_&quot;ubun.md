---
title: "System freezes at boot when the package &quot;ubuntu-desktop&quot; is installed"
date: 2010-09-14
forum: General Help
---

### Post by ygoe on 2010-09-14
Hi,

I have set up a server with Ubuntu 10.4. It always worked fine with 32-bit inside VMware. But on the production machine with 64-bit, it wasn't working well by now. I could now reliably trace the problem down to the "ubuntu-desktop" package. I have installed it (without the recommends) so all its depends are also installed. But as soon as that package is on the system, it freezes at boot time, on the page where CPU freq modules or AppArmor stuff is started. My server is an Intel Core i7, so it lists 8 CPUs for cpufreq. They're normally all listed in a line on their own, but when the system freezes here, the output is broken already. Sometimes it says that cupsd is started, or "Checking quotas", sometimes it stops after "CPU4", sometimes it prints out the lines "CPU0" to "CPU4", then "CPU7" in the same line followed by "[OK]". The system won't react on anything from then on except a hard reset.

As soon as I remove the package "ubuntu-desktop" (chrooted into the system from the rescue system), the OS on disk boots normally into the GUI logon. No problem at all anymore.

It took me a few days to figure out why it wasn't working. I first suspected quota, then a kernel upgrade. But the system booted well after each change on their own. Just as I installed all the graphical stuff, it stopped booting.

What's happening there? What am I supposed to to now? I need the desktop environment and the machine must be working by Saturday. Although the description of ubuntu-desktop says that I should not uninstall it because it's used for update management, I could now install it to get all its depends, and then immediately uninstall it to make the system boot up again. Is that a good idea? Shouldn't it be working without such hacks?

---

### Post by dcstar on 2010-09-15
> **LonelyPixel said:**
> Hi,

I have set up a server with Ubuntu 10.4. It always worked fine with 32-bit inside VMware. But on the production machine with 64-bit, it wasn't working well by now.
..........

Is this a "normal" installation or a VM installation?

---

### Post by ygoe on 2010-09-15
The server that shows the problem was installed by an image installation provided by the data centre operator (Hetzner Online). It should be a pretty normal installation, they should only have modified the network configuration and possibly other minor settings.

My VM setup was a normal interactive setup from the Ubuntu 10.4 Server CD. In both cases the installation only contains minimal packages, no GUI or anything. I then proceed and install those packages myself. One of them is ubuntu-desktop.

---

### Post by ygoe on 2010-09-25
Well, it turned out it wasn't that particular package, but it was the X server starting locally on the machine. The graphics driver seems to be unstable so that it freezes directly before showing the graphical login. Since this is a web server and a GUI is only used via NX, there's no need to run gdm for login and I have disabled it. Now everything is okay. But this was a tricky issue because there was nothing to see but some scrambled startup messages before the end. It stopped working at a different point every time, I suppose it's upstart's parallel way of starting apps that made the exact time of failure somewhat random, misleading me every time.

---

