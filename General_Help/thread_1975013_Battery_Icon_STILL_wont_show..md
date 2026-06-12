---
title: "Battery Icon STILL wont show."
date: 2012-05-06
forum: General Help
---

### Post by Hwensta on 2012-05-06
I already made a thread for this but none of the people helped. 
Today I downloaded Wubi to try out Ubuntu obviously and when it started working it was really fun seeing all the things it had to offer. After that I wanted to see if it would be a good replacement for my Windows 7. So far that is a No. This is because the little battery icon thats supposed to show me how much battery I have left in my laptop isnt showing up. Ubuntu reconizes my computer as a laptop but still wont show it. I have tried the following:
- Set it to show. 
- Search for Drivers
If someone could help you might just give Ubuntu another customer.

---

### Post by llamabr on 2012-05-06
No reason to start a new thread.  Just bump the old one.

What if you right click the top panel, choose 'add to panel' and then choose 'battery charge monitor'?

---

### Post by llamabr on 2012-05-06
also it looks like you could run:

```
gnome-power-manager
```

also, probably search the repositories for other neat stuff:

```
brock@vader:~$ apt-cache search battery stat
acpid - Advanced Configuration and Power Interface event daemon
kacpimon - Kernel ACPI Event Monitor
acpitail - Show ACPI information in a tail-like style
acpitool-dbg - command line ACPI client (debug)
acpitool - command line ACPI client
apmd - Utilities for Advanced Power Management (APM)
libapm-dev - Library for interacting with APM driver in kernel
libapm1 - Library for interacting with APM driver in kernel
xapm - X program to monitor APM battery status
awn-applets-python-core - A collection of applets for Awn, written in python
batmon.app - Battery monitor for GNUstep
battery-stats - collects statistics about charge of laptop batteries
chiark-utils-bin - chiark system administration utilities
collectd-core - statistics collection and monitoring daemon (core system)
gkrellm-thinkbat - ThinkPad laptops battery status indicator for GKrellM
gnome-power-manager - power management tool for the GNOME desktop
gkrellm-ibam - Advanced battery monitor for laptops - gkrellm plugin
ibam - Advanced battery monitor for laptops
laptop-mode-tools - Tools for Power Savings based on battery/AC status
libacpi-dev - development files for libacpi
libacpi0 - general purpose library for ACPI
libifp-dev - communicate with iRiver iFP audio devices (development files)
libifp4 - communicate with iRiver iFP audio devices
libosso-dbus-conf - Basic library for maemo applications - Scratchbox D-Bus configuration
libosso-dev - Basic library for maemo applications - development files
libosso1-dbg - Basic library for maemo applications - detached debug symbols
libosso1-doc - Basic library for maemo applications - documentation
libosso1 - Basic library for maemo applications - shared library
osdsh - Overlays your screen with various system information
tp-smapi-dkms - ThinkPad hardware/firmware access modules source - dkms version
tp-smapi-source - ThinkPad hardware/firmware access modules source
wmacpi - ACPI battery monitor for WindowMaker
wmbattery - display laptop battery info, dockable in WindowMaker
wmibam - dockapp to monitor the apm status using ibam
xbattbar - Display battery status in X11
yacpi - ncurses based acpi monitor for text mode
awn-applets-python-core-trunk - A collection of applets for avant-window-navigator
brock@vader:~$ 

```

All sorts of stuff there when you look for it.

---

### Post by schulwitz on 2012-06-25
Did you find a solution for this?  I had a similar missing battery meter due to my booting with acpi=off.  Check you grub.conf file and see if you have any special acpi options configured.

I'm a noobie too, but here's the solution I found: [http://ubuntuforums.org/showthread.php?t=1366304&page=2](http://ubuntuforums.org/showthread.php?t=1366304&page=2)

---

