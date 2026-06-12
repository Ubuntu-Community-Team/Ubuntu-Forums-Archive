---
title: "New HDD Not Recognized During Install"
date: 2010-07-10
forum: General Help
---

### Post by ProgenitorVirus on 2010-07-10
Hi there,

I just built a new PC, and was hoping to install Ubuntu on it.  However, my hard drive is not being recognized by gParted or the installer.  I think this may be due to the fact that my drive is SATA 3 and there is no support for it.  Any help at all is appreciated, the specs I think are important are below, tell me if you need to know anything else

CPU: Intel i7
Harddrive:  Western Digital 1 TB SATA 3 Black Edn.
Motherboard:  ASUS Rampage III Extreme

---

### Post by Ozymandias_117 on 2010-07-10
> **ProgenitorVirus said:**
> Hi there,

I just built a new PC, and was hoping to install Ubuntu on it.  However, my hard drive is not being recognized by gParted or the installer.  I think this may be due to the fact that my drive is SATA 3 and there is no support for it.  Any help at all is appreciated, the specs I think are important are below, tell me if you need to know anything else

CPU: Intel i7
Harddrive:  Western Digital 1 TB SATA 3 Black Edn.
Motherboard:  ASUS Rampage III Extreme

I would be surprised if SATA 3 wasn't supported... But to test that, you should be able to go into your BIOS and tell it to make SATA to emulate IDE (There will be something about SATA operation, you should have options of AHCI, IDE, and possibly RAID - set it to IDE). If SATA 3 is the problem, that would allow you to bypass it.

---

### Post by ProgenitorVirus on 2010-07-10
Hmm, I'll try that right now, but my drive is recognized as an IDE drive already :S

Maybe I'll try to set it to AHCI?  I'll go snooping around, but like I said, the drive is showing as an IDE drive now

---

### Post by ProgenitorVirus on 2010-07-10
Tried to, do that, it was recognized but Windows didn't much care for booting any more *Attempting a Dual Boot scenario*

---

### Post by cascade9 on 2010-07-10
> **ProgenitorVirus said:**
> Hmm, I'll try that right now, but my drive is recognized as an IDE drive already :S

Maybe I'll try to set it to AHCI?  I'll go snooping around, but like I said, the drive is showing as an IDE drive now

That could be the problem...if you were using IDE mode, that could well screw up SATA III support. 

There is a jumper to limit the drive to SATA II that might work. See the pic at the bottom of this page (pins 5-6 limits PHY to 3Gbps)  

[http://www.computerlimbo.com/home/tag/wd1002faex/](http://www.computerlimbo.com/home/tag/wd1002faex/)

---

