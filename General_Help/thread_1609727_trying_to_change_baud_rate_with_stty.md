---
title: "trying to change baud rate with stty"
date: 2010-10-30
forum: General Help
---

### Post by sportsdude81 on 2010-10-30
I am using the command:

```
sudo stty -F /dev/ttyUSB0 115200
```

to try and change the baud rate from 9600 to 115200 on device USB0, but I keep getting this error.

```
stty: /dev/ttyUSB0: unable to perform all requested operations
```

ttyUSB0 is not locked, and I know it is capable of 230400 b/s so I know it should handle 115200 just fine.  Any ideas?

---

### Post by efflandt on 2010-10-30
I believe **stty** is for setting the baud rate of a terminal.

The **setserial** command is used to set the baud rate of a serial port(unless Ubuntu uses something else, because setserial is not installed by default)

---

### Post by adummy on 2010-10-31
A related question: Is it possible to change the baud rate to 2,000,000 in Ubuntu? It works fine with Windows XP. Thanks!

Here is the current setserial info:
```
setserial -a /dev/ttyUSB0 
/dev/ttyUSB0, Line 0, UART: unknown, Port: 0x0000, IRQ: 0
    Baud_base: 24000000, close_delay: 0, divisor: 0
    closing_wait: infinite
    Flags: spd_normal low_latency

```

Does this mean if I set divisor to 12 then I get 2000000? Thanks!

---

### Post by sportsdude81 on 2010-11-01
> **efflandt said:**
> I believe **stty** is for setting the baud rate of a terminal.

The **setserial** command is used to set the baud rate of a serial port(unless Ubuntu uses something else, because setserial is not installed by default)

Sorry should of mention this before I get the same error message with setserial

```
sudo setserial /dev/ttyUSB0
Cannot get serial info: Invalid argument
```

I know it works because i can use screen to talk to it just fine.

```
screen /dev/ttyUSB0 230400
```

Any ideas?

---

### Post by sportsdude81 on 2010-11-01
Is there any way to configure ttyUSB* before the USB serial device is plugged in or to configure it permanently?

---

### Post by efflandt on 2010-11-01
What kind of USB to serial device do you have?  It works for me for just the USB/serial cable with nothing connected to it:

**lsusb | grep -i serial**
Bus 002 Device 004: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port

**sudo setserial -av /dev/ttyUSB0**
```
/dev/ttyUSB0, Line 0, UART: 16654, Port: 0x0000, IRQ: 0
    Baud_base: 460800, close_delay: 0, divisor: 0
    closing_wait: infinite
    Flags: spd_normal
```PS: I cannot change any settings though.  Maybe that is simply determined by whatever pace programs or devices communicate through it.

I wonder if my USB cable is USB 1.0 and adummy's is USB 2.0.  The one I got is just to communicate with an ancient Garmin GPS45 (from mid-1990's) at 4800 baud.  Although, I have not figured out how to do that in Linux yet (programs seem to use minimum 9600 baud).

---

### Post by sportsdude81 on 2010-11-01
I don't have the hookup right now because I left it at work, but I'll post up what lsusb prints out.  The hardware is a 3G cellular modem hooked with a 2.0 USB cord and the computer sees 4 serial hookups 2 of which I can talk to and use for a connection.  First step change the baud rate. Second step set it up so both connections are seen as one.  Got a lot of debugging to do :-D.

My problem is setserial can't talk to it at all.  can't even get a print out from setserial.

---

### Post by HermanAB on 2010-11-02
Howdy,

Use Cutecom (very nice) or Minicom (clunky).

---

### Post by sportsdude81 on 2010-11-02
I actually prefer screen, but I use wvdial and pppd to connect.  My problem is I can't change the baud rate to get the full potential out of my modem though.

---

### Post by sportsdude81 on 2010-11-02
Well I guess this solves my problem my computer doesn't see the 4 ttyUSB* connections as serial ports.

lsusb gives:

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 1bc7:1004  
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0461:4d64 Primax Electronics, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6363 Alcor Micro Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 050d:845a Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
lsusb | grep -i serial
``` doesn't return anything

---

### Post by adummy on 2010-11-03
> **HermanAB said:**
> Howdy,

Use Cutecom (very nice) or Minicom (clunky).

How do you set the cutecom baud rate to 2M (2000000)? It has very limited choices in the gui.

---

