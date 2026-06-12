---
title: "Question about lshw"
date: 2010-05-04
forum: General Help
---

### Post by darkestfright on 2010-05-04
I was just wondering, what does it mean when a device is highlighted in red when viewing an -html output of lshw?  At first I thought it meant that there was no driver for the hardware but after installing on an older machine, the only 'red' device is my video card (ATI Radeon 9200SE) which seems to be running fine even with compositing enabled (using the open source ATI drivers) so I'm not really sure.

Any help is appreciated.

---

### Post by gzarkadas on 2010-05-04
The red color is for .node-unclaimed class (you can check yourself looking at the <head>...</head> part of the output); so it is for unclaimed hardware, I think. What is the specific output for the device in question?

---

