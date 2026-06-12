---
title: "Installing XP drivers."
date: 2011-11-06
forum: General Help
---

### Post by iLewis87 on 2011-11-06
I have just, this morning, installed Ubuntu onto my Acer Aspire T180.  I am happy with the OS my only issue is I now need to install the drivers for my D-Link DWA-142 wireless adapter to be able to access the internet.  I have a downloaded copy of the drivers on a disc however it does not read the files as being installable.

Any suggestions?


(btw if this has already been posted or is in the wrong thread please feel free to move it)


Thank you in advance.

---

### Post by BillyBoa on 2011-11-06
The best way to install the drivers is through a wire connection or by using a wireless pen (for me a D-Link is working perfectly).
When you establish internet connection, just search for proprietary drivers in your computer and if you are lucky you can download them easily.

---

### Post by gandaran on 2011-11-06
the adapter should work "out of the box", or at least that's what it says here and some instructions for ndiswrapper too
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
> I have a downloaded copy of the drivers on a disc however it does not read the files as being installable
from the HardwareSupport
> drivers are distributed in a executable file with no easy way to just extract the .sys and .inf files
you will have to find a way of extracting the driver package

which ubuntu version do you have?

post the output of
```
lsusb
```
and 
```
lsmod
```
this is just to check the wireless chipset and if any driver loaded.

---

### Post by iLewis87 on 2011-11-06
I am running Ubuntu 11.10 Oneiric Ocelot 

lsusb:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 07d1:3b10 D-Link System RangeBooster N Adapter
Bus 002 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Reciever
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader.

Unfortunately I am unable to post the lmod output as I can't transfer it off the machine and had to type the lsusb output by hand.

I have also noticed that it doesn't seem to recognise my any of my ports when inserting readable media (SD, USB etc)

---

