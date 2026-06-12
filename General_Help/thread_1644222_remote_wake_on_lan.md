---
title: "remote wake on lan"
date: 2010-12-13
forum: General Help
---

### Post by dannyry on 2010-12-13
I am trying to conserve electricity and was looking for a linux WOL app that will allow me to remotely wake my windows 7 computer so I can stream music on demand.  I have to believe this exists/is possible.  I am also an idiot so if there is such a thing I'm going to need help getting it up and running.

---

### Post by tredegar on 2010-12-13
Just install **wakeonlan**
```
wakeonlan -i IP.OF.WINDOWS.PC XX:XX:XX:XX:XX:XX
```
where XX:... is the HW address of the NIC on the win PC  to
wake up the win PC.

---

### Post by dannyry on 2010-12-15
I assume I have to have something up and running on the windows pc to do this?  I am trying to wake up a windows 7 pc for this. First attempt did not work.

---

### Post by stinkeye on 2010-12-15
> **dannyry said:**
> I assume I have to have something up and running on the windows pc to do this?  I am trying to wake up a windows 7 pc for this. First attempt did not work.
You need to enable this feature in the BIOS.

---

### Post by tredegar on 2010-12-15
> **dannyry said:**
> I assume I have to have something up and running on the windows pc to do this?  I am trying to wake up a windows 7 pc for this. First attempt did not work.
Not as far as I know. 

Some things to check:

There may be a BIOS option to enable/disable this feature on your NIC. Not all NICs / Motherboards support WOL, you should check your hardware specifications.

Or maybe you have to shut down windows some special way. I know nothing about windows though.

Although your PC is "shut down" it still needs to supply power to the NIC, or it won't be able to listen for the magic packet.

---

### Post by tredegar on 2010-12-15
Found a link for how to set up windows here:
[http://onlineforall.info/2010/08/how-to-wake-your-pc-on-lan/](http://onlineforall.info/2010/08/how-to-wake-your-pc-on-lan/)

---

### Post by dannyry on 2010-12-16
thanks all, unfortunately i was unable to get it to work since I run off a PCI wifi card (I created the win7 reg key for wifi to work after googling it) and tried to change power settings in the bios and device manager, however it seems impossible to do a wowlan most of the time in 7.  But I learned something new, thank you.

---

