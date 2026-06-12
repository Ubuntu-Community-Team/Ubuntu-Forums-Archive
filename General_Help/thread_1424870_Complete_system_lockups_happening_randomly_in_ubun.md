---
title: "Complete system lockups happening randomly in ubuntu karmic."
date: 2010-03-08
forum: General Help
---

### Post by Mr.Banana on 2010-03-08
Hello. My Ubuntu Karmic running system experiences random lockups. There is no pattern in when it will happen, it can go for days without one, or happen every couple hours. Only thing I can notice is that it happens most often when I run Firefox, but when it happens, it happens regardless of me having Firefox open on a website with lots of Flash content or not. 

When the lockup happens, I cannot move the mouse - the led light on my mouse shuts off, I can't move the cursor, the whole UI becomes unrensponsive, there is no blinking lights on the keyboard, REISUB does not work, only hitting the reset button on my case helps. After reboot, there are no indications of errors in any of the logs that I can see.

I have ran memtest for 24 hours, and it completed without errors. 

Additional information:

1. LSPCI output:

```
00:00.0 Host bridge: ALi Corporation M1697 HTT Host Bridge
00:01.0 PCI bridge: ALi Corporation PCI Express Root Port
00:02.0 PCI bridge: ALi Corporation PCI Express Root Port
00:03.0 PCI bridge: ALi Corporation PCI Express Root Port
00:04.0 PCI bridge: ALi Corporation PCI Express Root Port
00:11.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:12.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 60)
00:13.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:14.0 Audio device: ALi Corporation High Definition Audio/AC'97 Host Controller (rev 01)
00:15.0 ISA bridge: ALi Corporation PCI to LPC Controller (rev 10)
00:15.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:16.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:16.1 IDE interface: ALi Corporation ULi M5288 SATA
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV670PRO [Radeon HD 3850]
01:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device
05:0a.0 Communication controller: Conexant Systems, Inc. SoftV92 SpeakerPhone SoftRing Modem with SmartSP (rev 01)

```

2. Computer configuration:

MBO: ASROCK am2xli-esata2
CPU: AMD Athlon X2 64 6000+
GPU: ATi RadeonHD 3850 (Using catalyst 10.2 drivers(fglrx)


Thanks in advance for any help.

---

### Post by Sin@Sin-Sacrifice on 2010-03-08
I don't have much experience with ati cards but I would start with that. Such as reinstalling the drivers or checking the compatibility. After it freezes, and if you have a means, try to ssh into it too.

---

### Post by Techsnap on 2010-03-08
> GPU: ATi RadeonHD 3850 (Using catalyst 10.2 drivers(fglrx)

Did this happen before you installed the newest version of the ATi driver? Does it happen with the default ATi driver or the ones from the restricted driver manager?

---

### Post by LowSky on 2010-03-08
I had a similar issue a little while back, and I have a Nvidia graphics card. What Kernel are you using. The issue for me has gone away since I've upgraded. Also check for BIOS updates. They might improve your system stability as well.

My system has the following

AMD Phenom II x2 550
msi 790fx-gd70
Nvidia 8600GT

---

### Post by Mr.Banana on 2010-03-08
> **Sin@Sin-Sacrifice said:**
> I don't have much experience with ati cards but I would start with that. Such as reinstalling the drivers or checking the compatibility. After it freezes, and if you have a means, try to ssh into it too.

I have tried to reinstall the drivers, to no avail. I don't know how to check the compatibility. All I know that these drivers are for my graphics card. 

I do not know how to ssh into the system, and if I'm right about what ssh is, then I think that I dont have any means to ssh into the system.

> **Techsnap said:**
> Did this happen before you installed the newest version of the ATi driver? Does it happen with the default ATi driver or the ones from the restricted driver manager?

It happened before, even with the ones from the the restricted driver manager.

I have not tried to use open source drivers.  

> **LowSky said:**
> I had a similar issue a little while back, and I have a Nvidia graphics card. What Kernel are you using. The issue for me has gone away since I've upgraded. Also check for BIOS updates. They might improve your system stability as well

I am using the 2.6.31.20 kernel. I have not used any newer kernel on this machine. Also, my motherboard is using the latest BIOS update.

What I have done so far is disable Compiz completely. I have not uninstalled it though. I will run with Compiz disabled for couple of days and see if fixes the problem.

---

### Post by Mr.Banana on 2010-03-08
Well, disabling compiz did not do the trick- It just happened again, this time while watching a youtube video using Firefox. 

Next thing I'll do is try Google chrome and Opera.

Here are, for those bored enough to read them, all the logs attached to this post.

---

### Post by Kheops_74 on 2010-03-08
I'm not sure if it's the same problem here. Google Chrome freeze the computer and MythTV play recording but the screen is unreadable when it go back to the menu. 

How can i update the driver at the last version in Ubuntu?

K

---

### Post by ShapeShifta on 2010-03-09
I'm having a similar issue and it's with my old laptop. Everytime it's been with google chrome open, either immediate or having it open a while, the laptop will just lock up completely. I have no other way of explaining what's going on. I don't have these issues on my desktop which is much more recent. I had to install another web browser just to post and search for  a solution.

---

### Post by Sin@Sin-Sacrifice on 2010-03-11
I can't remember where it is but you can check compatability of gpus and drivers here in the forums somewhere. Since it's happening so randomly I can only assume hardware issues. Reboot and and try to put the cpu under heavy load. If you have lm sensors that show voltages you can check to see if they're right on or high. Have you tried overclocking or anything like that? Or is it pretty random? I know with firefox but is there anything you did to the system before it happened? Updates, reconfigure anything, add new hardware?

---

