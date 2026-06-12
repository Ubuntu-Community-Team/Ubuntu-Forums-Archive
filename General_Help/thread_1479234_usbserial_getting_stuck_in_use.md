---
title: "usbserial getting stuck in use"
date: 2010-05-10
forum: General Help
---

### Post by MeisBarry on 2010-05-10
I've been working with an Arduino (usb microcontroller board) together with Python a bunch recently, and I've been having intermittent trouble with the usb interface.

In Python I'm using the pyserial library to talk with ttyUSB0.  Normally it works great, but sometimes (not always) during prototyping the script exits in error, and afterwards the serial port becomes unusable.  Neither Python nor the Arduino's own IDE can talk to the serial port.  Plugging in a second Arduino, un/replugging in, etc does not work.  The only consistent solution I've found is a system restart.

lsmod says usbserial is used by 2 things, ftdi (which is the serial driver needed) and an unknown process.  I can rmmod ftdi, but can't do the same for usbserial since another process is still using it.  modprobing doesn't do anything, neither does rmmod -f.

Besides restarting and making sure I never have errors when prototyping, I can't think of a solution for this, either preventative or responsive.  Any ideas?

---

