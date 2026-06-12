---
title: "ATI driver problems"
date: 2011-12-26
forum: General Help
---

### Post by smiche on 2011-12-26
I have recently Installed Ubuntu 10.04 and I can't seem to make my graphic card drivers work.
My graphic card model is ATI Radeon 9550.
I tried 3 things to install them & none worked.
1st System->Administration->Hardware Drivers.(nothing was found).
2nd System->Administration->Synaptic Package Manager.
All of the packets I needed were already installed.
3rd Downloaded the drivers from [www.amd.com](www.amd.com) and installed the .run file.
Still nothing works.
System->Preferences-> ATI Catalyst Control Center gives this error on start->
```
 p, li { white-space: pre-wrap; } There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
  No ATI graphics driver is installed, or the ATI driver is not functioning properly.
 Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.
  
```
Help appreciated.
I cant open any 3D games or set Appearance visual effects to maximum.

---

### Post by 2F4U on 2011-12-26
Which version did you download? If the Additional Drivers tool doesn't find a driver for your card, this usually means there is no support from ATI for your card.

---

### Post by smiche on 2011-12-26
Well i downloaded the one for 9x series which had my gfx card in the list.

---

### Post by mastablasta on 2011-12-26
> **smiche said:**
> I have recently Installed Ubuntu 10.04 and I can't seem to make my graphic card drivers work.
My graphic card model is ATI Radeon 9550.

Old card. ATI dropped Linux driver support for this card soem time ago. You have two options 
1. use old version of the OS where drivers sitll worked (not recommended). 
2. Use the opensource driver that is provided automaticly by Ubuntu on install. there is a way to use PPA to upgrade them to latest version if you do not want to use the latest Ubuntu version that also has them. Some more info on this can be found here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

> 

I tried 3 things to install them & none worked.
1st System->Administration->Hardware Drivers.(nothing was found).
2nd System->Administration->Synaptic Package Manager.
All of the packets I needed were already installed.

Indeed they were.

> 
3rd Downloaded the drivers from [www.amd.com]("http://www.amd.com") and installed the .run file.
Still nothing works.
System->Preferences-> ATI Catalyst Control Center gives this error on start->
```
 p, li { white-space: pre-wrap; } There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
  No ATI graphics driver is installed, or the ATI driver is not functioning properly.
 Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.
  
```Help appreciated.


Wrong approach that will not work as the latest ATI drivers do not work under newer Ubuntu versions. you will need to remove them now if you managed to install them and revert to open source ones. use this page to help you with that: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

> 
I cant open any 3D games or set Appearance visual effects to maximum.
9500 should have good 3d support with opensource drivers. follow the first link i gave you for more info or if you decide to upgrade the drivers.

---

### Post by coffeecat on 2011-12-26
The only proprietary ATI driver for the Radeon 9550 Series is a legacy one which will only work with Linux releases prior to 2009 - for Ubuntu that means the obsolete 8.10 or earlier. See:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

Unfortunately, there is no alternative to the open source driver in 10.04 for that legacy card.

---

### Post by smiche on 2011-12-26
How can I get the open source driver x.x?

---

