---
title: "Oracle VirtualBox questions"
date: 2010-10-07
forum: General Help
---

### Post by toxic9813 on 2010-10-07
Okay, I have some questions about Oracle's VirtualBox. Two is not very serious.

1.) What should my settings be? The OS's I use (the guest OS's) are Windows 7, Linux Mint, and soon to be, Solaris 10 (in download). The Host OS is Ubuntu 10.10 Maverick RC. I have only 1gb of RAM, and only 128mb of video memory onboard. Processor is a Pentium D (overclocked? this computer is secondhand) clocked at 4.1ghz. I've tried giving my OS's 512MB RAM with most video memory, and 700MB RAM with all video memory. Have not tried donating very little RAM to my guest OS's because I doubt they'll work well with less than 512mb.

2.) Do you think Oracle Solaris 10 will work well on Oracle VirtualBox?


P.S. Is Solaris 10 any good? never tried it. Any other recommendations on Linux distros?

---

### Post by SeijiSensei on 2010-10-07
You're going to have a hard time running more than one VM at a time in 1 GB of memory.  Linux will have to keep swapping making the VMs run extremely slowly.  The single best solution you could implement is to add memory. 3 GB is the maximum if the host is running 32-bit Ubuntu, lots more if it's a 64-bit machine.

---

### Post by toxic9813 on 2010-10-07
Huh. Well, I went to crucial back when this was runnin XP and it says I can get two 2gb chips for 80 smackers. Not bad, but I don't have any spare income. Food, water, electricity, and internet ;)

---

### Post by toxic9813 on 2010-10-07
Also, what settings can I put on to squeeze the best out of what I have?

---

### Post by DarthScape on 2010-10-07
Solaris is pointless, don't even bother. If anything, try OpenSolaris, but don't get hooked, they are discontinuing it. Anyway, I agree, you need more memory, period. There is no way you should even try to use all of those VM's at the same time. If your CPU supports VTx, make sure that it is turned on. Also, make sure that you have the guest additions install, helps a ton.

---

### Post by toxic9813 on 2010-10-07
Okay, 1)Not running them ALL at the SAME TIME, just one. I like trying new things without dual booting. 2)Solaris, meh, I'll look at it. 3)RAM sounds good. I will try 

4)How do I turn on VTx?

---

### Post by Locke_99GS on 2010-10-07
OpenSolaris is nice, if you're lucky enough to have it function on your hardware. The project isn't dead; the community project leaders forked it.
[http://www.illumos.org/](http://www.illumos.org/)
Also, ZFS+TimeSlider is incredible. I can't wait for similar functionality in Linux.

VTx would be enabled in your BIOS settings, if the processor supports it.

Give the VM just enough to run it without it swapping all the time.  If you only have 1g RAM on the host, I'd imagine host and guest should be happy enough with 512.

---

### Post by toxic9813 on 2010-10-07
Thanks! Good info.

---

### Post by Old_Grey_Wolf on 2010-10-07
> **toxic9813 said:**
> Okay, I have some questions about Oracle's VirtualBox.........

You need more RAM. The spec for Ubuntu is 1 GB of memory. Here are the specs, [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements).

---

### Post by Merthod on 2010-10-07
Check here:
[http://www.virtualbox.org/wiki/Guest_OSes]("http://www.virtualbox.org/wiki/Guest_OSes")

Depending on the use of the operating system and the operating system own requirements (i.e. Win7 eats up 1 GB at minimum) you may give the RAM. Also take into account that depending on your version and updating the own OS may take more disk space. So take into account at least 3-4 GB for the OS itself.

---

