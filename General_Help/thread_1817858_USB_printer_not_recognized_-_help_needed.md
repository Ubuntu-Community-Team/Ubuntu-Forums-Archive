---
title: "USB printer not recognized - help needed"
date: 2011-08-03
forum: General Help
---

### Post by AussieGuy on 2011-08-03
I am trying to get my Lexmark E210n printer to work through a USB port.  Originally I had it set up (at home) as a network printer, and it worked perfectly.  Now I have it at work, directly attached to my desktop.  However, the desktop refuses to recognize the printer.

In CUPS, there's no USB option in "Add Printer" -> "Local Printers"; dmesg produces nothing, and lsusb produces:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

It seems as if my entire system (which is an up-to-date version of Ubuntu 10.04) is missing something which allows it to recognize USB printers.

Can anybody give me a little advice here?

Thanks very much!

-A.

---

