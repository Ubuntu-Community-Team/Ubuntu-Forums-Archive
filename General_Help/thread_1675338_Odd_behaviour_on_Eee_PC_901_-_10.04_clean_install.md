---
title: "Odd behaviour on Eee PC 901 - 10.04 clean install"
date: 2011-01-25
forum: General Help
---

### Post by M1ke on 2011-01-25
Hi, I've just reinstalled 10.04 on my Eee 901 and noticed that performance has taken a hit since the last installation. There are three main issues that I think might all be related:


[LIST]
[*]The boot time is much longer than before, though still no more than a minute or so.
[/LIST]

[LIST]
[*]The CPU frequency scaling applet on my top panel is only occasionally responsive - on most boots I can right-click it to reach the context menu but left-click no longer brings up options for power profiles or CPU frequencies. Removing and re-adding it doesn't solve the problem, but in the previous installation everything was fine.
[/LIST]

[LIST]
[*]Cairo Dock's performance has slowed to an absolute crawl when using OpenGL. Was fine previously.
[/LIST]

I fixed the dock by simply running "cairo-dock -c" on boot instead of -o, but I include the problem here as I have a feeling all three problems might be related. For some reason, I have a sneaking suspicion that all of it is some kind of graphics/display issue.

I'm plugged in to an external monitor if that makes any difference, but the issues are present even when using the laptop screen.

---

### Post by M1ke on 2011-01-27
I've solved all these problems now except the lengthened boot time; it seems using synaptic to remove games has the potential to remove files needed for optimal video/audio performance. Strange as I've done so before on another system with no ill effects, but I thought I'd at least note the solution here for anyone who gets the same issue in future.

The issues were resolved by running the following command:

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```Which for me also sneakily removed ubuntu-desktop, so to undo that I entered:

```
sudo apt-get install gdm ubuntu-desktop
```I noticed on running that command apt-get was pulling in game-related files I had previously removed to clear space on the Eee's tiny 4GB SSD. One last command to ensure all the necessary audio files were reinstalled:

```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```And a reboot later I once again had a fully functional Cairo Dock with OpenGL, a usable CPU frequency scaling applet and audio. Credit to LordRaiden for providing the terminal commands in [this thread]("http://ubuntuforums.org/showthread.php?t=205449").[U]
[/U]

---

