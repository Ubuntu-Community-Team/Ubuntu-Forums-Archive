---
title: "Controlling Sony STR-DA3500ES AV-receiver via RS-232 using Mythbuntu 9.10 HTPC"
date: 2010-12-06
forum: General Help
---

### Post by morge on 2010-12-06
I'm hoping you can give me some pointers how to get  my HTPC<->receiver setup working the way it should. My goal is to  use HTPC to send on/off signals to receiver when suspending/resuming.  Additionally I'd like to query receivers current input and if needed,  switch to proper HDMI.

Some info: I've connected my  Mythtv-running Ubuntu-based HTPC to Sony STR-DE3500ES AV-receiver using  null-modem (female-female) serial cable. Receiver is set up to use  serial port (installer mode or something like that it was called) and I  can see some sort of communication going on as I run minicom from HTPC  and switch receiver on and off. Minicom is set up to use proper settings  (9600 baud, 8N1) but all the info coming from the receiver and shown on  the minicom screen is garbled (binary?). I've tried echoing some of the  Sony-specific commands found here to /dev/ttyS0 but receiver doesn't  react to those in any way. I've tried to figure stty out to setup the  serial interface to correct settings, but without any luck so far. Only  way to see any communication to actually happening is to use minicom (so  far).

Any tips how to debug this one?

---

