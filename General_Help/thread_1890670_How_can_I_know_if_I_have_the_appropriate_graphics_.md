---
title: "How can I know if I have the appropriate graphics card drivers installed?"
date: 2011-12-04
forum: General Help
---

### Post by 3Nex on 2011-12-04
I don't know what i'm doing! In the past few years that i've been using Ubuntu, in some installations the Desktop would be all jittery (if that's the word), the Alt+Tabbing would be slow, Compiz would be slow my whole computer down unbelievably, while some other installations things seemed to be more okay. This last one, i again seem to have struck a bad graphics installation, but with the introduction of the Unity interface, the Desktop has become unbearable! 

But each time tho, i installed the "recommended" (173) driver for nVidia, but it looks as if sometimes it just doesn't work as well as other times. Especially considering that at one time i was able to play Quakelive fullscreen with no problems, then in my last install i couldn't play it normally without fullscreen. 

How do i check if i'm using the best driver and if the driver is correctly installed? Can it be something other than the graphic drivers?

---

### Post by oldtimer7777 on 2011-12-04
You can try going down the checklist first to see if you got everything installed correctly.. This works for most users that want to be sure:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **3Nex said:**
> I don't know what i'm doing! In the past few years that i've been using Ubuntu, in some installations the Desktop would be all jittery (if that's the word), the Alt+Tabbing would be slow, Compiz would be slow my whole computer down unbelievably, while some other installations things seemed to be more okay. This last one, i again seem to have struck a bad graphics installation, but with the introduction of the Unity interface, the Desktop has become unbearable! 

But each time tho, i installed the "recommended" (173) driver for nVidia, but it looks as if sometimes it just doesn't work as well as other times. Especially considering that at one time i was able to play Quakelive fullscreen with no problems, then in my last install i couldn't play it normally without fullscreen. 

How do i check if i'm using the best driver and if the driver is correctly installed? Can it be something other than the graphic drivers?

---

### Post by jfed on 2011-12-04
I'm not sure, but if you go to system>administration>additional drives, it'll show you a list of additional drivers you have the option to install

---

### Post by raja.genupula on 2011-12-04
assassin@assassin-ubuntu:~$ lsmod | grep video
video                  18908  1** i915**


that  bold one indicates right drivers are in, if not proper one installed then its gonna something like some word i didnt remember that properly .

---

### Post by 3Nex on 2011-12-04
> **oldtimer7777 said:**
> You can try going down the checklist first  to see if you got everything installed correctly.. This works for most  users that want to be sure:
 
 [https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
 I did only the graphics card part; It did some work and installed some stuff, but i see no improvement. 
 

> **jfed said:**
> I'm not sure, but if you go to  system>administration>additional drives, it'll show you a list of  additional drivers you have the option to install
What i mentioned in my post about installing the recommended drives, that was through this. So been there, done that. 


> **raja.genupula said:**
> assassin@assassin-ubuntu:~$ lsmod | grep video
video                  18908  1** i915**


that  bold one indicates right drivers are in, if not proper one installed then its gonna something like some word i didnt remember that properly .
Well... that command returns nothing for me. But there is a line in [FONT=Courier New]lsmod[/FONT] that says "nvidia 10782577 40". 

Should i be worried?


Also, my xorg.conf says this, if that helps any... 
```
Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

```

---

### Post by 2F4U on 2011-12-04
> **raja.genupula said:**
> assassin@assassin-ubuntu:~$ lsmod | grep video
video                  18908  1** i915**


that  bold one indicates right drivers are in, if not proper one installed then its gonna something like some word i didnt remember that properly .

You probably mean lspci instead of lsmod?

---

### Post by 3Nex on 2011-12-04
> **2F4U said:**
> You probably mean lspci instead of lsmod?
Well if he does, the output of [FONT=Courier New]lspci[/FONT] is actually this: 
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46)
```

---

### Post by 3Nex on 2011-12-05
Oh please please please someone.. :( Everything is superslow! Please help.. 

Maybe this computer is just getting to old for this new Ubuntu Unity interface? It's a GeForce 6200 Turbocache. What do you think?

---

