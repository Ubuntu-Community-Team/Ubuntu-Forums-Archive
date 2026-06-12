---
title: "computer freezes randomly and video flashes"
date: 2011-10-16
forum: General Help
---

### Post by slixz85 on 2011-10-16
hi i am running lubuntu on a dell optiplex gx260 pc. i am having an issue where my video will flash randomly about every few hours and the computer is running pretty slow. the disk reads healthy from disk utility and so does the memory from memory test. could there be another video driver i need to be using or something like that. i know in windows it will freeze up with driver problems about like this is doing now.


thanks to any help. i dont know alot of terminal commmands but here are some specs.




lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:09.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)

---

### Post by coldraven on 2011-10-16
I'm no expert but could it be the motherboard?
I know that some Optiplex models had some hardware issues.
See "Capacitor Issues" section here:
[http://en.wikipedia.org/wiki/Dell_OptiPlex](http://en.wikipedia.org/wiki/Dell_OptiPlex)

---

### Post by slixz85 on 2011-10-16
thanks for tip, i keep it in mind just hoping i can find another issue.

---

### Post by slixz85 on 2011-10-17
apparently alot of people have had this problem with linux video drivers on the dell optiplex gx260 [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/566324](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/566324) alot of people talking about no fixes and just trying stuff. i am lost. but good thing to know it most likely aint my mobo. i am too worried about trying alot of video drivers right now until i can install another operating system on this hard drive in case of video crashes. i dont know enough to fix linux when it drops to the black screen lol.

---

### Post by coldraven on 2011-10-17
A company that I work for had hundreds of those Optiplexs and I have to say I thought they were rubbish! They ran Windows XP, even a simple thing like opening a jpg email attachment took about 10 mins. The company replaced them all.......with Dells! WTF!

---

### Post by slixz85 on 2011-10-20
i am still stuck with this problem. i have installed knoppix to this drive alongside  lubuntu and bodhi, bodhi runs decent but same issue. knoppix actually runs a bit better somehow having compiz and all that stuff but it is still very glitchy and choppy as well.

any more help appreciated. thanks

---

