---
title: "making ubuntu look like an external USB drive"
date: 2010-02-14
forum: General Help
---

### Post by mstephens on 2010-02-14
Slightly unusual but what I'm looking for is something which can make a linux file system appear as an external USB drive to another device e.g. a media player which expects to find an external drive (which might need to be FAT32 )

I've previously set up my somewhat underpowered Ubuntu box as a NAS and also had it connected to the TV to play video files. A cheap media player would offload video processing and also allow sort out remote control and UI issues.

---

### Post by Chronon on 2010-02-14
> A cheap media player would offload video processing and also allow sort out remote control and UI issues.

I'm not clear on what you're trying to do here.  Are you intending to use the media player to process video files stored on a UMS formatted with a file system that Linux recognizes or what?

If the media player will act as USB host then it must contain file system drivers for accessing the UMS device.

---

### Post by mstephens on 2010-02-14
I want to be able to plug a media player (i.e. a hardware device not software) into a linux system via USB and the media player to think it has been plugged into an external USB drive.

Firstly, the USB connections would need sorting as both ends think they are the host but I've seen "crossover" cables which should sort that bit out.

Secondly, the linux system would need to provide something which looks to the media player like an external drive formatted in whatever way the player expects (which for many seems to be FAT32) but is actually a normal directory containing media files. The media player would only need to be able to read the files.

A simplified concept would be a straight FAT32 partition on a hard disk in a linux box which was also accessible to a media player via a USB connector on the linux box. So basically both the linux box and the media player would see a file system they could read (and linux could write to )

Even simpler would be an actual external drive with a USB lead which split to allow 2 devices to connect to it simultaneously.


I'm not really bothered about the finer details of how its implemented, just whether anything already exists along these lines.

---

### Post by Chronon on 2010-02-15
With USB one agent must act as the host and other agents can connect as devices.  It isn't possible for two agents (pieces of hardware) to both be host simultaneously.  It is possible for them to dynamically exchange roles (as I believe this is what USBOTG is all about).

I am fairly certain that it would take some pretty interesting gymnastics to allow access of a given UMS device to two different devices that both wish to act as hosts since only one of them can act as host at a time and they have to take turns mounting the file system, synchronizing disk operations, etc.  Perhaps there's a way with MTP (or another protocol), which does not expose an actual file system to the host.

I can only say that I'm not aware of anything like what you are asking about.

---

### Post by coldraven on 2010-02-15
Just buy an external HDD! They are cheap enough these days.
I did some research then bought a 1TB Samsung Story for £80 in the UK.
The one handy feature is a radio style on/off switch on the front panel which also dims the LED light.
It came as FAT32 but I formatted it to NTFS so that I can store DVD ISO files (over 4GB in size). It can also be used by any windoze boxes that you may have.
I use VLC to play the movies from disk.
I don't have a TV, after I found myself shouting at the stupid adverts I thought it was better to give it away!  Sanity restored................:D

---

### Post by gmargo on 2010-02-15
That's an interesting idea.  There's some info on Wikipedia about "USB On-The-Go" which sounds similar [http://en.wikipedia.org/wiki/USB_On-The-Go](http://en.wikipedia.org/wiki/USB_On-The-Go)

---

### Post by mstephens on 2010-02-16
> **coldraven said:**
> Just buy an external HDD! They are cheap enough these days.
I did some research then bought a 1TB Samsung Story for £80 in the UK.
The one handy feature is a radio style on/off switch on the front panel which also dims the LED light.
It came as FAT32 but I formatted it to NTFS so that I can store DVD ISO files (over 4GB in size). It can also be used by any windoze boxes that you may have.
I use VLC to play the movies from disk.
I don't have a TV, after I found myself shouting at the stupid adverts I thought it was better to give it away!  Sanity restored................:D

Not really relevant. I'm looking at integrating systems not something which requires to be manually unplugged from one device and then connected to the other.

---

### Post by mstephens on 2010-02-17
To answer my own question.

Yes it's do-able but the problem seems to be the cost.

There are chips like the NET2280 which are designed for  USB device (as opposed to USB host ) which are reasonably priced until you want them on a PCI card at which point the price increases dramatically because you are essentially buying a full development kit. 

There is linux software about -see kernel/drivers/usb/gadget.

I don't think it would work with an A-A bridging cable (which have something like the NET2280 in the middle) because there needs to be a B end actually on the PC in order to implement the UMS.

---

### Post by mstephens on 2010-05-20
For anyone still interested in this, I recently bought an Iomega ScreenPlay Pro HD box which is a NAS device primarily designed for outputting video onto a TV screen controlled by an IR remote.
The OS is Linux (albeit not Ubuntu) and as well as ethernet connectivity, the box can function as either end of a USB connection i.e. it can connect to a PC as an external HDD and it can host other external HDDs. Similarly the LAN connectivity incorporates a samba server to allow the box to act as a NAS device and also a samba client so it can mount drives which are on other servers (linux/windows).
Boot time is around 20 seconds. Neat bit of kit which hasn't really taken off in the consumer world because the UI is not exactly brilliant. Ideal for anyone who wants to mess about though and you can pick them up for slightly more than the cost of a standard external drive.

---

