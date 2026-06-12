---
title: "Logitech USB wireless headphones doesn't work. Please help!!!"
date: 2011-09-04
forum: General Help
---

### Post by BlackoutWorm on 2011-09-04
Hey guys. I've been googleing this problem for a long time now trying to find a solution. But all I can find is unsolved posts from people dealing with the same problem as I do.
All logitech's usb wireless headphones work out of the box in Windows but not linux.
There doesn't seam to be any linux drivers for this, neither Pulse, oss or alsa seem to recognize the headphones.
Nomatter what audio setting I change or usb port I try, allow or block for headphone support, nothing seem to work.

Please, is there ANY thing at all I can do to fix this thing?
Or alternative 2. Are there any wireless usb headphones that will work with linux?
Trust me, I've checked for days now to find and come up with a solution.
But then again, I'm just a beginner with linux, and PC isn't really interesting to me, so I am the type of person who usually give up pretty quick when it comes to things like this.
But I really want it to work.
And who know, maybe the answer is a very obvious one that noone has found yet.

---

### Post by kbeals on 2011-09-04
I'm using the Logitech H760 wireless headset and it works fine under 10.10 through PulseAudio. I did not have any issues, just plugged it in and updated the 'output' settings in the sound preferences menu. I have it set to use both the internal sound and the wireless so I can drive external devices at the same time.

---

### Post by Docaltmed on 2011-09-04
If you type "lsusb" in a terminal, do the headphones show up?

---

### Post by BlackoutWorm on 2011-09-05
I don't think so. Here's the output:

Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0955:7002 NVidia Corp. 
Bus 002 Device 003: ID 045e:0745 Microsoft Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0b05:1788 ASUSTek Computer, Inc. 
Bus 001 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 13d3:5122 IMC Networks 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by BlackoutWorm on 2011-09-07
bump

---

### Post by BlackoutWorm on 2011-09-08
Bump

---

