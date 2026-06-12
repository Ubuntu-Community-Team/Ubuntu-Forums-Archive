---
title: "Linux hates my computer - Won't install or installs very slowly"
date: 2006-05-18
forum: General Help
---

### Post by archer75 on 2006-05-18
I tried to install two distros recently. SuSE and Ubuntu. The problem is with both the install takes forever and when it's done linux runs very very slowly.

SuSE 10.1 DVD took about 5 hours to install. And the OS is very slow.

Ubuntu 5.10 will install only when I unplug one of my USB hubs. The install still takes 1+ hours and the OS, once loaded, runs very slowly as well. 

Ubuntu 6.06 beta 2 takes forever to install as well and when it's done I boot to a prompt and type startx and it tells me something about X11 no such directory. 

To boot into the OS it takes about 7 minutes after the BIOS splash screen. Windows takes about 45 seconds. 

System Specs:

P4 3.4ghz Prescott
2x512gb PC3200
2x1gb PC3200
Asus P4C800-E Deluxe
Geforce BFG 6800GT
Soundblaster X-Fi
Sony DVD +/- burner
NEC DVD +/- burner
2x160gb Seagate 7200rpm, SATA2, NCQ
74gb WD Raptor SATA

Windows XP is installed on the raptor drive which is connected to an onboard Intel controller. I'm installing linux onto a seagate drive on that same controller.
My 2nd seagate drive is on the onboard TX2 promise controller and is just used for storage.

I have tried installs with both distros with both of my USB hubs unplugged. No change in speed. 
I have disabled the onboard promise controller and set the Intel controller to compatibility mode. No change in speed either. 

I have also tried 3 different optical drives.

Distros still install very slowly and once installed, run very slowly. I have posted this same info on several forums and still cannot find a solution.

---

### Post by rcarring on 2006-05-19
If you are installing directly onto your hard disk, it has to format the partition, it also has to write to the partition and later on read/write to the partition you chose to install Linux on.

Try vmplayer with the breezy browser appliance, give the spec of your system it should run like a rocket.

---

### Post by archer75 on 2006-05-19
[QUOTE=rcarring]If you are installing directly onto your hard disk, it has to format the partition, it also has to write to the partition and later on read/write to the partition you chose to install Linux on.[/QUOTE]

Yes, of course. It's doing that. That isn't the issue. I'm installing onto another hard drive. I'm giving it the entire thing. An install should not take that long. And on other slower computers I have done it on things went just fine. But a 5 hour install for SuSE is quite long. It should have been 20 minutes max. Same with Ubuntu. 

I'm not using any Live CD's. I have in the past and they take about 20 minutes to boot up. I'm not using those now. 

[QUOTE=rcarring]
Try vmplayer with the breezy browser appliance, give the spec of your system it should run like a rocket.[/QUOTE]

Vmplayer? breezy browser appliance? I'm not using VMware here. I'm just doing a straight install onto a hard drive.

---

### Post by archer75 on 2006-05-19
up

---

