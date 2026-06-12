---
title: "Monitor Not Detected 11.10"
date: 2012-01-06
forum: General Help
---

### Post by squid636 on 2012-01-06
I have installed Ubuntu 11.10 on my desktop and I had to plug in a second monitor to get the operating system installed. I was hoping that after installation that I would be able to detect the Sceptre monitor. I am not an expert at Linux so I really dont know what I need to do or install so I can use my monitor. Can anyone give me some suggestions? Thanks.

System Information: Intel® Core™2 Quad CPU Q6700 @ 2.66GHz × 4
Graphics Card: GeForce GTS 250
NVIDIA Driver Version: 280.13
Monitor 1: NEC LCD1715 (Ubuntu detects and displays correctly on this monitor)
Monitor 2: Sceptre X246W-1080p (Ubuntu does not detect this display at all, not even during boot.)

---

### Post by conradin on 2012-01-07
Do you have the NVIDIA driver for that card?
As in the one from NVidia, no the linux generic one.
[http://www.nvidia.com/object/linux-display-ia32-290.10-driver.html](http://www.nvidia.com/object/linux-display-ia32-290.10-driver.html)
in version 2.90

I'm curious to know if the monitor shows up in the output of the command ```
sudo lshw
``` 

For additional giggles, I might switch the screens as in plug in the sceptre into port 1 on the Graphics Card, maybe even solitary just to verify it really really doesn't see the thing, and that its not something to do with the configuration of the graphics card.

---

