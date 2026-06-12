---
title: "error I/O scanner diagnosis steps ?"
date: 2010-10-25
forum: General Help
---

### Post by AgentZ86 on 2010-10-25
Hi

I need help diagnosing my system

[LIST]
[*]Ubuntu 9.10 Karmic Koala 64 bit
[*]Dual Core AMD 64
[*]USB scanner with xsane etc.
[/LIST]

The subject is that I don't know how to tell why (ALL) scanners have developed this problem on my system ( have many known working scanners to choose from to diagnose this topic) for now I'm using the hp 5590 scanjet

Scanners are detected and scan but never complete.They look like they are timing out or something.

The Xsane progress bar starts and scans, but then the typical error I/O message pops up then the scanner is no longer detected until I turn if off then restart it and then it's detected again. On occasion it will scan a page, but not more then one.
But mostly it just duplicates the problem over and over again every time I restart the scanner.

So it appears this must have occurred after an update of some sort. I cannot be sure which because I don't scan that often.

Anyhow, I need some help with command that might help diagnose this problem

Please advise any help is appreciated otherwise I'm going to have to re-install because I know this was all working before.

Thanks

---

### Post by sikander3786 on 2010-10-25
Support for 9.10 is near to end so consider a fresh instal of 10.04 or 10.10 if you can backup all your data. But before that, make sure to test all your hardware from the Live CD so you get no problems afterwards.

Regarding the original problem, first of all I'll recommend to check the printer data cable if it is broken or damaged at some point. Better if you can check with some other cable.

You can also try purging hplip and reinstalling it from Synaptic. But first of all check the data cable. I strongly suspect it as a hardware issue.

I believe it is a USB scanner. Also worthy to check your USB ports. Do they work fine with other devices?

---

### Post by AgentZ86 on 2010-10-25
> **sikander3786 said:**
> Support for 9.10 is near to end so consider a fresh instal of 10.04 or 10.10 if you can backup all your data. But before that, make sure to test all your hardware from the Live CD so you get no problems afterwards.

Regarding the original problem, first of all I'll recommend to check the printer data cable if it is broken or damaged at some point. Better if you can check with some other cable.

You can also try purging hplip and reinstalling it from Synaptic. But first of all check the data cable. I strongly suspect it as a hardware issue.

I believe it is a USB scanner. Also worthy to check your USB ports. Do they work fine with other devices?

Thanks for the response

I have 5 other computers running and all the scanners test perfectly on the 9.10 32 bit machines.

The 64 bit machine was working fine also but then NO scanners can work on it all of the sudden.
I tested the scanner in question on another machine and it works perfect.
And I use the usb ports regularly with other hardware so I believe the hardware is OK.

I would love to be able to learn to diagnose this problem for knowledge and also future use. I hate to just re-install every time something goes wrong.

I can install the latest ubuntu, but was hoping to avoid that right now.

how do you purge hplip ? Just uninstall it or can I just select Reinstall from Synaptic ?

Please advise
Thanks

P.S 
The only other things I have different on this machine is that I'm running the xbox360 drv or I think it's called xboxdrv and all the associated installs to go with it.

But the scanner was working fine with that installed for a long time up until recently.

---

### Post by sikander3786 on 2010-10-25
> how do you purge hplip ? Just uninstall it or can I just select Reinstall from Synaptic ?

Search for hplip, right click and Mark for complete removal from Synaptic. Then reinstall.

---

### Post by AgentZ86 on 2010-10-25
> **sikander3786 said:**
> Search for hplip, right click and Mark for complete removal from Synaptic. Then reinstall.

Thanks for the advise

I tried this, and same effect.

I ran xsane from command prompt to watch the output and get this on the command line:

[hp5590] hp5590_bulk_read: USB-in-USB: incomplete bulk read (requested 65536 bytes, got 13824 bytes)

then this:
[hp5590] hp5590_get_ack: USB-in-USB: error getting acknowledge

And then the annoying error pops up about (error during read: error during device I/O)

I'll see if I can find out what this means.

---

