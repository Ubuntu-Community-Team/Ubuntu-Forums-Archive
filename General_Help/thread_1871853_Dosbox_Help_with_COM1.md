---
title: "Dosbox Help with COM1"
date: 2011-10-29
forum: General Help
---

### Post by CadillacRick on 2011-10-29
Hey,

I'm trying to use DOSBOX ver 0.74 to run an old Motorla programming app in DOS to reprogram an old VHF radio. However it seems that DOSBOX is having problems communicating with COM1 where the Radio Interface Box (RIB) is connected.

Now in Ubuntu I can communicate with /dev/ttyS0 just fine by using ls > /dev/ttyS0 and I can see the lights flashing on the Radio Interface Box that is connected to COM1 so Ubuntu is not the problem.. it sees the port and the box attached to it.

When I start Dosbox I have the COM1 port configured with this command in the dosbox.conf file

serial1=directserial comport=1 realport=ttyS0

Now i've also tried

serial1=directserial comport=COM1 realport=/dev/ttyS0

and I just can't seem to get Dosbox to communicate with the Radio Interface Box connected to COM1 (/dev/ttyS0)...


Need Help !!!!  Anyone ????

And by the way, I tried running a VirtualBox with DOS... and the Motorola software won't run on it at all... I only get Divide Overflow...    it only seems to want to start up in the DOSBOX environment... 


Help !!


:)

---

### Post by CatKiller on 2011-10-30
DOSBox is focused on old games. It's possible that you'll have more luck with DOSEmu instead, which is set up to be a more accurate emulation.

---

### Post by CadillacRick on 2011-10-30
Thanks for the input.. i'll give that a try later today and see if I can get it to recognize COM1 through /dev/ttyS0


:)

---

### Post by CadillacRick on 2011-10-30
Tried the DOSemu and the motorola program won't start in there either....  it keeps giving me the Interrupt Divide by Zero error.. and then dumps the stack... 

It seems like this program will only run in DOSbox but still haven't figured out how to communicate through COM1 to the Radio Interface Box...   still can't proceed any further..

Any help would be appreciated :)

---

### Post by dcstar on 2011-10-31
> **CadillacRick said:**
> Hey,

I'm trying to use DOSBOX ver 0.74 to run an old Motorla programming app in DOS to reprogram an old VHF radio. However it seems that DOSBOX is having problems communicating with COM1 where the Radio Interface Box (RIB) is connected.

Now in Ubuntu I can communicate with /dev/ttyS0 just fine by using ls > /dev/ttyS0 and I can see the lights flashing on the Radio Interface Box that is connected to COM1 so Ubuntu is not the problem.. it sees the port and the box attached to it.

When I start Dosbox I have the COM1 port configured with this command in the dosbox.conf file

[B]serial1=directserial comport=1 realport=ttyS0
[/B]
Now i've also tried

**serial1=directserial comport=COM1 realport=/dev/ttyS0**

and I just can't seem to get Dosbox to communicate with the Radio Interface Box connected to COM1 (/dev/ttyS0)...


Need Help !!!!  Anyone ????

And by the way, I tried running a VirtualBox with DOS... and the Motorola software won't run on it at all... I only get Divide Overflow...    it only seems to want to start up in the DOSBOX environment... 


Help !!


:)

That is not the correct syntax according to this:

[http://www.dosbox.com/wiki/Dosbox.conf#.5Bserial.5D](http://www.dosbox.com/wiki/Dosbox.conf#.5Bserial.5D)
or this:
[http://sense.net/~egan/virtual82240b/](http://sense.net/~egan/virtual82240b/)

---

### Post by pandrews on 2013-04-09
> **dcstar said:**
> That is not the correct syntax according to this:

[http://www.dosbox.com/wiki/Dosbox.conf#.5Bserial.5D](http://www.dosbox.com/wiki/Dosbox.conf#.5Bserial.5D)
or this:
[http://sense.net/~egan/virtual82240b/](http://sense.net/~egan/virtual82240b/)

I know this is an old topic, but I ran into the same problem, and for the sake of clarity, my COM1 port is /dev/ttyUSB0 (usb to 9 pin serial) and my line for Dosbox is:

```
serial1=directserial realport:ttyUSB0
```

---

### Post by oldos2er on 2013-04-09
Old thread closed.

---

