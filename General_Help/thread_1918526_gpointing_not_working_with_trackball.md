---
title: "gpointing not working with trackball"
date: 2012-02-01
forum: General Help
---

### Post by lusop on 2012-02-01
Hi there,

I used my ubuntu on Monday with no problems at all, but today my trackball doesn't care about my gpointing setup.

Middle button emulation works whether it's setup or not (I think it already workedbefore I started using gpointing, and there's no way of making scrolling work, either vertically or horizontally.

I already tried reconfiguring the gpointing-device-settings package, but with no positive results.

My trackball, if important, is a Logitech one, and has always worked properly.

Thanks for any help!!!

---

### Post by ridgeland on 2012-03-12
I'm searching for a fix for gpointing-device-settings (gds).  In 10.10 it works fine. In 11.04, 11.10 and 12.04 beta 1 gds ignores the settings when I reboot. That is gds in gnome2 great, gds in gnome3 broken.  Broken in Xubuntu 11.10.  Broken in Lubuntu 11.10.

This is stupid but this is the ONLY fix I've found.
I launched gds and while it was open I anchored it to the launcher, have to set it EVERY boot.  Now each boot is three steps to get my scroll wheel emmulation working.
1 - gds - turn off emmulation - close gds
2 - gds - turn on emmulation but to button 2 - close gds
3 - gds - change emmulation button from 2 to 3 - close gds
Now it works.  Emmulation with button 3 for my track ball. Stupid stupid.  3 screens later the settings are exactly as they were at boot but now it works! huh?

Any clues?
Anyone know why it takes three shots when the settings file is correct at boot time?

---

