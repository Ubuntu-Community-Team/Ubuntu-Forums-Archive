---
title: "Two webcams in flash problem"
date: 2011-11-23
forum: General Help
---

### Post by alex_4u_89 on 2011-11-23
My system: Ubuntu 10.04, Flash 11,0,1,152, Firefox 3.6.17

I have a problem using two identical webcams simultaneously in flash.

If I use the same model webcams the first loaded webcam is black(as it is in use) but the second webcam is loaded fine. If I use two webcams from the same vendor there is the same problem.

If I use two different webcams it works fine. It loads and display both.

lsusb output:
Fail:
Bus 001 Device 006: ID 0ac8:3420 Z-Star Microelectronics Corp. Venus USB2.0 Camera
Bus 001 Device 003: ID 0ac8:3420 Z-Star Microelectronics Corp. Venus USB2.0 Camera

Ok:
Bus 002 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam
Bus 001 Device 003: ID 0ac8:3420 Z-Star Microelectronics Corp. Venus USB2.0 Camera

All webcams use v4l2 driver.

Any suggestions?

---

