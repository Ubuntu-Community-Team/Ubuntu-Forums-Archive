---
title: "Binary serial port communication - what tool ?"
date: 2012-01-13
forum: General Help
---

### Post by Andre-D on 2012-01-13
Hi.
I need to test hardware that needs to receive 8bytes - not letters
using normal 57600bps 8,n,1 - but no longer than 100ms delay between characters in a burst is acceptable, so I cannot type it manually.

So I need to send (for example) 8 hexadecimal numbers as 8 bytes:

for expample, if I could paste this; 
0x00 0x73 0x38 0x93 .... 

The hardware will reply in the same manner
- and I'd like to *see* the incoming data as decimal or hex codes, not the mess it would normally cause in a serial terminal.


What program /script /application can I use to accomplish this ?

---

### Post by dcstar on 2012-01-16
> **Andre-D said:**
> Hi.
I need to test hardware that needs to receive 8bytes - not letters
using normal 57600bps 8,n,1 - but no longer than 100ms delay between characters in a burst is acceptable, so I cannot type it manually.

So I need to send (for example) 8 hexadecimal numbers as 8 bytes:

for expample, if I could paste this; 
0x00 0x73 0x38 0x93 .... 

The hardware will reply in the same manner
- and I'd like to *see* the incoming data as decimal or hex codes, not the mess it would normally cause in a serial terminal.


What program /script /application can I use to accomplish this ?

*nix Serial Ports are /dev/tty ports, you can use them as with any file and any suitable application that can read/write to a file (which is basically every *nix app).

For some more info on serial ports:
```
man stty
man getty
```

---

