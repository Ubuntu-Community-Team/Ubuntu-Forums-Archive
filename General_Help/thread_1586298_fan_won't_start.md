---
title: "fan won't start"
date: 2010-10-01
forum: General Help
---

### Post by Don DeGregori on 2010-10-01
Have Lucid 10.04 on Intel D510MO mini-ITX MB. Decided to install a 12 volt 40 mm fan, which has 2 wires. Header has 3 pins. I see 11 volts (not sure why it's low), 5 volts, and ground. First connected fan to external 12 volts. No problem. Now connected to the 12 volt and ground of fan header. Started computer. Fan doesn't start. Voltage that was 11 drops to 0.85 volts. I believe the unused pin is for tachometer, but again this fan has 2 wires. I do have the polarity correct. As soon as I disconnect the red (plus) of fan, voltage goes back up to 11. Using a DVM. Any ideas?
Thanks, Don

---

### Post by coffee412 on 2010-10-01
> **Don DeGregori said:**
> Have Lucid 10.04 on Intel D510MO mini-ITX MB. Decided to install a 12 volt 40 mm fan, which has 2 wires. Header has 3 pins. I see 11 volts (not sure why it's low), 5 volts, and ground. First connected fan to external 12 volts. No problem. Now connected to the 12 volt and ground of fan header. Started computer. Fan doesn't start. Voltage that was 11 drops to 0.85 volts. I believe the unused pin is for tachometer, but again this fan has 2 wires. I do have the polarity correct. As soon as I disconnect the red (plus) of fan, voltage goes back up to 11. Using a DVM. Any ideas?
Thanks, Don

You probably need a 3 pin fan. You are correct that pin 3 is the tach. A tach registering 0 rpms probably has the circuit discontinued as a safety feature is my guess. If you want take the power directly from one of the rails of the powersupply.

---

### Post by Don DeGregori on 2010-10-01
I did what you suggested. Not going worry about fan control or showing speed. I need the fan blowing right over a new mini-PCI wireless card. It's much cooler now!
Thanks

---

### Post by arvevans on 2010-10-01
It sounds like what coffee412 said.  The tach lead senses no fan rotation so it drops the 12 volts to almost zero so it won't burn out the fan motor (assumes a stuck blade or bad bearing condition).

As a work-around, try running your fan directly off the 12 volt connectors that go to disk drives.  This way you can run your 2-wire fan from the full 12 volts with no rotation sensing.

---

### Post by CharlesA on 2010-10-01
You could also turn fan control off in the BIOS.

---

