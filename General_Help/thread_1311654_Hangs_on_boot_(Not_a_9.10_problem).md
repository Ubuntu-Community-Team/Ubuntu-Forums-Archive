---
title: "Hangs on boot? (Not a 9.10 problem)"
date: 2009-11-02
forum: General Help
---

### Post by Scott P on 2009-11-02
I've had a boot problem for a few weeks now (after having no such troubles for the first year and a half of this computer's life). I've been holding off in hopes that the 9.10 upgrade would fix it, but no such luck.

When I turn my computer on, the computer doesn't always turn on.  The case comes on, but the monitor gets no signal, and my USB devices (keyboard, mouse) get no power.  And there's no system beep, as I'd usually get at the beginning of any boot.

The only fix I've found for this is manually holding the reset button on the case.  Sometimes I press the reset once, sometimes it takes three or four times, but eventually, I get a system beep and the computer begins the boot process and starts up completely normally.

I don't know where to start diagnosing this. I've tried to look in the boot logs, but I'm not knowledgeable enough to identify anything that's not labeled "here's your boot problem." Any help identifying what's going on here and how to fix it would be greatly appreciated!

---

### Post by Giblet5 on 2009-11-02
I have seen this.

What appeared to fix it was replacing the CMOS battery on the motherboard.

In my case (heh heh), that was a CR2032 lithium button-cell battery. It looks like a shiny disk, about the size of a nickel, mounted in a battery clip on the motherboard.

Take off the skins and see. If you have one of those, replace it with the same type, then enter BIOS setup and re-tweak your date/time and any settings you normally change.

Those things die after a couple of years.

People throw entire systems away because a $2 battery died and the manuals hardly ever mention the thing (for obvious reasons).


Some motherboards have batteries soldered to the motherboard. Those are rechargeable, but they too go bad. Fixing that requires a soldering iron and a visit to [www.jameco.com](www.jameco.com)...

---

### Post by Scott P on 2009-11-02
So it's totally a hardware problem, then? Makes sense, I suppose.  I'll switch out the battery and see what happens.

---

### Post by Scott P on 2009-11-04
No dice - replacing the CMOS battery had no effect.

In my googling, I found that some people with similar problems had blown capacitors on their motherboards or video cards.  When I opened up my machine, everything looked perfectly intact, though.

Any other possible fixes?

---

### Post by Scott P on 2009-11-05
New symptom: I don't usually leave my computer turned on overnight. Last night, I did, and it had turned off by the morning.  I'd guess power supply or motherboard, but I'd be interested in the thoughts of the more knowledgeable. Thanks!

---

### Post by Scott P on 2009-11-05
(Anyone? Sorry to be impatient.)

---

### Post by lavinog on 2009-11-05
Sounds like a power supply issue to me.  Is this a hp / emachine / gateway type computer?
I have replaced a lot of <200W power supplies from those brands because they start to have issues with turning on.

---

### Post by pqwoerituytrueiwoq on 2009-11-05
just had  issus like this in my hardware class we were using fedora 
the clock needed to be set for it to boot 
you can do it form the bios 
press F1 or F2 to enter it

---

### Post by Scott P on 2009-11-08
lavinog: No, I built it myself about a year and a half ago; the power supply is a ~500W Earthwatts that came with my Antec 300 case.

pqwoerituytrueiwoq: I'll try resetting the clock in BIOS. Thanks for the tip.

If the clock idea doesn't work, I'm ordering a new power supply.  Thanks for the helps!

---

### Post by stephenlac on 2009-11-10
I'm having a similar problem. I can run Ubuntu 9.1 from the live CD, install it without problem. I can then run it ONCE booting from the hard drive. Running it a second time from the hard drive, the system hangs. The CMOS battery is fairly new and system clock remembers the time between sessions. I'm baffled by this. 

The same problems existed under Jaunty as well. I just never turned off the computer after I had it running, but some updates require a re-start and I'm screwed. 

I'm running a dual-boot system with Windows 7, and have no issues at all with Windows 7 booting and running.

---

### Post by lavinog on 2009-11-10
> **stephenlac said:**
> I'm having a similar problem. I can run Ubuntu 9.1 from the live CD, install it without problem. I can then run it ONCE booting from the hard drive. Running it a second time from the hard drive, the system hangs. The CMOS battery is fairly new and system clock remembers the time between sessions. I'm baffled by this. 

The same problems existed under Jaunty as well. I just never turned off the computer after I had it running, but some updates require a re-start and I'm screwed. 

I'm running a dual-boot system with Windows 7, and have no issues at all with Windows 7 booting and running.

You would be better off starting a new thread for your problem.  Your problem will not be the same as the OP on this thread.

---

