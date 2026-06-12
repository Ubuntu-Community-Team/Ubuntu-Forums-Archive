---
title: "Boot stops at &quot;elevator:&quot;"
date: 2005-02-06
forum: General Help
---

### Post by mouse on 2005-02-06
Hey everyone, I thought I'd check this forum to see if anyone has had, or seen, this problem. When booting the Live CD, a bunch of stuff scrolls by way too fast to read, but then booting stops at the line "elevator: using anticipatory as default io". I've search around for quite some time and, I should say that I am a bit embarrased that  I haven't found out anything that tells me what "elevator" or "anticipatory" are! What is happening at this point during boot up? It just stops! 

I have had trouble in the past booting any Debian based CD's. Typically, they all seem to stop quite early, I think when it is looking for scsi hardware. I've tried to have them not search for scsi hardware, and sometimes they will get past that point, but then my network card never works! I think I tried the no_probe option for scsi with Ubuntu too, but it stopped at the same "elevator:" point.

I've included what I think are the hardware devices on my PC:
VIA TECHNOLOGIES, INC. P4PB 400
2.40 gigahertz Intel Pentium 4
256 Megabytes Memory
RADEON 7500 SERIES [Display adapter]
Maxtor 6Y120L0 [Hard drive] (122.94 GB)
Western Digital WD102AA [Hard drive] (10.26 GB)
TEAC CD-W58E [CD-ROM drive]
Adaptec AHA-2940U/2940UW/2940D PCI SCSI Controller
SEAGATE DAT 06240-XXX SCSI Sequential Device [Tape drive]
VIA VT1616 6 channel AC’97 CODEC
VIA Rhine III Network Adapter

Thanks,
Joe

---

### Post by Buffalo Soldier on 2005-02-06
That's a lot of details for someone posting a thread for the first time :) which is good.

Now for your problem, this is the first time I've seen the error message "elevator: using anticipatory as default io". I think your guess is right it has something to do with SCSI, but I'm guessing it could be more specific to the Tape Drive. I did a search on Google on that 3 keyword **elevator anticipatory tape** and received a few sites discussing the error.

I'm sorry I couldn't be much of a help to you Joe. Maybe the others have better ideas how to solve this.

---

### Post by alastair on 2005-02-06
It might not be the "elevator" line that's the problem - but what comes after that. I will have to boot the CD myself and have a look. The "elevator" is the IO scheduler used i.e. how I/O tasks are managed/queued to your block devices (disks etc.). There are other elevators e.g. elevator=deadline.

For the SCSI - you might be able to use a "noscsi" option on boot. Other options worth trying at boot are "noapic" and "acpi=off".

---

### Post by mouse on 2005-02-10
Just thought I'd follow up on this thread. I decided to do a little more testing, which I probably should have done before I posted origionally.  I disconnected the Tape Drive from the SCSI card and the boot up stopped at the same point. I then removed the SCSI card and the Boot Up whizzed right past that spot. Everything appeard to be going well... up to... Starting Gnome Desktop... Starting CUPS.... and the screen went blank.... then everything stopped. I think the problem now is that I only have 256MB memory. Oh well. Funny the SCSI card doesn't seem to work. Maybe there is some setup on the card that would enable it to work? It worked, or at least appeared to work (I never used it, but the system booted up) with other flavors of Linux (Fedora, Suse).

---

