---
title: "Slow USB transfer speed - any ideas at all?"
date: 2011-12-23
forum: General Help
---

### Post by hackb0y294 on 2011-12-23
Hi all,
I know this subject is all over the internet (so to speak), and I've read dozens of threads on UF, Launchpad bug reports, etc., but none seem to address the problem. In my case, one one PC I'm dual booting Windows 7 and Ubuntu 11.04; an 8GB USB flash drive seems to work fine in both Windows and Ubuntu, but my digital camera is appallingly slow on Ubuntu. In Windows, transfer speeds are around 12 - 15 MBps; in Ubuntu it's in the KBps range. I haven't done extensive testing with the flash drive, though it *seems *to work ok, but the camera is obviously slow.

On another PC, *everything* is slow; the same flash drive transfers in KBps. An external HDD is the same.

If there are no solutions, does anyone know if this bug will be addressed in 12.xx?

---

### Post by dino99 on 2011-12-23
speed depend on hardware: usb & stick, the slowest give the tempo; can depend on how the stick is formatted too.

---

### Post by bluexrider on 2011-12-23
> **dino99 said:**
> speed depend on hardware: usb & stick, the slowest give the tempo; can depend on how the stick is formatted too.
I find this problem a lot, (slow transfer speeds), using both thumbdrives and external HDD's. 
I can use the same hardware on the same PC but get faster transfer speeds with Windows.

It would be nice to have a real "fix" for the issue

---

### Post by mike555 on 2011-12-23
Some makers use USB 1.1 in front plugs while using USB 2 plugs in back .... maybe try a back plug?

---

### Post by hackb0y294 on 2011-12-23
> **bluexrider said:**
> I find this problem a lot, (slow transfer speeds), using both thumbdrives and external HDD's. 
I can use the same hardware on the same PC but get faster transfer speeds with Windows.

It would be nice to have a real "fix" for the issue

Same here. The same devices, same ports, same everything but the OS; Windows is faster by far in transfer speed.

---

### Post by philinux on 2011-12-23
> **hackb0y294 said:**
> Same here. The same devices, same ports, same everything but the OS; Windows is faster by far in transfer speed.

Yea. The big I've commented on shows it starts ok then slows to a crawl. Bug not fixed yet. Royal pain.

---

### Post by bluexrider on 2011-12-23
> **philinux said:**
> Yea. The big I've commented on shows it starts ok then slows to a crawl. Bug not fixed yet. Royal pain.
Is the bug a Ubuntu thing or does it effect other distros as well?

---

### Post by hackb0y294 on 2011-12-23
> **bluexrider said:**
> Is the bug a Ubuntu thing or does it effect other distros as well?

Apparently, it's been experienced in others; the Ubuntu variants, and I think most Debian based distros.

---

### Post by bluexrider on 2011-12-23
> **hackb0y294 said:**
> Apparently, it's been experienced in others; the Ubuntu variants, and I think most Debian based distros.
I wonder if the USB 3.0 has the same issues

---

### Post by nick3501 on 2012-01-15
i have noticed this on my dell inspiron laptop over the past few weeks. was it caused by an update?  It seems fine on external HD, but thumbdrives are slow.  Transfers start off fast (~12 mb/s) but dwindle down to ~2mb/s, and that is innacurate because it does 2mb/s in short bursts....with loong pauses in between. if i try to cancel a thumbdrive transfer, it takes at least 30 seconds to actually stop writing...and it needs just as long to finish once it gets to the last mb of data ("0 seconds left" on the clock, but it takes 30-45 to finish up)

---

### Post by donw35 on 2012-01-22
I am working transitioning my forensics machines from Win7 to Linux, starting with Ubuntu 10.11 and this has been my experience, slow USB HDD. I know its a Linux/Ubuntu issue as this machine dual boots between windows 7 and Ubuntu, windows is copies a 600MB file in less then 3 minutes, Ubuntu takes 30 minutes. same machine, same drive and same USB port. I am hoping for a fix for this as this is a deal breaker to move to Linux on these machines.

Thanks

---

### Post by donw35 on 2012-01-23
well, for what its worth, I re installed 10.04 LTS and the USB speed is fine, I will stay with LTS for my needs. hope this helps others.

---

