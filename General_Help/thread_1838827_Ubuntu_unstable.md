---
title: "Ubuntu unstable"
date: 2011-09-04
forum: General Help
---

### Post by Ltw on 2011-09-04
I have just installed Ubuntu 10.04 to my AMD Athlon 64 and I experienced that my system is too unstable. It is fast (booting the system takes 4 till 6 seconds) but sometimes (especially when I use Firefox) it just crashes.

Does anyone know what the problem might be?

Ltw.

---

### Post by FormatSeize on 2011-09-04
10.XX just crashes? That's unusual (relatively speaking). Can you give more detail on what hardware you have?

---

### Post by Ltw on 2011-09-04
> **FormatSeize said:**
> 10.XX just crashes? That's unusual (relatively speaking). Can you give more detail on what hardware you have?

I have:
- AMD Athlon 64 2,4Ghz.
- 2GB DDR400
- Samsung MP4 500GB HDD (the fastest regular drive which I could pay :P ).
- MSI Nvidia graphics card with 1GB DDR3 (couldn't find the type number, I lost the box).
- Motherboard with Sata II, all my drives etc. are plugged with Sata II.

---

### Post by dino99 on 2011-09-04
and i suppose you have installed ubuntu 32 bits right ?

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

---

### Post by Ltw on 2011-09-04
> **dino99 said:**
> and i suppose you have installed ubuntu 32 bits right ?

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

No, I installed the 64bit. Forgot to mention it. I have a 64bit system and I also run Win7 64bit so I figured that it would be the best if Ubuntu is also 64bit. Or are there some bugs in the 64bit version?

---

### Post by soumyabratapaul on 2011-09-04
Download the Ubuntu that specifically is for the AMD system and not for the Intel based system. And as far as the "unstable" question goes, Ubuntu 10.04 is an LTS version, which means that it has 3 years of support against the traditional 6 months of support, which specifically means that Ubuntu 10.04 is very stable(I am personally using that, so I know about the "stability" question). The problem is that you have install an Intel based version, whereas you should have installed the AMD one. This should solve your problem.

---

### Post by overdrank on 2011-09-04
> **soumyabratapaul said:**
> Download the Ubuntu that specifically is for the AMD system and not for the Intel based system. And as far as the "unstable" question goes, Ubuntu 10.04 is an LTS version, which means that it has 3 years of support against the traditional 6 months of support, which specifically means that Ubuntu 10.04 is very stable(I am personally using that, so I know about the "stability" question). The problem is that you have install an Intel based version, whereas you should have installed the AMD one. This should solve your problem.

:confused:

---

### Post by IWantFroyo on 2011-09-04
> **soumyabratapaul said:**
> Download the Ubuntu that specifically is for the AMD system and not for the Intel based system. And as far as the "unstable" question goes, Ubuntu 10.04 is an LTS version, which means that it has 3 years of support against the traditional 6 months of support, which specifically means that Ubuntu 10.04 is very stable(I am personally using that, so I know about the "stability" question). The problem is that you have install an Intel based version, whereas you should have installed the AMD one. This should solve your problem.

Actually, it really shouldn't matter. As long as your computer is 64bit, amd64 or i386 should work fine.

Did you install Firefox from Mozilla's website? That isn't the best way to install it.
Delete the Firefox folder (assuming you downloaded it from Mozilla) and run this to get the newest version:
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```
```
sudo apt-get update && sudo apt-get install firefox
```

---

### Post by aeronutt on 2011-09-04
> **Ltw said:**
> No, I installed the 64bit. Forgot to mention it. I have a 64bit system and I also run Win7 64bit so I figured that it would be the best if Ubuntu is also 64bit. Or are there some bugs in the 64bit version?

There are bugs in both 32 and 64b versions. ;)  I wouldn't go re-intalling 32b version until you can provide a bit more info.  Is your load up to date? (run update manager.) Have you tried running from liveCD, and if so does it crash from liveCD also?

More importantly, what happens when it 'crashes'.

---

### Post by Ltw on 2011-09-04
I use the Firefox client which is included in Ubuntu.

My system is completely up to date.

When Ubuntu freezes it is possible that two things happen.
I've had some problems with Facebook, scrolling down works but when I scroll up it closes down and I see a lot of text. The only way to let this disappear is to press the reset button. Scrolling in other sites works fine by the way. I've also had some problems with switching tabs sometimes, when I do this it freezes and I can't move the mouse any more, it just doesn't respond to anything, again, the only way to let this disappear is to press the reset button.

I hope I gave enough information.

Ltw.

---

### Post by Wim Sturkenboom on 2011-09-04
> **Ltw said:**
> I have just installed Ubuntu 10.04 to my AMD Athlon 64 and I experienced that my system is too unstable. It is fast (booting the system takes 4 till 6 seconds) but sometimes (especially when I use Firefox) it just crashes.

Does anyone know what the problem might be?

Ltw.
Are you using the nouveau driver (standard), a driver from the repository or a driver from the nvidia website? This question relates to the video driver. If the nouveau, try the one from the repository and see if it fixes the problem. It might however break the system.
Can you post the output of lspci? Output will look like below. This should reveal the video card that you have (or at least the chip on it).
```

wim@aa0:~$ **lspci**
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
wim@aa0:~$ ^C

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
wim@aa0:~$ 

```

> **soumyabratapaul said:**
> Download the Ubuntu that specifically is for the AMD system and not for the Intel based system. And as far as the "unstable" question goes, Ubuntu 10.04 is an LTS version, which means that it has 3 years of support against the traditional 6 months of support, which specifically means that Ubuntu 10.04 is very stable(I am personally using that, so I know about the "stability" question). The problem is that you have install an Intel based version, whereas you should have installed the AMD one. This should solve your problem.

There is only one 64 bit version; so what are you talking about :confused:

---

### Post by aeronutt on 2011-09-04
Hmmm...also, I've had a 'bad' install of flash cause similar problems. Although while it took complete control of the browser, I was always able to move the mouse. You might consider installing 'flash-aid' in firefox and running it. I'll recommend telling it to install a stable version of flash rather than a beta version, if it asks.

---

### Post by Ltw on 2011-09-05
Everyone, thanks for your advice.

I'm not home right now but when I'm home I will try it out.

I'm sure my problem will be solved!

Ltw.

---

