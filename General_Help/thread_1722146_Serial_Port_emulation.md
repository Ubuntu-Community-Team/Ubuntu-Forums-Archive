---
title: "Serial Port emulation"
date: 2011-04-05
forum: General Help
---

### Post by Don1500 on 2011-04-05
I am trying to use one serial port simultaniously for two different programs.

I have a two programs that use GPS information that I would like to run at the same time. At this time only one program at a time can access a serial port. I have found a way to emulate this in Windows so that I can have both running, now I'm trying to do the same in Ubuntu. Is it possible? If yes, How?

The GPS receiver is connected via a USB port.

---

### Post by mikejonesey on 2011-04-06
you'd have to write a program that opens and closes the port and writes to ports which the two programs will end up using;

why do you want both programs on the same port?

---

