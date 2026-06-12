---
title: "Need help sending hex code via rs232 cable"
date: 2009-08-01
forum: General Help
---

### Post by Afkpuz on 2009-08-01
Hey guys, I'm trying to control my tv using it's rs232 port, but am completely lost as how to do this.  I am using a usb>serial plug cable and found this command to send the signal via the command line
```
echo "ka 01 00" > /dev/ttyS0

```

I was led to believe that this command should turn off my tv, but nothing happens.  So, my first question is: How do I tell if I have the correct /dev name?  Since this is a usb to cable, does that change the name?

Second, is this even the proper way to send a this sort of signal?  Here are the tech specs of the type of sygnal I'm supposed to send from the LG tv manual.

Baud rate : 9600 bps (UART)                      
Data length : 8 bits
Parity : None
Stop bit : 1 bit
Communication code : ASCII code
Use a crossed (reverse) cable.

Any help would be appreciated.  Tv model is the 42LG50.  And yes, this is a rs232 control port.  I checked. Thanks

---

### Post by cajhdz on 2009-10-20
hi, the problem is that at the end of your "hex" word el command echo ... > port sends a feed line so at the you have and extra 0x0A you can probe that gathering tx to rx.

---

