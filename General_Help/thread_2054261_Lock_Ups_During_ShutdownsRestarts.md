---
title: "Lock Ups During Shutdowns/Restarts"
date: 2012-09-06
forum: General Help
---

### Post by uRock on 2012-09-06
I am having problems on two of my machines with them locking up during shutdowns and restarts, which force me to do a hard power off. One system is running 11.10 and the other is running 12.04. Both are 64 bit CPUs with 64 bit ubuntu. The following output is from the 12.04 machine,```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Caicos [Radeon HD 6450]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Caicos HDMI Audio [Radeon HD 6400 Series]
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57788 Gigabit Ethernet PCIe (rev 01)
```Please help me with this issue.

---

### Post by Epodx64 on 2012-09-07
Just wondering how this works hit ctrl+alt+f1 login to the console and type
sudo shutdown -h now

and see if that locks it up.

or sudo shutdown -r now
to reboot

---

### Post by uRock on 2012-09-07
**sudo halt** caused a lock, while the two **shutdown** commands worked fine. 

This problem is usually intermittent. It only happens once every few attempts.

---

### Post by Epodx64 on 2012-09-07
I'm just wondering are you using a Nvidia card? I had a very similar problem when I was using a Geforce 6150se Nforce 430 when I updated the driver to 304 from x-swat it cleared up most of the problems I was having with the regressed IMO Nvidia 29x drivers.

---

### Post by uRock on 2012-09-07
> **Epodx64 said:**
> I'm just wondering are you using a Nvidia card? I had a very similar problem when I was using a Geforce 6150se Nforce 430 when I updated the driver to 304 from x-swat it cleared up most of the problems I was having with the regressed IMO Nvidia 29x drivers.

I have a Radeon HD 6450 card. Both systems having problems have ATI cards.

I have tried the advice here, [http://askubuntu.com/questions/132143/stuck-on-reboot-and-shutdown](http://askubuntu.com/questions/132143/stuck-on-reboot-and-shutdown) which failed.

---

### Post by Epodx64 on 2012-09-07
hmm I know the x-swat has the latest drivers for ATI cards as well might be worth a shot to upgrade those to there latest drivers. 

here

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

It worked great when I was using a Geforce card I don't know about ATI but it's worth a shot oh and install ppa-purge to just in case it really messes up your system you can purge it and revert back to what you have now.

---

### Post by uRock on 2012-09-08
> **Epodx64 said:**
> hmm I know the x-swat has the latest drivers for ATI cards as well might be worth a shot to upgrade those to there latest drivers. 

here

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

It worked great when I was using a Geforce card I don't know about ATI but it's worth a shot oh and install ppa-purge to just in case it really messes up your system you can purge it and revert back to what you have now.

Thanks for the advice. Are the drivers offered in this PPA newer than the ubuntu repo versions. I really want to be able to put this behind me and get my ubuntu running right without having to do hard shutdowns.

Cheers and Blue Moons,
uRock™

---

### Post by uRock on 2012-09-08
I installed the repo. It upgraded a xorg package, but the problem is still there.

I installed the latest driver from ATI.com. Hopefully this fixes the problem.

---

### Post by uRock on 2012-09-08
Will mark as solved once I hit a decent number of restarts without any issues.

Number of problem free restarts/shutdowns: 13

I am pleased to say the problem has not recurred.

---

