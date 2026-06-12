---
title: "What is failing at pre-boot?"
date: 2010-06-27
forum: General Help
---

### Post by HousieMousie2 on 2010-06-27
A bit of strangeness here...

Intermittently, when I power on my machine, it fails to boot.

The fans come on, the case lights come on, the "drive" light on the case comes on and stays on... but the CD drives never spin up and nothing is being sent to my monitor (it just goes into stand-by/power saving mode.)

The reset button does nothing.

Holding down the power button for 30 seconds powers off the machine.

-----

I have tried just waiting for the boot to complete, but nothing happens.

I have tried leaving the machine off for a while then powering on again... this has hit and miss results.

I have tried turning off/on the power supply unit (via it's own switch) and trying again... this seems to do the trick.

-----

I know I am never reaching Linux (and just not seeing it since the display is dark) because when I do get a normal boot Linux doesn't complain about a bad shut down or scan /Boot.

-----

How can I determine that POST initiates/completes?

I do not have a spare PSU, that can boot this machine, to rule out the PSU.

-----

I have not yet tried pulling everything out to do a bare-bones start up... largely because the problem is so intermittent.  Since my machine is the server for the other machines in the house, if I left it at bare-bones for a couple of weeks to see if the problem still occurred... they would find my bludgeoned body in a ditch somewhere. 8-[

I could use a little help here, so thanks in advance to anyone and everyone who tries to lend a hand... er... brain.

---

### Post by nacho32 on 2010-06-27
the power supply is underrated it if your running a add on video card and have a internal remove it it should boot . If your sure the power supply is not underrated I would suggest  remove the cmos battery, unplug tower hit button to discharge and put battery in few minutes latter, If this fails I would say the motherboard is going or a possible bad stick of ram.

---

### Post by HousieMousie2 on 2010-06-27
> **nacho32 said:**
> the power supply is underrated it if your running a add on video card and have a internal remove it it should boot . If your sure the power supply is not underrated I would suggest  remove the cmos battery, unplug tower hit button to discharge and put battery in few minutes latter, If this fails I would say the motherboard is going or a possible bad stick of ram.


Thanks for replying nacho32.

I *believe* that my PSU is not underrated, it is an 800W.  And for the past few years it has not had an issue, and I have not added anything new to the mix.

I will try replacing the CMOS battery... again, since the problem is intermittent popping out the battery every time it fails to boot would not be an easy way to see if it is the problem. lol

I will also run MemTest to check the RAM.

Thanks again, nacho32 for the suggestions.

---

### Post by ajgreeny on 2010-06-27
If this is a desktop machine that you can get at and check things, try re-seating the disk cables and such things, by disconnecting and then reconnecting them along with anything else you can get at.

Very occasionally, on my old machine with two IDE hard disks, I get a problem in POST when the screen display says "Detecting IDE disks" or something like that, and it goes no further, ie no disks are seen by the BIOS.  Pressing the reset button does not help, but repeats the problem, but if I press the power button to completely remove power, and the restart, all is OK.  Since this happened a lot more at one time I used this reseating trick and it is much less common now; perhaps once a month at most.

I have also suspected the power supply unit on the machine, but it is now hardly worth bothering to change that on a 5 or 6 yr old computer, so I live with the problem.

---

### Post by HousieMousie2 on 2010-06-27
> **ajgreeny said:**
> If this is a desktop machine that you can get at and check things, try re-seating the disk cables and such things, by disconnecting and then reconnecting them along with anything else you can get at.

Very occasionally, on my old machine with two IDE hard disks, I get a problem in POST when the screen display says "Detecting IDE disks" or something like that, and it goes no further, ie no disks are seen by the BIOS.  Pressing the reset button does not help, but repeats the problem, but if I press the power button to completely remove power, and the restart, all is OK.  Since this happened a lot more at one time I used this reseating trick and it is much less common now; perhaps once a month at most.

I have also suspected the power supply unit on the machine, but it is now hardly worth bothering to change that on a 5 or 6 yr old computer, so I live with the problem.

Thank you for replying, ajgreeny.

This machine is a little over a year old and is not moved or even jostled, so I doubt loose cables would be the sudden culprit, but while I have it open to replace the CMOS battery, I will be doing a complete cleaning too, and checking all connections.

Thanks again.

---

