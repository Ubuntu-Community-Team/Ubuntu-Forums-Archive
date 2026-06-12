---
title: "Dell Vostro 3560 - Ati/Intel Graphic Problem"
date: 2012-08-17
forum: General Help
---

### Post by xCAFEBABE on 2012-08-17
I just bought a Vostro 3560 and  as usually I do, immediately the Windows partition is removed (previous  partition backup, for warranty proposal) and then I made  a fresh  installation of Ubuntu Desktop.

In general everything works as expected BUT I had several problems with  this fresh installation of Ubuntu 12.04, the most critical and unsolved  is the Battery Life, only 1h:30m !!!

After two days trying different options, I give up and ask for help.

The battery problem is related to the Dual Graphic card option.

These are my graphic cards
**Ati Radeon 7600M**
```

01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD]  nee ATI Thames XT/GL [Radeon HD 7600M Series] [1002:6840] (prog-if 00  [VGA controller])
        Subsystem: Dell Device [1028:056e]
        Flags: fast devsel, IRQ 7
        Memory at a0000000 (64-bit, prefetchable) [disabled] [size=256M]
        Memory at c2000000 (64-bit, non-prefetchable) [disabled] [size=128K]
        I/O ports at 4000 [disabled] [size=256]
        Expansion ROM at c2020000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Legacy Endpoint, MSI 00
        Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
        Capabilities: [150] Advanced Error Reporting
        Kernel modules: fglrx, radeon

```and

**Intel Ivy**
```

00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge   Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
        Subsystem: Dell Device [1028:056e]
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at c3000000 (64-bit, non-prefetchable) [size=4M]
        Memory at b0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 5000 [size=64]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
        Capabilities: [d0] Power Management version 2
        Capabilities: [a4] PCI Advanced Features
        Kernel driver in use: i915
        Kernel modules: i915

```I followed instructions of this two articles
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)
[http://asusm51ta-with-linux.blogspot.de/](http://asusm51ta-with-linux.blogspot.de/)

But in both cases, after the first reboot I got a black screen with this message


> 
The system is running in low-graphic mode 

Your screen, graphics and input device setting could not be detected correctly.

You will need to configure these yourself


After this message, it's possible recover selecting a default xorg configuration. 

I think something is missing in xorg.conf but right now I don't know how to proceed

Any help from the community?

---

### Post by xCAFEBABE on 2012-08-17
Ok, after reading carefully these articles


[LIST]
[*][https://wiki.archlinux.org/index.php/Hybrid_graphics#ATI_Dynamic_Switchable_Graphics](https://wiki.archlinux.org/index.php/Hybrid_graphics#ATI_Dynamic_Switchable_Graphics)
[*][https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
[*][http://asusm51ta-with-linux.blogspot.de/](http://asusm51ta-with-linux.blogspot.de/)
[/LIST]

I found a solution that improve  battery life from 1:30h to 3:00h  and also the laptop temperature is colder than before, it's more acceptable now.

1.- Remove completely fglrx driver for ATI

```

sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx*
sudo apt-get update
sudo reboot

```You should check if your ATI Driver is using  after reboot the opensource driver [I]radeon
[/I][FONT=Courier New]lspci -nnnv | grep ATI -A 5[/FONT]


2.- Add this lines to /etc/rc.local (before exit 0)

```

chmod o+rx /sys/kernel/debug
#Replace USERNAME with your user
chown USERNAME /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

```With this, next time you reboot, the discrete GPU will be switched off and after that you will see a lot of improvements in your battery life.

Also if you want a script to switch on/off your ATI GPU, you kindly follow  instructions from here [http://asusm51ta-with-linux.blogspot.de/](http://asusm51ta-with-linux.blogspot.de/) and setup an script at your convenience.

Cons of this you can't use Unity 3d anymore (at least in my case), but, I can live better with that ;)

---

### Post by QIII on 2012-08-17
Provided your ATI discrete graphics card is a 6xxx series or higher, the ATI wiki in my signature gives a clean method that has worked for some users to preserve the Intel/ATI switchable graphics feature.

The Catalyst Control Center can be used to switch the graphics and switcheroo is not needed.

---

### Post by xCAFEBABE on 2012-08-17
> **QIII said:**
> Provided your ATI discrete graphics card is a 6xxx series or higher, the ATI wiki in my signature gives a clean method that has worked for some users to preserve the Intel/ATI switchable graphics feature.

The Catalyst Control Center can be used to switch the graphics and switcheroo is not needed.

Thanks for this great wiki article, yesterday I tried to follow this guide but not good results for me. 

After reboot from the install of fglrx driver and *sudo amdconfig --initial  *

I got a black screen with this message

```

The system is running in low-graphic mode 

Your screen, graphics and input device setting could not be detected correctly.

You will need to configure these yourself

```

So for the moment vgaswitcheroo is my savior.

---

### Post by QIII on 2012-08-17
Did you use the method where you ran the .run file directly and used the ATI installer?

---

### Post by xCAFEBABE on 2012-08-18
> **QIII said:**
> Did you use the method where you ran the .run file directly and used the ATI installer?

After your message, I decided to try a fresh install of Ubuntu 12.04 again and now it worked with your guide!!! (Using deb files approach)

I think the difference this time was install the driver fglrx using your guide instead of trying try to install it first using "Additional Driver" functionality.

Thanks :) 

BTW: If you using only the Intel Integrated card, United 3d doesn't work, right?

---

### Post by xCAFEBABE on 2012-08-19
Well, after testing the laptop the all day, the main problem persist. Only 1:h 30!!! min battery life (supposedly using only integrated gpu) Unacceptable!!!

Is there some way to switch off  one of GPUs, using fglrx driver? (Through BIOS I can't do it)
I think amdconfig do the job correctly (switching GPUs), but I believe both cards are remaining ON, this is why there is no improvement in the battery life.

At least vgaswitcheroo offer me  3 hours of battery life.

---

### Post by bogosoundz on 2012-09-14
I had the same problem, vgaswitcheroo is enough for me... working like a charm.
Thanks for the tips...

---

### Post by jleon on 2012-12-20
Just to share my story after trying it for a week. 

I was able to get 4.3 hours out of the vostro 3560 with i7 3632. I used laptop-mode to turn on power saving on almost everything, and the above to make sure the radeon card is turned off. When using powertop, the power usage is as low as 8.7W using icewm (better than ubuntu 2D or 3D) when completely idle. I plan to install everything on to the mSATA drive or get a low power SSD drive to further reduce the power consumption. 

Please share your configuration if you can do better than 9W. The fan is still on and off with 8.7W mode, though the off-period is much longer now. PS. the fan noise is very annoying. I would like to turn it off completely when it is idle or when I am just doing some typing. 

The laptop is used for software development, with GCC compilation and sometimes running benchmarks/testing. I am happy with the sub-10W setup on, the fan noise is still very annoying.

---

