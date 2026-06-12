---
title: "Any good PCI-X devices?"
date: 2010-04-28
forum: General Help
---

### Post by Objekt on 2010-04-28
For various reasons, I ended up with a motherboard (listed in my sig) which sports a pair of PCI-X ports.  

I'm itching to use at least one of my PCI-X slots.  Seems a shame to have that nifty, fast slot & not use it.

Anyone know of devices which use a PCI-X slot AND will work in Ubuntu?

---

### Post by cascade9 on 2010-04-28
Wow, I clicked on this expecting the usual 'dont know the difference between PCI-e and PCI-x' but I was wrong. That board DOES have PCI-x! o.O 

Apart from some network cards, HDD interface and RAID cards...I dont know of anything. 

If you've got the money and like RAID, heres the card for you- 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16816116052](http://www.newegg.com/Product/Product.aspx?Item=N82E16816116052)

BTW, AFAIK, PCI-e is faster. Maybe not in x1 form (never checked) but x4 slots or higher would be faster than PCI-x.

---

### Post by Objekt on 2010-04-29
Yes, PCIe does blow away PCI-X in all but the 1x mode.  I think that's why PCI Express was invented.  PCI-X is really just two legacy PCI slots stuck together.  

The motherboard has turned out to be massive overkill, actually.  It has two of almost everything.  I only use the second SATA controller because that is what provides the eSATA ports.  I have no use for the second NIC, except [s]frustrating myself[/s] driving myself absolutely bonkers by trying to set up Internet connection sharing on it (thread here: [http://ubuntuforums.org/showthread.php?t=1459406]("http://ubuntuforums.org/showthread.php?t=1459406")).

I chose the P5E3 WS Pro because it was one of the few with an X38 chipset and DDR3 support at the time.  In retrospect, fast DDR2 would have been fine, and it was a waste of money to pay for all those extra devices.  Oh well, live and learn.

---

### Post by cascade9 on 2010-04-29
Sort of...PCI-X was meant to be a much faster PCI connection, used quite a lot on servers, etc. PCIe uses the 'narow but fast' idea, not PCI-x 'wdie but slow'. The motherboard manufacturers love PCI-e, its a lot less soldering, easier traces, and a much smaller slot to build around, but PCI-x is still very respectable IMO. 

Might have been a bit of a waste...but when you dicide that you want to upgrade it to 8/16GB in a few years time, DDR3 is going to be a lot cheaper *whistles "always look on the birght side of life'* :lolflag:

BTW, if you really want to use the 1st SATA controller for eSATA as well, then yuo can convert an internal port to an external port with a back panel (sata to esata).

---

### Post by Objekt on 2010-04-29
Shopping around, I notice that most PCI-X devices are server-oriented, meaning "expensive."  I guess there was a time when it made sense to connect a gigabit Ethernet NIC via a PCI-X expansion card, but...boy howdy, 500 bucks??

PCI-X kit seems similar to SCSI gear: expensive partly because of the parallel wiring, which is difficult to pull off, due to things like clock skew.  I think that's also the reason PCI-X is "slower but parallel."  "Very fast and parallel" is really hard to pull off.  I think the emergence of serialized technologies - PCIe, serial attached SCSI, SATA - is evidence of that.

I don't have a problem using my 2nd disk controller for eSATA, but I do wish Asus' eSATA implementation were more robust.  eSATA is supposed to support hot-plugging.  Mine doesn't.  I get dirty dismounts if I try, and Windows XP freaks out.  Having to shut down completely every time I want to connect or disconnect the external drive, eliminates most of the benefit fo having an external drive.

---

### Post by cascade9 on 2010-04-29
> **Objekt said:**
> Shopping around, I notice that most PCI-X devices are server-oriented, meaning "expensive."  I guess there was a time when it made sense to connect a gigabit Ethernet NIC via a PCI-X expansion card, but...boy howdy, 500 bucks??

PCI-X kit seems similar to SCSI gear: expensive partly because of the parallel wiring, which is difficult to pull off, due to things like clock skew.  I think that's also the reason PCI-X is "slower but parallel."  "Very fast and parallel" is really hard to pull off.  I think the emergence of serialized technologies - PCIe, serial attached SCSI, SATA - is evidence of that.

PCI-X is also 'expensive because its expensive' if you get my meaning. 

> **Objekt said:**
> I don't have a problem using my 2nd disk controller for eSATA, but I do wish Asus' eSATA implementation were more robust.  eSATA is supposed to support hot-plugging.  Mine doesn't.  I get dirty dismounts if I try, and Windows XP freaks out.  Having to shut down completely every time I want to connect or disconnect the external drive, eliminates most of the benefit fo having an external drive.

Ohh dear....seems its a marvel controller for the eSATA. :( 

I'd seriously consider a SATA->eSATA panel...marvel controllers are real junk (and the fact that it doesnt work well with XP I offer as 'proof' that its not just a linux driver issue).  

Really, I wish that either marvel would lift theier game, or manufacturers would stop putting the useless ^#%^# chips they make onto motehrboards. It really brings down what should otherwise be top quaillity products a few notches IMO, and thats a real pity. Being caused by a single part that the manufacturer is probably only saving a few cents (50c US max IMO) per unit on compared to a better quality product is more than fustrating......

---

### Post by Objekt on 2010-04-30
> **cascade9 said:**
> Ohh dear....seems its a marvel controller for the eSATA. :( 

You almost caused coffee through the nose there! :)

Bonus points for guessing the disk controller brand without looking it up!  You're absolutely right, the secondary disk controller is a Marvell 6100-series.

> **cascade9 said:**
> I'd seriously consider a SATA->eSATA panel...marvel controllers are real junk (and the fact that it doesnt work well with XP I offer as 'proof' that its not just a linux driver issue).  

I happen to have an extra SATA->eSATA panel, and spare SATA ports on the primary disk controller (Intel ICH9R).  It does seem worth a try.  We'll see whether the Intel controller properly supports eSATA.

As you say, it's only Windows XP that freaks out if I try to hot-plug (haven't tried Windows 7 yet).  Ubuntu doesn't skip a beat, although I can't mount the drive until after a reboot.  Ubuntu can't see the drive, but it doesn't lock up temporarily or send garbage noise through the speakers.  The "scream of pain" I get with a Windows XP hotplug is rather curious, since I am not even using the motherboard sound device, but rather the PCI SoundBlaster.  Must be some kind of electrical shenanigans going on.

Not *all* PCI-X gear is expensive.  I did find quite a few PCI-X expansion cards in the $30-$50 range.  None of them are terribly useful, however.  I don't really need an old-fashioned parallel port.

Even Newegg can't keep PCI-X vs. PCI Express straight.  Searching for PCI-X devices, I got several items that are actually meant for PCI Express slots.

---

### Post by cascade9 on 2010-05-01
> **Objekt said:**
> You almost caused coffee through the nose there! :)

Bonus points for guessing the disk controller brand without looking it up!  You're absolutely right, the secondary disk controller is a Marvell 6100-series.

Opps, sorry ;) 

Well, I guessed it was marvel, but I have to admit I did check that before posting. 5 second job to do so, I figure that its always best to do that. ;) 


> **Objekt said:**
> I happen to have an extra SATA->eSATA panel, and spare SATA ports on the primary disk controller (Intel ICH9R).  It does seem worth a try.  We'll see whether the Intel controller properly supports eSATA.

Pretty sure that it should work well, good luck :) 

> **Objekt said:**
> 
As you say, it's only Windows XP that freaks out if I try to hot-plug (haven't tried Windows 7 yet).  Ubuntu doesn't skip a beat, although I can't mount the drive until after a reboot.  Ubuntu can't see the drive, but it doesn't lock up temporarily or send garbage noise through the speakers.  The "scream of pain" I get with a Windows XP hotplug is rather curious, since I am not even using the motherboard sound device, but rather the PCI SoundBlaster.  Must be some kind of electrical shenanigans going on.

'Scream of pain'? o.O Sounds like EMI/RFI (electromagnetic/radio frequency interference) :( . Theres a few tricks you can try to check that, mostly involving foil (or better yet copper mesh, but you dont find that in the average house). 

ANOTHER thing to add to my list of 'reasons why marvel sucketh most profound'.  

> **Objekt said:**
> 
Not *all* PCI-X gear is expensive.  I did find quite a few PCI-X expansion cards in the $30-$50 range.  None of them are terribly useful, however.  I don't really need an old-fashioned parallel port.

True, its not *all* expensive, but most of it is. 

> **Objekt said:**
> 
Even Newegg can't keep PCI-X vs. PCI Express straight.  Searching for PCI-X devices, I got several items that are actually meant for PCI Express slots.

I've noticed that newegg searches can throw out really odd results. I'm glad its not just me.

---

### Post by Objekt on 2010-05-01
I got the SATA->eSATA bracket installed yesterday.  Unfortunately, the ICH9R is no more hot-pluggable than the Marvell abomination.  The external HDD doesn't show up after being plugged in until I reboot.  

Part of the problem may be the lack of proper and explicit mounting/unmounting tools.  In Windows XP, I have no way to "eject" the external drive.  XP sees it as just another internal HDD, so I can't right-click and "stop" it as one can do with, say, a USB storage device.

Haven't tried it under Ubuntu.

Attempting to hotplug with the eSATA bracket/ICH9R no longer causes the system to lock up for a couple of minutes, and there are no audio artifacts.  I guess that's something.

---

### Post by cascade9 on 2010-05-01
Well, it was worth a try. :| 

I really should reconnect my winXP drive and have a play with it- I'm 99.99% sure I have managed to unmount an (internal!) SATA drive under XP. Not the OS drive, that was PATA, but a data/storage drive. Maybe I can remember how I did that. :S

---

### Post by Objekt on 2010-05-07
On the topic of mounting/unmounting drives in Windows XP, here's an article by Microsoft: [The DevCon command-line utility functions as an alternative to Device Manager]("http://support.microsoft.com/kb/311272")

You can also go to the Storage plugin of Computer Management under Control Panel->Administrative Tools, and "remove" drives there.

The terminology gets a bit confused.  If you run a file system check (chkdsk) in Windows, it will say something about "unmounting" the drive before checking it.  That is familiar to Linux/Unix users.  However, both devcon and the Storage plugin refer to it as "removing" a drive.

Windows usually mounts anything connected automagically, so I don't think you would have to run a command to do that.  

I'll have to experiment with this later.  I don't often need to disconnect & move my external HDD while using the computer, but it sure would be nice to have the ability.  Without some way to unmount properly, I will always get a "dirty" unmount, resulting in Linux systems (like Clonezilla) being unable to mount the partition until I can run chkdsk.

A Linux equivalent of Windows' chkdsk would be very useful for us dual-boot types.  I don't know whether the Linux dev community is just not interested, or whether it's a technical hurdle that keeps such a thing from existing.

---

