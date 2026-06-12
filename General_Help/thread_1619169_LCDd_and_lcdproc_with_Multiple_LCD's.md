---
title: "LCDd and lcdproc with Multiple LCD's"
date: 2010-11-11
forum: General Help
---

### Post by vcolonel on 2010-11-11
Hi all (First post woop),

Having problems with getting multiple LCD working with Ubuntu 10.10. I have installed LCDd and lcdproc "correctly", and I have it working outputting "g15stats -d" to my Logitech Z-10 speaker LCD.

However, on my Logitech G15 rev2 display, I have nothing. When i unplug said speakers USB connection, I can get it up on the keyboard. Has anyone ever got this working with 2 USB fed LCD's?

My /etc/LCDd.conf snippet as below:

```
# The following drivers are supported:
#   bayrad, CFontz, CFontz633, CFontzPacket, curses, CwLnx, ea65, 
#   EyeboxOne, g15, glcdlib, glk, hd44780, icp_a106, imon, imonlcd, IOWarrior,
#   irman, joy, lb216, lcdm001, lcterm, lirc, lis, MD8800, ms6931, mtc_s16209x,
#   MtxOrb, mx5000, NoritakeVFD, picolcd, pyramid, sed1330, sed1520, serialPOS,
#   serialVFD, shuttleVFD, sli, stv5730, svga, t6963, text, tyan, ula200,
#   xosd
#Driver=curses
Driver=g15

# Tells the driver to bind to the given interface
Bind=127.0.0.1

# Listen on this specified port; defaults to 13666.
Port=13666
```

If anyone can shed any light i'd be more than grateful :)

BR, 
Sam

---

