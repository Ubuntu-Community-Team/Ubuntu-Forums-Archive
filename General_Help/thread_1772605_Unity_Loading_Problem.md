---
title: "Unity Loading Problem"
date: 2011-05-31
forum: General Help
---

### Post by charliewhizbeez on 2011-05-31
Hey all, I've never liked unity much so I've been using classic.  However, out of curiosity I decided to give it a try.  However, when I tried to load it, my login sound played, but the dock and the taskbar didn't load.

I've been using compiz in classic, so would that have anything to do with it?


Thanks if you can help!:P

---

### Post by charliewhizbeez on 2011-05-31
By the way, here's a picture.  I forgot to tell you all that the compiz splash doesn't load and that my icons do.  The white spaces are some pictures of some family that I decided not to post on the web.  That was done in GIMP.

[IMG]https://lh3.googleusercontent.com/-8DlvXmCf4zw/TeWDKWTMtwI/AAAAAAAAAFg/VhOm7UDdUwc/s800/Screenshot-2.png[/IMG]

---

### Post by wildmanne39 on 2011-05-31
> **charliewhizbeez said:**
> Hey all, I've never liked unity much so I've been using classic.  However, out of curiosity I decided to give it a try.  However, when I tried to load it, my login sound played, but the dock and the taskbar didn't load.

I've been using compiz in classic, so would that have anything to do with it?


Thanks if you can help!:PHi, no what happens in the gnome is separate they did not sure settings. Need to know the specs of your system. put this into the terminal
```
lspci
```then post it here.Also run this in terminal and post here.
```
/usr/lib/nux/unity_support_test -p
```for each command click # and paste the information between the brackets.

---

### Post by garvinrick4 on 2011-05-31
Most likely:
[http://ubuntuforums.org/showthread.php?p=10887741#post10887741](http://ubuntuforums.org/showthread.php?p=10887741#post10887741)

---

### Post by charliewhizbeez on 2011-06-02
Here are the lspci results:

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N + WiMAX 6250 (rev 57)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05) 
```

---

### Post by charliewhizbeez on 2011-06-02
And the other command


```
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

```

---

### Post by dFlyer on 2011-06-02
This link might be able to provide the information you need to fix your problems. Hope it works:

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by charliewhizbeez on 2011-06-02
> **garvinrick4 said:**
> Most likely:
[http://ubuntuforums.org/showthread.php?p=10887741#post10887741](http://ubuntuforums.org/showthread.php?p=10887741#post10887741)


Okay, CCSM was already installed, but the thing is is that the unity plugin isn't there.  Also, when I type in unity-reset, it says that unity isn't installed.


Should I install it with

```

sudo apt-get install unity

```

like it says?

---

### Post by charliewhizbeez on 2011-06-02
I tried sudo apt-get install unity.  Trying unity -reset now.


RESULT:

```

Usage: unity [options]

unity: error: no such option: -r


```

---

### Post by charliewhizbeez on 2011-06-02
Okay.  I restarted X and now unity is working.   The plugin is checked in ccsm, but the compiz effects aren't working.

---

### Post by charliewhizbeez on 2011-06-02
Sigh, never mind, that's just the unity plugin. 


Oh well, thanks guys, for the most part I'll be using classic but this is really helpful for 11.10.

THANKS!

---

### Post by wildmanne39 on 2011-06-02
> **charliewhizbeez said:**
> Sigh, never mind, that's just the unity plugin. 


Oh well, thanks guys, for the most part I'll be using classic but this is really helpful for 11.10.

THANKS!
Hi, ok I am glad you got to check out unity, I have the cube working in unity, you have to follow these instructions to activate it in unity, here is the link.
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

---

