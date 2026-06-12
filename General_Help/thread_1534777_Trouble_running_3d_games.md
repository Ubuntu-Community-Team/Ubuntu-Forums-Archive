---
title: "Trouble running 3d games"
date: 2010-07-20
forum: General Help
---

### Post by Juan_Solo on 2010-07-20
Hello, this is my first post! :D
Anyways, I'm having trouble running games like ut2004, Stormbaan Coreur, Spring, every game under wine (not the issue here, just saying) curiously everything with the in-game menus works fine, but when I try to start the game it just crashes.

I have an ATI Radeon 9250, Ubuntu 10.04, open source drivers

Here's the terminal output from running ut2004:
```
WARNING: ALC_EXT_capture is subject to change!
IRQ's not enabled, falling back to busy waits: 0 1
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
drmRadeonCmdBuffer: -12. Kernel failed to parse or rejected command stream. See dmesg for more info.

```Although "dmesg" doesn't give much information, just a bunch of this:
```
[50524.596051] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[50524.925044] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).
[50525.324706] phy0 -> rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16).

```What should I do?

---

### Post by Juan_Solo on 2010-07-21
Anyone?

---

### Post by MaxIBoy on 2010-07-21
Unfortunately, the Open Source drivers aren't as good as the proprietary ones (although for your card they *should* be nearly up-to-par by now.) And you can't use the latest proprietary drivers with your card. If you want to use proprietary drivers with your card, you're looking at a downgrade to Ubuntu 8.04 for the older X server.

I know for a fact that Spring does not render correctly on my Intel GMA 960 laptop because of hardware limitations, and for all I know your Radeon card might not meet the requirements as well-- the Spring website says it needs a GeForce 4 MX or later, and the GeForce 4 series was a year later than the Radeon 9000 series. So that might be causing the problem for Spring.

Ut2004 could be crashing because the Linux version stinks and hasn't been updated or maintained for years (and I never did get the native version working right, it always crashed just like how you describe.)

I'd suggest working your way up from some really basic game engines, so starting at ioQuake3 (free games on that engine include Urban Terror, World of Padman, and OpenArena,) and then Darkplaces (free games on that engine include Xonotic and Nexuiz.) See if you can figure out about the level of graphics your hardware and drivers can support.

---

