---
title: "Choosing which monitor the console displays on"
date: 2010-03-24
forum: General Help
---

### Post by BinarySplit on 2010-03-24
I'm running a multi-GPU multi-monitor system. I have 2 monitors on the primary GPU (lets call them monitors A and B) and 1 monitor(monitor C) on the secondary GPU. I'm running the restricted nvidia drivers on 10.04 beta 1. All my packages are up to date.

When Ubuntu boots (I have 'quiet' turned off, so I see the boot messages), the console appears on monitor A and displays correctly, as I'd like it. After GDM starts, however, if I press ctrl-alt-F1, monitors A and B show "No Input" and monitor C shows "Mode not supported". It appears that Linux is now only showing the console on GPU 2 and at an unsupported resolution.

If I unplug monitor C and reboot, both monitors A and B still show "No Input", so it seems like the console goes to GPU 2 whether or not a monitor is attached. The only way I've found to get the console to appear on GPU 1 is by physically removing GPU 2 from the computer completely.

This is quite a problem for me as I am currently trying to configure using multiple monitors with NVIDIA's drivers and cannot use the console to edit xorg.conf and restart GDM without removing the second graphics card and rebooting.

Is there any way to set which display the Linux console appears on? Alternatively, is there any way to disable my second GPU so that not even the Linux kernel tries to use it, without me physically removing the card?

---

