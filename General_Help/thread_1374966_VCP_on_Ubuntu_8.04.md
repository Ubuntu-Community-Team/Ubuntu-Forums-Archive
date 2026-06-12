---
title: "VCP on Ubuntu 8.04"
date: 2010-01-07
forum: General Help
---

### Post by zdoor on 2010-01-07
Does anybody now how Virtual Com Ports (VCP) are named on Ubuntu?

/dev$ ls | grep ttyS

This returns the normal 4 com ports numbered 0 to 4

/dev$ ls | grep ttyUSB

This returns nothing.

/dev$ ls | grep usb

This returns 12 entries like: usbdev1.1_ep00, usbdev1.1_ep81 etc. But these ports I cannot open with Python pyserial.

There are numerous tty ports (tty, tty1, ttya etc.). But I want to have the ones that support VCP, i.e. that I can open as a serial port, using RS232.

Thanks, Alex van der Spek

---

