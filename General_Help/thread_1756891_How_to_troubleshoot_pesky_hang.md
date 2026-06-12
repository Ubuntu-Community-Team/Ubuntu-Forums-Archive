---
title: "How to troubleshoot pesky hang"
date: 2011-05-12
forum: General Help
---

### Post by keevill on 2011-05-12
I have a dual boot Ubuntu 10.04 and Win XP and I have recently been forced to use Windows for some applications which won't work under Linux.
Having completed those tasks, I now boot up into ( my preferred OS ) Ubuntu however after login and perhaps 1 minute, just enough time to open a firefox or chrome browser , the system just freezes.
It's a very basic box with basic hardware and it was working fine and no changes have been made to it.
How can I troubleshoot this problem please ?
-keevill-

---

### Post by manzdagratiano on 2011-05-12
You need to tell us what your hardware is. Post the output of:

```

$ lspci

```Focus on the Graphics card:

```

$ lspci | grep VGA

```In the absence of that information, the only conceivable problem I can see with freezes is that if you have an nvidia video card, you may be plagued by the "powermizer" issue, which I have also faced. In that case, you will need to do the following:

1) Hit Ctrl + Alt + F1: This will take you to a virtual terminal. Login there.
2) Type:

```

$ sudo dpkg-reconfigure xserver-xorg

```This will generate a rudimentary /etc/xorg.conf. Open it:

```

$ sudo nano /etc/xorg.conf

```Edit the "Device" section with:

```

Section "Device"
  Identifier "NVIDIA GeForce"
  Driver     "nvidia"
  Option     "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerDefault=0x3 PowerMizerDefaultAC=0x1"
EndSection

```Then reboot:

```

$ sudo reboot

```and you should be all set next time.

---

### Post by keevill on 2011-05-12
> **manzdagratiano said:**
> You need to tell us what your hardware is. Post the output of:

```

$ lspci

```Focus on the Graphics card:

```

$ lspci | grep VGA

```In the absence of that information, the only conceivable problem I can see with freezes is that if you have an nvidia video card, you may be plagued by the "powermizer" issue, which I have also faced. In that case, you will need to do the following:

1) Hit Ctrl + Alt + F1: This will take you to a virtual terminal. Login there.
2) Type:

```

$ sudo dpkg-reconfigure xserver-xorg

```This will generate a rudimentary /etc/xorg.conf. Open it:

```

$ sudo nano /etc/xorg.conf

```Edit the "Device" section with:

```

Section "Device"
  Identifier "NVIDIA GeForce"
  Driver     "nvidia"
  Option     "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerDefault=0x3 PowerMizerDefaultAC=0x1"
EndSection

```Then reboot:

```

$ sudo reboot

```and you should be all set next time.

Looks a very comprehensive and plausible answer.
I am not at the box until later. I will try and post back results.
Many thx,
-keevill-

---

### Post by keevill on 2011-05-13
> **manzdagratiano said:**
> You need to tell us what your hardware is. Post the output of:

```

$ lspci

```Focus on the Graphics card:

```

$ lspci | grep VGA

```In the absence of that information, the only conceivable problem I can see with freezes is that if you have an nvidia video card, you may be plagued by the "powermizer" issue, which I have also faced. In that case, you will need to do the following:

1) Hit Ctrl + Alt + F1: This will take you to a virtual terminal. Login there.
2) Type:

```

$ sudo dpkg-reconfigure xserver-xorg

```This will generate a rudimentary /etc/xorg.conf. Open it:

```

$ sudo nano /etc/xorg.conf

```Edit the "Device" section with:

```

Section "Device"
  Identifier "NVIDIA GeForce"
  Driver     "nvidia"
  Option     "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerDefault=0x3 PowerMizerDefaultAC=0x1"
EndSection

```Then reboot:

```

$ sudo reboot

```and you should be all set next time.

I can only get the machine to stay unfrozen by booting into 'failsafe low graphics mode'.
Here is the output of the device info. I don't think that the Nvidia graphics card is the problem. If I continue with the creation of a xorg.conf file, I get a totally blank one so I did not input any of the info suggested.
Any input from knowledgeable folks welcomed.
-keevill-

lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
02:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
02:02.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
david@david-desktop:~$ 
____________

lspci | grep VGA

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

_________________

---

### Post by manzdagratiano on 2011-05-15
It appears you do not have an nvidia card, in which case my suggestion above will not work at all. You should then not need to create an xorg.conf.

Your configuration seems to be similar to my other laptop which has an Intel graphics card, and all works fine here, so I really don't know why the freeze happens. Maybe you could post the output of /var/log/Xorg.0.log when a freeze happens?

Also, when a freeze happens, can you hit Ctrl + Alt + F1 and log into a virtual terminal? If you can kill X by issuing:
```

$ sudo pkill X

```

and that fixes the freeze without having to hard reboot, that's one step better.

---

