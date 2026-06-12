---
title: "Dual monitors in ubuntu with diff resolution - screen problems"
date: 2011-08-09
forum: General Help
---

### Post by MorrisseyJ on 2011-08-09
Hi,

I am trying to set up dual monitors in Ubuntu, with the two monitors having different resolutions. One monitor is on my laptop and the other is an external monitor. 

I have seen a number of threads detailing this.

1. Talks about editing xorg.conf. 
- The problem here is that i don't seem to have an xorg.conf file in /usr/share/X11. When i > locate xorg.conf in the terminal i get:
> /usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/10-evdev.conf
/usr/share/X11/xorg.conf.d/11-evdev-quirks.conf
/usr/share/X11/xorg.conf.d/50-synaptics.conf
/usr/share/X11/xorg.conf.d/50-vmmouse.conf
/usr/share/X11/xorg.conf.d/50-wacom.conf
/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
/usr/share/doc/xserver-xorg-video-nouveau/examples/xorg.conf
/usr/share/man/man5/xorg.conf.5.gz2. Talks about editing xrandr, linking to this page [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)
- This looks incredibly intimidating and i can't really work out what to do in my case. 

3. Try changing resolution on one of the monitors in ~/.config/monitors.xml, which is where i got the unity dock to only show on the primary monitor. 
- Here, after i saved and logged out and in, i got an error msg saying the the resolution wouldn't work. When i looked at ~/.config/monitors.xml, the resolutions had reverted back to what they were originally.

4. I have tried 'configure display settings' in 'monitor preferences'. Here i can change the resolution of each monitor quite easily. This works and the resolution is perfect. The problem though is once i have done this monitor on my laptop - the one with the higher resolution - behaves really strangely. When i close things they don't disappear off the screen, the unity dock smears on the screen when it minimizes and mouse pointer labels show up and then don't disappear. 

So i am now stumped. If anyone can tell me either how to sort the resolution, interpret the xrandr instructions or fix the screen smearing i would be very grateful.

Thanks.

---

### Post by MorrisseyJ on 2011-08-11
I managed to find a partial fix to this:

I was able to set the resolution that i wanted using option 4 from the original post. To get rid of the screen problems (things smearing and sticking on the screen) i simply had to log in using the Ubuntu classic desktop (without effects). So it seems that the problem was being caused by the advanced effects in unity. 

i am left with one small problem now: The screen size appears to be taken from the larger 19" monitor. This means that the mouse can fall off the top or bottom (or both) of the smaller monitor, depending on where i position the smaller monitor in relation to the larger one (in 'monitor preferences'). This isn't much of an issue however as the GNOME menus bound the size to which applications maximise in the smaller monitor. So i am happy to live with this.

Thanks to the people on the Ubuntu UK mailing list who helped me out.

P.S. My graphics card was an ATI Radeon Express 200M, i was running Natty and 

> lspci -v -s `lspci |grep VGA|awk {'print $1'} into the terminal returns:

> 01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon
Xpress 200M] (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Device 1392
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9800 [size=256]
        Memory at fe1f0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at fe1c0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: radeon
        Kernel modules: radeon, radeonfb

---

