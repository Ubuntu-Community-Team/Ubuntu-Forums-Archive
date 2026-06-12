---
title: "Laptop fails to start windows environment after upgrade"
date: 2011-04-05
forum: General Help
---

### Post by yamokosk on 2011-04-05
I recently installed the 32bit version of 10.10 on my Dell Latitude E6510. Everything went smoothly.. in fact I was quite impressed as I have my laptop in a docking station connected to dual 24" displays. The installer recognized them and they worked perfectly right outta the box: yea for Ubuntu :D!

After the install, I installed some apps then upgraded the installation to the latest hotness - lots and lots of things were upgraded. I restarted the machine to "complete the upgrade process" and it boots but right when it gets to starting the Windows environment, both display just loose their signal... :(

It boots fine to the command line if I boot in safe mode. I had installed the nVidia drivers but I did that before the update and I had no problems until I did the system update. Any ideas? Should I start by disabling the 3rd party drivers? If so, how would I do that?

---

### Post by spacesamurai on 2011-04-05
I have this same problem every time I upgrade the kernel. What I always have to do is enter the command line and reinstall the driver there. once done, I restart and this is fixed. Could you try reinstalling the driver from the command line?

---

### Post by Mark Phelps on 2011-04-05
Not to be discouraging, but I regularly encounter this same problem with 10.10 -- starts to boot but ends up with blank screen on both displays.

What I have found to work in most cases is to bring up the GRUB menu, select Recovery Mode, once there, select the option to repair broken packages.  When that is done, select the option for normal boot, and if that worked OK, you will have a working desktop (and dual screens) again.

Good Luck

---

