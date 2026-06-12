---
title: "Dell 1355cnw printer drivers?"
date: 2011-06-06
forum: General Help
---

### Post by bird_4321 on 2011-06-06
I'm trying to find a Dell 1355cnw printer driver that will work with Zorin OS 4 system.  I searched the forums and there doesn't seem to be anyone else with this problem.  Please HELP!:confused:

---

### Post by lindend on 2011-07-15
Did you ever get this problem resolved?  Just got this printer too and would like to know what the right drivers are to install for it.

---

### Post by lindend on 2011-07-15
They seem to be based on this Xerox print engine:


[http://www.action-intell.com/2011/02/23/xerox-finally-introduces-printer-based-on-low-cost-color-led-engine-and-ea-eco-toner/](http://www.action-intell.com/2011/02/23/xerox-finally-introduces-printer-based-on-low-cost-color-led-engine-and-ea-eco-toner/)

---

### Post by hacor on 2011-08-22
I was wondering if there is any progression on the subject? I also have a Dell 1355cnw and want to use it in Ubuntu. It now is attached to a network. Tried to experiment with the .ppd file for mac, but without success...

Best,

H

---

### Post by birdy_ on 2011-11-02
Same here. My company bought a 1355 cnw and I'm the only one using Ubuntu... Try some drivers with no success.

---

### Post by Arielxgbarton on 2012-01-03
I also have this problem. I have been on many forums and there nothing about 1355cnw - it is just not listed

---

### Post by 1proton on 2012-09-04
As Linux driver for Dell 1355cnw the one for **Xerox WorkCentre 6015N** can be used :p
Dell does not provide Linux drivers for the Dell 1355cnw :mad:(even if there were some available!).
But as the 1355cnw is almost a clone of the Xerox WorkCentre 6015N the Xerox drivers can be used.
See:
[http://www.support.xerox.com/support/workcentre-6015/downloads/enus.html?operatingSystem=linux&fileLanguage=en]("http://www.support.xerox.com/support/workcentre-6015/downloads/enus.html?operatingSystem=linux&fileLanguage=en")


For x64 systems there is a problem with the drivers but also a HowTo fix it ....
[http://www.bertol.de/tiki-index.php?page=Xerox+WorkCentre+6015N+on+Linux+64bit+system&structure=Content&no_bl=y]("http://www.bertol.de/tiki-index.php?page=Xerox+WorkCentre+6015N+on+Linux+64bit+system&structure=Content&no_bl=y")

---

### Post by datajack on 2012-10-12
Thanks for the info in this thread. I have this printer working .. almost.

My colours are waaay off. In the ubuntu test page, the magenta is a muddy red, the green is very washed out, yellow is slightly orangey, cyan is very blue and the ubuntu logo orange comes out as a pink-like colour. Printing photos makes them look as though they have been put through a cheesy 'alien vision' style filter.

I've managed to get hold of a Windows box to test and the colours in a test page on there print fine so it is something to do with these drivers.

Does anyone have any clue to how to diagnose (or fix) this problem?

TIA


Update:

I've done some digging and managed to find a PPD file for the printer (part of the Mac driver). Things are now slightly different. The red is noticably better and the blue, green and cyan look about right. The Yellow is much more the right colour but looks like it has thin dark stripes running through it. The blacK circle is grey and the ubuntu logo has changed from pink to a greeny-yellow.

---

### Post by datajack on 2012-10-12
After spending hours playing with colour profiles I have realised I'm barking up the wrong tree and that there is something more fundamental awry.

I printed the colour wheel at [http://gardenerstips.co.uk/blog/tips/colourful-tips/](http://gardenerstips.co.uk/blog/tips/colourful-tips/). When printed it looks a complete mess, see attached file. When printing from Windows it looks fine.

Can anyone throw any light on this?

please?

---

### Post by datajack on 2012-10-14
I have got to the bottom of the problem, well nearly.

The problem exists in 12.04 but not in 11.10. I'm not sure exactly what change causes the issue, or even really how to diagnose it, but I'm happy I have a working printer now :)

---

### Post by phill on 2012-11-20
I've just bought this printer and I'm having bizarre colour issues as other have mentioned.  I've tried reverting to 11.10 ( cups 1.50-8 ) but it's still not solving it for me.

Datajack - which driver are you using (the Xerox 6015N?) and can you shed any more light on the way your system is set-up (AppSocket?) and does the test page work perfectly?

Many thanks!

---

### Post by datajack on 2012-11-20
> **phill said:**
> Datajack - which driver are you using (the Xerox 6015N?) and can you shed any more light on the way your system is set-up (AppSocket?) and does the test page work perfectly?


I didn't do anything special, just threw together a VM of 11.10 to see if it would work and it did.

I am using the Xerox drivers and am connecting to the printer via a socket. I have the printer configured with a static IP address and it has an entry in my local DNS. Here's my printers.conf, in case it will help ...


-----
# Printer configuration file for CUPS v1.5.0
# Written by cupsd
# DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING
<Printer DellLaser>
UUID urn:uuid:e1e806df-2b78-3ead-7e4a-dde4211f6238
Info Dell 1355cnw Color MFP
Location Office Room
MakeModel Xerox WorkCentre 6015N v1.0
DeviceURI socket://dell1355cnw.localnet
State Idle
StateTime 1352927411
Reason media-empty-warning
Reason toner-low-report
Type 4300
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
Attribute marker-colors \#00FFFF,#FF00FF,#FFFF00,#000000
Attribute marker-levels 69,74,72,8
Attribute marker-names Cyan Cartridge,Magenta Cartridge,Yellow Cartridge,Black Cartridge
Attribute marker-types toner,toner,toner,toner
Attribute marker-change-time 1352927410
</Printer>

----

A lot of the attributes are just status information about the printer so will be different on your system - I really need to get around replacing the black toner!

I'm running a 64bit system and installed all the 32bit compatibility libraries to make the Xerox driver work. Other than that I really didn't do anything special. Yes the test page works fine.

If you are really stuck I can give you a copy of the VM disk image. You'll have to be desperate though as it is 1.5GB and my upload rate is low to say the least.

---

### Post by phill on 2012-11-25
That's really helpful - thanks so much!

I did not think about a VM - for some reason I've had issues with putting the live CD onto a USB but the VM was so much easier!

Ran it, installed the 32bit xerox deb and printed all colours perfectly as expected.  This means worst case I can run that when I need to print in colour, however it has also given me a full list of debs installed (just dpkg -l) which I'm going to manually compare to the downgraded ones I have in 12.04 (and most printing related ones rolled back to 11.10).  When I find a what is the cause I'll post it here and to the bug on launchpad.

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/984424](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/984424)

---

### Post by GerryGG on 2012-12-01
I hope you can get your Dell working with the Xerox driver. But as far as I know this driver only partially works even on Xerox WorkCentre 6015 printers. On my 6015 printer the deb package works to get the 6015 printing (and the colors are fine), but the scanner doesn't work. Still I guess if you can get your Dell printing properly, even if it doesn't scan, that's better than what you had.

---

### Post by Arielxgbarton on 2013-01-29
DataJack, you said you had found the PPD file. 
I binned the mac disc a long time ago, can you email it to me

[email]Arielxgbarton@gmail.com[/email]

I would like to try to use it

---

### Post by Arielxgbarton on 2013-01-29
This probabaly is a stupid idea, but I am going to try Windows disc + Wine.

---

### Post by niendo on 2013-03-03
please try the latest version from [URL="http://foo2hbpl.rkkda.com/"]http://foo2hbpl.rkkda.com/
[/URL]it has support for the Xerox Workspace 6015 and the Dell 1355.

---

