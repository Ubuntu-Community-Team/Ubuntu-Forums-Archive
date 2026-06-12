---
title: "Satellite C655 S5212"
date: 2012-02-19
forum: General Help
---

### Post by dkz666 on 2012-02-19
I am coming to the community out of sheer desperation.
this is long, but i tried to include as much information as could be useful
I am a moderately experienced Ubuntu user, still working on the specifics of the grammar, but i love the OS and the Open Source, and the community, been with it for a few years.

Quick antedote that may help diagnose, i do not know: i got this Satellite C655-S5212 before the school year. Got home, put on Ubuntu, kick off Windows. Everything was going great for a really long time (this was 11.04 days).
About halfway into the first semester (October or so) i was upgrading to 11.10, yippee right? Went to sleep, and something had hung up in the upgrade. Tried to restart, well i am sure you all can guess that did not work. Formatted the thing, re-installed 11.04 from an external hard drive with a partition, and then went back through and upgraded to 11.10. Worked great until this January.
First my software sources went. Tried long and hard to diagnose and correct the problems, but overall functionality wasn't to affect. This changed as updates became necessary and the internet started acting up. Recently had time to back everything up from those few months since the crash, then formatted the system and re-installed 11.04.

Now things are really weird. I have noticed that the BIOS message does not display, though i am still able to get into the Computer's Settings/boot menu with the F[integer] keys. Startup takes ridiculously long, five minutes or so, and that is if i do not get a No Bootable Disk Error. When ubuntu manages to launch, occasionally i get an "Out of disk" error, and sometimes the Gnome simply wont load. When i do get on, the internet is not accessible via an ethernet cable (my only option).

Now this worked in 11.04 with enough restarting the network manager and ifconfig eth0 up. Not the case after the update. I attempted installing the compat-wireless driver, though i do not know if it worked, or if i am able to do that using a bootable hard drive as a Start-Up disk. Regardless, i still cannot access the internet.

I am trying to do so as to check to see if the BIOS can be updated or to see if i can update/upgrade and take care of some of these issues. I know that the community is flooded with "Ohh help me" threads but this problem has been months affecting me, and i need this computer to do school work on.

Just to start off, here is the output from "lspci -nm"

                                  zach@zachtop:~$ lspci -nn  
 00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)  
 00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)  
 00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)  
 00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)  
 00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)  
 00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)  
 00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)  
 00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)  
 00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 04)  
 00:1f.2 IDE interface [0101]: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller [8086:1c01] (rev 04)  
 00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)  
 00:1f.5 IDE interface [0101]: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller [8086:1c09] (rev 04)  
 01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1) 
 02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)  
 

 Thank you all in advance.

---

### Post by dkz666 on 2012-02-19
In addition, i have been checking many different threads over the past month or so and tried many things, seen many similar, but nothing at all has worked

---

### Post by HeroOfCanton on 2012-02-19
See if your BIOS has an upgrade available and try that. Does not sound OS related.

HDD may be going bad as well. About 3/5 times those odd here and there disk related errors start popping up I end up having to replace a drive eventually.

---

### Post by HeroOfCanton on 2012-02-19
According to this page:

[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/bulletinDetail.jsp?pf=true&soid=3199314](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/bulletinDetail.jsp?pf=true&soid=3199314)

Your BIOS upgrade would be this file:

[http://cdgenp01.csd.toshiba.com/content/support/downloads/sc2ev110.exe](http://cdgenp01.csd.toshiba.com/content/support/downloads/sc2ev110.exe)

I didn't see any instructions or anything. Tough little bugger to find info on!

Hope it helps. **Do BIOS flashing with great caution.** The ability to hose your entire system is very real.

---

### Post by wolfen69 on 2012-02-19
Sounds like hardware related issues. I had that exact laptop, and it ran perfectly for me with 11.10

---

### Post by dkz666 on 2012-02-19
was hoping to avoid going into the BIOS, but would the standard instructions do me right here?
Thank you for the quick response.

---

### Post by HeroOfCanton on 2012-02-19
> **dkz666 said:**
> was hoping to avoid going into the BIOS, but would the standard instructions do me right here?
Thank you for the quick response.

If there is a standard set of instructions for Toshiba it would probably be the correct way to go. I'm not personally very familiar with them. Only worked on a few for other people. Never owned one.

That said, a BIOS upgrade is *probably* not going to solve your problem. Like wolfen mentioned, it's more likely hardware. My guess would be the HDD or mother board. The HDD is probably the only real option for swapping as the MB is virtually impossible to replace in most laptops even for a highly experienced tech.

---

### Post by mörgæs on 2012-02-19
It sounds like a dying hard drive. 

As a last attempt you could try a reinstall of 11.10 where you do a manual partitioning. You can for example skip the first 20 GB - if you are lucky and the hard disk errors are only here, you now have a working computer.

---

### Post by wildmanne39 on 2012-02-20
Hi, you want to avoid updating the bios if at all possible, it is almost never needed and if something goes wrong it will kill your computer for good.

There is no fix for a bios update gone bad.
Thanks

---

### Post by wolfen69 on 2012-02-20
> **wildmanne39 said:**
> 
There is no fix for a bios update gone bad.
Thanks

Actually it *can* be fixed, but it would have to go back to the manufacturer and would be expensive.

---

