---
title: "usb2serial problem with pl2303 (pl2303x)"
date: 2011-01-27
forum: General Help
---

### Post by Dair T'arg on 2011-01-27
I have some device (particularly telescope mount) which can be controlled by software through a serial port. However I have no serial ports in my computer so I want to plug it using usb2serial adapter (pl2303x).

But I've failed to send and receive any through that adapter. Here is what was done:

The following line of code fails to complete (so computer just waits for something):

```
fd = open ("/dev/ttyUSB0", O_RDWR|O_NOCTTY);
```

If I'm trying to use O_NONBLOCK|O_NOWAIT flag than it seems that nothing is send and definetly nothing is received.

So, the next step was to try to use some shell commands. But something like that has failed too:

```
echo 'V' < /dev/ttyUSB0 > /dev/ttyUSB0 
```

(The device should respond with '22' on 'V' request as said in manual)

So for now I don't even know where the problem could be? It may be driver problem (the adapter is visible in the system but no serial terminal (ttyS*) has been created). It may be some hardware problems too... So does anybody have any ideas?

---

### Post by coldraven on 2011-01-27
I don't know about the USB side but when I used to do lots of RS232 comms a tester was invaluable. Something like what's in the links below.

[http://cgi.ebay.co.uk/Serial-RS232-DB9-DTE-DCE-9-LED-Link-Tester-No-Power-Req-/150554079116?pt=LH_DefaultDomain_0&hash=item230db8ef8c](http://cgi.ebay.co.uk/Serial-RS232-DB9-DTE-DCE-9-LED-Link-Tester-No-Power-Req-/150554079116?pt=LH_DefaultDomain_0&hash=item230db8ef8c)

[http://cgi.ebay.co.uk/9-pin-RS232-Tester-USB-Serial-Adapter-Converter-Cable-/260584827479?pt=LH_DefaultDomain_0&hash=item3cac10ea57](http://cgi.ebay.co.uk/9-pin-RS232-Tester-USB-Serial-Adapter-Converter-Cable-/260584827479?pt=LH_DefaultDomain_0&hash=item3cac10ea57)

---

### Post by tgalati4 on 2011-01-27
I've only used the pl2303 driver with gps USB pucks and it works reliably.  Have you looked at the source code (pl2303.c) to see how to initialize the driver?

What does:

dmesg | tail

say?

---

