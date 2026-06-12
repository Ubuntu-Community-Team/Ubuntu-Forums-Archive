---
title: "Need help with serial port"
date: 2011-04-04
forum: General Help
---

### Post by mugwump40 on 2011-04-04
Hi:  I have a home built PC with a AMD Phenom X2 processor, Gigabyte GA-MA785GM-US2H MOBO, and a plug in serial card.  Can someone tell me how to list the serial card to find the port, IRQ, UART, etc??  If I do lsusb, I get:

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08bb:2904 Texas Instruments Japan PCM2904 Audio Codec
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 03f0:3812 Hewlett-Packard 
Bus 001 Device 003: ID 2001:f103 D-Link Corp. [hex] DUB-H7 7-port USB 2.0 hub
Bus 001 Device 002: ID 04f2:a13c Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I think the Chicony Electronics is the serial card, but not sure.  It is NOT the Audio Codec as this is a separate piece of hardware (outboard sound card) and works fine. Here is what I'm trying to do.....I'm a ham radio nut and I'm trying to get a "push to talk" signal to my transmitter via the DTR or RTS on the serial port.  I have one software program set up where it works great, but it was automatically assigned (FLDIGI).  I am trying to get WSJT to key up the transmitter and I have to assign the "TTY" device in the options.  Don't let the ham radio part deter you, it is really just a simple :-) setup of the serial device.  Any help will be deeply appreciated.

---

### Post by matt_symes on 2011-04-04
Hi

Plug the device in. Open a terminal and type

```
sudo lshw | less
```

Enter your password. It will not be echoed to the screen. It has to run with root privileges to get extra information.

It is piped into less so you can use the up and down arrows to see what is reported. Press q to quit less.

You can also redirect into a file.

Hopefully, that will give you (at least some of) the info you need.

Kind regards

---

### Post by mugwump40 on 2011-04-11
Somehow, the routine updates to UBUNTU solved the problem and all works well, now.

---

