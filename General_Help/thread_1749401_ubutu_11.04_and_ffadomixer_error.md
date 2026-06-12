---
title: "ubutu 11.04 and ffadomixer error"
date: 2011-05-04
forum: General Help
---

### Post by gordsd on 2011-05-04
I hope I posted this at the right spot.  Forgive me I'm new to Ubuntu, anyway,

My son got me started using Ardour, and it worked good with a Digteck USB inerface I had (with Ubuntu 10.10 and Ardour).  However I wanted to use my Multimix firewire* for multitrack recording and I read that it worked. Sooo, I went to Ubuntu 11.04 because of what ppalmers wrote at <wwww.ffado.org/?=node/61>  I have an Alesis mulitmix8 firwire which I want to work with Ardour.  After updating from Ubunto 10.10 to 11.04 beta (I think it was the latest version; I always updated), I couldn't get Jack to open; I would see the window for a split second and then it would disappear.  When I tried opening the ffado mixer I would get:  "logginghandler: Could not communicate with the FFADO DBus service..."  I looked for solutions and tried this (from "Balky Dbus" article <http://www.linuxplanet.com/linuxplanet/tutorials/7119/1> "ffado-dbus-server" and got:
-----------------------------------------------
FFADO Control DBUS service
Part of the FFADO project -- [www.ffado.org]("http://www.ffado.org")
Version: 2.999.0-
(C) 2008, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

 Discovering devices...
01189349722: Fatal (devicemanager.cpp)[ 191] initialize: No firewire adapters (ports) found.
01189349764: Error (ffado-dbus-server.cpp)[ 277] main: Could not initialize device manager
no message buffer overruns

I tried lspci and it shows the firwire:   00:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)

I tried following firewire steps at : <https://help.ubuntu.com/community/FireWire> and this did not help either; I tried the cammand which was advized " ls -al /dev/raw1394 " and got
ls: cannot access /dev/raw1394: No such file or directory
gordon@music-box:~$ 

I did this after disabling raw and re-booting and re-enabling raw, and then rebooting.  I can't get ffado to work?  and I can't get Jack to open since i went to 11.04.  I updated today and I still get the same messages.

I'm new to ubuntu so, please help if you can.

---

