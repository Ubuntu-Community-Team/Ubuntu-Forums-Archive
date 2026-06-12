---
title: "Ubuntu 10.04 - Hang on Boot"
date: 2010-05-16
forum: General Help
---

### Post by Atavaka on 2010-05-16
I'm at my wits end trying to get 10.04 to work on my laptop. It's an Inspiron 710m and I can provide any details that might aid in resolving my problem. 

I'm going to include all the details of my escapades to get this to work from the beginning:

I downloaded the live CD for 10.04 and loaded it in to my laptop. It would consistently get to the splash screen with the five dots, cycle through them, kick to a black screen and just hang. The CD drive would cease spinning and the disc would cease being accessed. 

I couldn't find a way to get more information out of this, so I installed 8.04 LTS (had the install laying around) and opted to just do a network update to install it. The install went off without a hitch, I reboot, boom- splash screen appears, moments later I'm kicked to a black screen, system hangs indefinitely. I selected the recovery option in GRUB and (once) made it to the command line. I logged in, attempted to start X, boom- hang at a black screen. So. I -think- this has something to do with xorg.

Now, I tried to reboot back in to the recovery section again, it gets to a certain point then the screen flashes green and starts rapid firing line after line of something faster than I could read (it has something to do with X, I made out that much) and now it hangs right after it complains at me that I need to update the firmware on my wireless card, etc. Occassionally it gets past that, but I've not been able to reach the command line login again. I can hit CTRL+ALT+DEL and it brings up the options similar to what you get when using an Alternate Install disc, but after 2 seconds it hard-reboots back to the BIOS. 

Can anyone -please- give me some advice on how I might get past this, or kindly tell me to give up on it? I've been hammering at this all day and I've about decided to just go with 9.10 instead. I had been using OpenSuSE but I don't like it quite as much as I do Ubuntu. This fiasco has been making me rethink that, though.

---

### Post by utnubuuser on 2010-05-16
You might want to google: nomodeset ubuntu, or i915.modeset=0 ubuntu, or i915.modeset=1 ubuntu

There is an problem with the intel driver that requires you to set boot parameters, (t's fairly straight forward).  I'm not saying that this is the problem, but it be.

If you could post the output of > lspci people will be able to see what your hardware is and give more accurate advice.

There are other boot options available through the F4 and F6 keys at boot (liveCD) -
You might have to set noacpi or one of the other options

oh, and have a look at the first part of this thread:> [http://ubuntuforums.org/showthread.php?t=1479633]("http://ubuntuforums.org/showthread.php?t=1479633")

---

### Post by -humanaut- on 2010-05-16
What type of Graphics card does the system have?

---

### Post by manojvajram on 2010-05-16
[B]Almost same problem with me. My system celeron 2.4ghz with 1.5 ddr2 ram, with 865intel board desktop pc. upto Ubuntu9.10 it was working fine. For 10.04LTS it hangs most of the time at boot up. On recovery mode I can see /script/init-bottom is the last command that booting script executing. After that system hangs and monitor displays no signal. And surprisingly sometimes it boots up without any problem. But booting time is more compared to ver.9.10.
Kindly help me.[/B]

---

### Post by flowingfire on 2010-05-16
Ubuntu 10.04 simply doesn't work.

---

### Post by Atavaka on 2010-05-16
Nomodeset, noacpi, and nolacpi (? I think that was the last one) all resulted in the same thing- hanging after the splash. 

Here is the output from lspci-

	 	 00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)  
 00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)  
 00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)  
 00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)  
 00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)  
 00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)  
 00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)  
 00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)  
 00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)  
 00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)  
 00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)  
 00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)  
 00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)  
 00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)  
 02:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)  
 02:04.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller  
 02:04.1 CardBus bridge: Texas Instruments PCI7420 CardBus Controller  
 02:04.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller  
 02:04.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller  
 02:05.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

---

### Post by manojvajram on 2010-05-16
The lspci of my computer is also attached for reference.
Plz. help me
*************************
[B][COLOR="Red"]00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)[/COLOR][/B]

---

### Post by Atavaka on 2010-05-17
Aaaaaaaand bump.

---

### Post by manojvajram on 2010-05-17
Today it took 6 reboot to boot to my new 10.04. Again on verification it is found that the problem is with memory.(memory full message is flashing). And it took 2 minute to boot. My earlier 8.04 was booting in 55 seconds. Can anybody give me a solution.

---

### Post by fbobraga on 2010-08-16
I've faced this issue this weekend.

This is how I solved/workaround ed it: at liveCD boot screen, I've hited ESC and edited the first entry putting this in the end:
```
xforcevesa
```

... now I'm looking for how change it to the 'intel' (instead of 'vesa') driver on the installed system...

edit: I will try it in the next weekend: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) (it's my Dad's HP Pavilion ze2000 laptop, that I have access only in weekends)

---

### Post by dranockcir on 2010-09-14
I had this problem with a Dell Inspiron 710m and it is with the video driver. I had to add "i915.modeset=1" to grub.cfg and I have to do it each time there is s kernel upgrade because grub.cfg gets overwritten. Just did it now for a friend. Anyway, hold down SHIFT while computer is starting to get GRUB menu, press "e" to edit. Use arrow keys to navigate and add "i915.modeset=1" no quotes of course after the "quiet splash" command and be sure to add a space between like this "quiet splash i915.modeset=1"  then press CTRL-X to go ahead and boot the computer. Once you get logged in, you need to edit grub.cfg as root and add the "i915.modeset=1" after the "quiet splash" command. You can add it after the other "quiet splash" commands for the older kernels you may have in your grub.cfg if you use them.

Rick

---

### Post by Yappy on 2010-09-20
I am using AMD, I too have this problem.

---

