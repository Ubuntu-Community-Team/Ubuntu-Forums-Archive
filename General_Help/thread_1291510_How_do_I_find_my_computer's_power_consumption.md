---
title: "How do I find my computer's power consumption?"
date: 2009-10-14
forum: General Help
---

### Post by cat2005 on 2009-10-14
How can I determine my computer's power consumption while active (i.e., not checking BIOS upon boot, but while the computer is actually using harddrives, DVD drives, etc)?

My current power supply is 500w but I doubt I need all 500w.  I want to get an 80+ replacement.  The one that caught my eye was a 350w unit.  According to my mobo booklet (ASUS p4s800), 300w is recommended for a "fully configured" system.

I want to see how much power I consume to comfortably determine if 350w is enough because I don't fully trust the mobo booklet.  I want to see the consumption myself.

Thanks.

---

### Post by trstncmpbll on 2009-10-14
i think you can monitor that with conky. google conky variables and itll tell you what to add for it

---

### Post by tuxxy on 2009-10-14
sensors provides power usage I think.  Search for lm-sensors using Synaptic or enter in terminal
```

sudo apt-get install lm-sensors
```

---

### Post by XCan on 2009-10-15
Althought softwares in your computer may provide you with an estimate, I wouldn't trust them. Get one of those power meters that you plug inbetween your computer and your socket. Although they may not be accurate due to phase shifts etc in your PSU, I believe they will give you a far better estimate than a software installed in your computer.

It would also help if you posted what's in your setup, as you said 500 W is hardly needed for a normal computer.

---

### Post by CatKiller on 2009-10-15
> **XCan said:**
> Get one of those power meters that you plug inbetween your computer and your socket.

+1.

Quality is more important than overall capacity. Cheap power supplies will only tell you the peak power they can supply, not the continuous load they can handle, which makes the numbers fairly meaningless.

The advice used to be "get a higher-rated power supply than you need, since then it might be able to supply the (much lower) power that you do need well." As rules-of-thumb go, that's pretty customer-hostile.

There are online estimation widgets to give you a rough idea of how much power you're likely to use, which just leaves you the task of finding a power supply that can actually do it.

It's probably worth realising that not all power use is the same. For example, a power supply might be great at supplying power on the 12V rail, but that's of only marginal use if everything you use needs the 5V rail. And so on.

---

### Post by StuartN on 2009-10-15
Plug your computer into one of these [http://michaelbluejay.com/electricity/measure.html](http://michaelbluejay.com/electricity/measure.html) - Maplin, RadioShack etc sell them for about $15. Most people will discover changes in electricity use that will easily save the cost. It measures both instantaneous power and energy consumption (KWh) over any length of time, so it will measure the use by things like fridges that cycle on and off (or 24-hour PC use). The internal software monitors can not deliver any meaningful measure of energy use.

When you have finished with it, give it to someone else.

MacBook: 3W standby, 24W on; Dell Inspiron: 3W standby, 30W on; Desktop with cheap PSU: 0 W off, 184W on; Identical desktop with High Efficiency PSU: 0W off, 85W on.

A high efficiency PSU will only consume what you need, and should support the maximum load (when all the disks spin up together, processor maxout, display switch-on surge). A cheapo PSU will not ramp down as much.

---

### Post by CharlesA on 2009-10-15
Just wanted to note that a PSU will only use as much power as your system needs. Even if you have a 750W PSU, and your system is only using 200W of that, the PSU will pull 200W worth of power, but 750.

It really depends on the efficiency of the PSUs.

See [here]("http://www.pcpower.com/technology/myths/#m1").

---

### Post by XCan on 2009-10-15
That's true indeed. However, you can't in general optimize the efficiency for all loads. Thus, in most cases a 80+ certified PSU will only reach its most efficient level when the load is matched to its design, i.e., a load of 100 W will most definitely give you a worse efficiency if you're running a 1 kW PSU compared with a 200 W PSU.

In other words, there's little reason to buy a severely overdimensioned PSU for a system which both costs more and is less efficient, given the same quality. Of course if you plan to upgrade to something like crossfire or SLI the story is different. On the other case, the OP already have a PSU, so I don't really know the motivation for the downgrade. The effect I mentioned above, is generally rather small, and one would not save any significant amount of money to make it worthwhile by purchasin a whole new PSU. Perhaps the PSU is of very poor quality?

---

### Post by P4man on 2009-10-15
You need (far) more rated capacity than your machine actually draws at the wall socket even if you stress it as much as you can. A "350W" PSU gets the 350W label from adding together maximum loads on all its rails. A powersupply may have 2, 3 or 4 12v rails, one rail for 3.3v, one for 5v (and two more for standby power). Adding those together doesn't tell you that much. 

What matters more is the amperage of each rail, and you should compare that to what you need. E.g. if you have 10 harddrives and 2 videocards and a fat cpu in your machine, have 4x 12v rails, you will get much better use of the rated maximum power (ie, you will get close to it), then when you only have a single hugely overclocked power hogging quad core cpu or gpu drawing only from a single 12v rail, and leaving the 3 others unused.

That said, a good quality 350W should be enough for most normal desktop systems  as long as you don't have extreme videocard(s).

Other point someone else already mentioned: a 750W PSU doesn't necessarily consume more than a 350W under equal load, although  it is true most PSU's are more efficient near maximum load, that difference is neglectable (we are talking a few watts here).

---

### Post by cat2005 on 2009-10-15
Wow....I had no idea this could be so complicated.
 
Here is my setup
 
- mobo ASUS p4s800
- processor p4 @ 2.4 ghz @ 300 - 400 bus
- 1gb ram @ 300 - 400 bus
- 2 IDE hdd @ 80 gb each
- Lite-on DVD burner
- Sony DVD reader
- Nvida GeForce FX 5200 graphics
- No sound card
- I am at work so I can't look @ my computer to see the current powersupply, but I know it is 500w and not very efficient
 
I use the computer for: mythtv, email, word processing, etc. I rarely, if ever, play video games. I do not plan to leave the computer (mythtv) constantly running. If I did leave the computer (mythtv) constantly running, then would I need more power?
 
 
This is the 80+ 350w powersupply that caught my eye:
 
a) [http://www.rackmountpro.com/product.aspx?prodid=1638](http://www.rackmountpro.com/product.aspx?prodid=1638)
 
Do you think it would suffice for my needs? My current mobo booklet says "300" for a "fully configured system" but I don't know what is meant by "fully configured system". That is a very vague phrase.
 
Your insight would be appreciated.
 
Thanks.

---

### Post by P4man on 2009-10-15
It should be plenty for your hardware. however, check if it has the required connectors. modern PSU's often have very few molex connectors used on "old style" (pata) harddrives and optical drives, and instead have plenty of sata and PCIE (for videocard) power connectors. Those are probably useless to you,

---

### Post by charliehorse55 on 2009-10-15
Get the Corsair 400 CX

It's a rock solid power supply that supplies 360w on a single +12v rail, so you don't have to worry about balancing the load like the above user said. It has a maximum load of 400W and is certified to be 80 plus. I used to have one (Upgraded to the 750w model for SLI) and it was whisper quiet. You can't even tell when it is on. 

It's a great PSU.

---

### Post by djbon2112 on 2009-10-15
There's no real reliable way to do this in software (if so, us overclockers would have found it by now ;)). As others have said, get a power monitor and stick it between the PC and the wall. That will give you a good number to work with. If needed, narrow it down by retesting after removing components (i.e. video card, HDD, etc.).

---

### Post by XCan on 2009-10-15
I would always pick a well known quality brand then I can tell you that 350 W is enough. For example, the corsair suggested, seasonic or silverstone.

---

### Post by cat2005 on 2009-10-15
> **P4man said:**
> It should be plenty for your hardware. however, check if it has the required connectors. modern PSU's often have very few molex connectors used on "old style" (pata) harddrives and optical drives, and instead have plenty of sata and PCIE (for videocard) power connectors. Those are probably useless to you,
 
 
P4man,
 
I found a 400w psu which also interest me:  [http://www.amazon.com/Corsair-CMPSU-400CX-400-Watt-Certified-compatible/dp/tech-data/B001FXB7X0/ref=de_a_smtd/175-8364980-5722631](http://www.amazon.com/Corsair-CMPSU-400CX-400-Watt-Certified-compatible/dp/tech-data/B001FXB7X0/ref=de_a_smtd/175-8364980-5722631)
 
Of course, I use IDE cables.  How could I determine if this psu supports IDE cables?  Here is what I pulled from that above link:
 
**Technical Details **

[LIST]
[*]**Form Factor:** ATX
[*]**Wattage:** 400-Watt
[*]**Modular Cabling:** No
[*]**Energy Efficiency:** 80 PLUS
[*]**Fan:** 120 mm
[*]**Input Voltage:** 115 ~ 230
[*]**+3.3V:** 20 A
[*]**+5V:** 20 A
[*]**+12V 1:** 30 A
[*]**-12V:** 0.8 A
[*]**+5VSB:** 2.5 A
[*]**20+4-Pin Connector:** 1
[*]**Motherboard Connector:** 20+4 Pin
[*]**4-Pin/8-Pin EPS Connector:** 1
[*]**6-Pin PCI-Express Connector:** 1
[*]**4-Pin Floppy Connector:** 2
[*]**4-Pin Peripheral Connector:** 6
[/LIST]
How do I interpret that data?  Could it support my IDE harddrives?
 
Thanks.

---

### Post by djbon2112 on 2009-10-15
> **cat2005 said:**
> P4man,
 
I found a 400w psu which also interest me:  [http://www.amazon.com/Corsair-CMPSU-400CX-400-Watt-Certified-compatible/dp/tech-data/B001FXB7X0/ref=de_a_smtd/175-8364980-5722631](http://www.amazon.com/Corsair-CMPSU-400CX-400-Watt-Certified-compatible/dp/tech-data/B001FXB7X0/ref=de_a_smtd/175-8364980-5722631)
 
Of course, I use IDE cables.  How could I determine if this psu supports IDE cables?  Here is what I pulled from that above link:
 
**Technical Details **

[LIST]
[*]**Form Factor:** ATX
[*]**Wattage:** 400-Watt
[*]**Modular Cabling:** No
[*]**Energy Efficiency:** 80 PLUS [COLOR="Red"]<- Good: you want high numbers here, it means less wasted power and a better quality PSU[/COLOR]
[*]**Fan:** 120 mm
[*]**Input Voltage:** 115 ~ 230
[*]**+3.3V:** 20 A
[*]**+5V:** 20 A
[*]**+12V 1:** 30 A
[*]**-12V:** 0.8 A
[*]**+5VSB:** 2.5 A
[*]**20+4-Pin Connector:** 1 [COLOR="Red"]<- Means you can use on new motherboards with PCIe[/COLOR]
[*]**Motherboard Connector:** 20+4 Pin
[*]**4-Pin/8-Pin EPS Connector:** 1 [COLOR="Red"]<- Means you can use on new motherboards that support quad-cores[/COLOR]
[*]**6-Pin PCI-Express Connector:** 1 [COLOR="Red"]<- For your PCIe video cards[/COLOR]
[*]**4-Pin Floppy Connector:** 2 [COLOR="Red"]<- Floppy connectors[/COLOR]
[*]**4-Pin Peripheral Connector:** 6 [COLOR="Red"]<- Molex (i.e. IDE HDD, IDE CD/DVD, AGP video card) connectors[/COLOR]
[/LIST]
How do I interpret that data?  Could it support my IDE harddrives?
 
Thanks.

I added in red the details of what each one means.

So according to that, you can use up to 6 IDE devices and 2 floppies, not that you'd probably need that many ;) And Corsair makes pretty good power supplies; I think you'll be happy with it.

---

