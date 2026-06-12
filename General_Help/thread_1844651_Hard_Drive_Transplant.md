---
title: "Hard Drive Transplant"
date: 2011-09-15
forum: General Help
---

### Post by carl97 on 2011-09-15
Hmmm  Very Strange...
Is it unusual for a Hard Drive with Ubuntu 10.04 fully updated with EHCP, Zend Frame-work and all my 32 Domains to be simply taken out of one machine (Master Hard Drive) and placed in a totally different machine and to work Perfectly ? (For over 4 months now)

Totally different spec. Systems,

1st (Was installed on this System)
Xeon Dual core X 2 32 Bit CPU's, 4Gb Ram on Dell Precision 640, Gforce fx 550 (Or simular ?)

2nd (ist has been running flawless for 4 months in this System)
Intel Pentium 4, 3.0Ghz 1.5Gb Ram on Gigabyte Mobo and Radeon X800 GTX and XiFi Fatality Sound card. Also sata drives and various other peripherals and Wireless all working.

Is this just a fluke or is Ubuntu 10.04 Transferable like this ?
Carl

---

### Post by sanderd17 on 2011-09-15
If Ubuntu needs machine specific fixes, it won't be transferable as that, but if both machines work very good with Ubuntu, it is transferable.

---

### Post by carl97 on 2011-09-15
> **sanderd17 said:**
> If Ubuntu needs machine specific fixes, it won't be transferable as that, but if both machines work very good with Ubuntu, it is transferable.

Forgot to mention that i did swap them over so both worked in either machine.
I Havent had to do any fixes yet but done plenty of updates.

Its great even if it was temporary as i can then clone the drive and run on the other computer while i do Upgrade on my Hosting sites etc. (Experiments and that sort of thing)

:-)

---

### Post by FormatSeize on 2011-09-15
> **carl97 said:**
> Is this just a fluke or is Ubuntu 10.04 Transferable like this ?
Carl
It's not a fluke, nor is it Ubuntu 10.04. I'm unsure why this is so alarming.
Karl

---

### Post by armandh on 2011-09-15
Its not windows

obviously such a thing in a paid for OS would not be good for the bottom line

but Linux rebuilds the hardware profile with every boot
so it can be hardware agnostic given enough drivers

---

### Post by lancest on 2011-09-16
As said - NOT A FLUKE. A Linux drive can be moved around to pretty much any machine with no installation necessary.  A magical system.

---

### Post by kimda on 2011-09-16
Its because the kernel modules are loaded on demand. With new hardware different modules are loaded. If you would compile your own kernel with no modules it would fail. Try doing that with Windows ;-)

---

### Post by stalkingwolf on 2011-09-16
I keep a HDD with my system loaded on it for "rescue work."  I have yet to have it not work.

---

### Post by Ms_Angel_D on 2011-09-17
This doesn't appear to fit into the testimonial and experiences category so I moved it to general help.

---

### Post by tgalati4 on 2011-09-18
sudo cp /dev/sda /dev/sdb

Gives you a pretty good clone of a disk drive, assuming that disk sda is smaller than sdb.

You can reclaim the extra space on sdb (assuming it's much bigger) by using gparted.

I had a dual-boot (winXP Pro SP3 and Jaunty) and went from an 80GB drive to a 320GB drive.  Slapped in the new drive, reclaimed the extra space and it's been running fine for 2 years.

So, it's something we expect from our operating system.

---

