---
title: "Ubuntu 10.04 keeps on freezing, but mouse works"
date: 2010-07-06
forum: General Help
---

### Post by clementeb on 2010-07-06
Hello,

I have recently installed Uberstudent Cicero 1 (a very cool variant of Ubuntu 10.04) on a computer. Unfortunately the computer often freezes, but most of these times the mouse cursor can still be moved.
I don't know if it is because of the specific Ubuntu variant or because of the computer I am using (which was recently moved from one house to another). I have also been trying to install TexLive over the internet, but it got stuck various times:( so something might have gone wrong somewhere else as well. 
How can I check if it is a OS, a hardware or a software problem?
What tests should I run? With what software?
All the best

---

### Post by mikewhatever on 2010-07-06
Start by posting your hardware specs, CPU, graphics card model, RAM.

---

### Post by clementeb on 2010-07-07
Sorry for forgetting.
I actually have a 1800GHz Sempron, cpu and 1GB ram plus a 80 GB HD.
I realised that perhaps it was due to the missing swap (I thought 1GB Ram should have been enough). I have been trying to change partitions but I am having some trouble. The fact is that I have a dual booting system, with Windows 7 (that by default uses two main partitions), Ubuntu, and now the swap, but I can no longer use the common storage area since I can at maximum have 4 primary partitions (before I had 2 for windos, 1 ubuntu, 1 storage).
How can I fix this problem in order to see if the cause was really the swap?
And how do I check if the direvers or the cpu or the ram are having problem?
Cheers

---

### Post by warfacegod on 2010-07-07
Using an Extended partition scheme is going to get you around the 4 Primary limit.

This sounds like a video driver issue to me. I had the nVidia 185 driver doing the same thing to me. I switched to the 173 driver and it hasn't done it since.

What is your video card?

```
sudo lspci
```

---

### Post by clementeb on 2010-07-07
If I run that command I get
> 00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
00:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
root@grha-PC:/home/grha# 


Which one exactly is it?

---

### Post by warfacegod on 2010-07-07
> 01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

This one and it's a problem. SIS drivers aren't well supported at best. You'll probably need to go hunting for a better driver for it if one exists.

If you have a friend that will lend you a video card then do so and try that to see if the problem continues. If it does then you know it's not the SIS driver but somewhere else in your system.

---

### Post by clementeb on 2010-07-07
Thanks, I will try with the drivers and with another video card.
Cheers

---

### Post by warfacegod on 2010-07-07
Just ran across this: [http://ubuntuforums.org/showthread.php?t=958967](http://ubuntuforums.org/showthread.php?t=958967)

---

### Post by clementeb on 2010-07-11
Thanks for the link.
Unfurtunately it basically says there is no hope :(
And at the moment I dont have a friend to lend me a graphic card. 
The dual boot Windows 7 does not have problems, which reinforces the thesis that it's all due to the drivers :(

---

