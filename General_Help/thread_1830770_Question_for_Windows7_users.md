---
title: "Question for Windows7 users"
date: 2011-08-22
forum: General Help
---

### Post by DaComboMan on 2011-08-22
I find when in Windows7 that the graphics and fonts look better.

I've tried to configure Ubuntu to be just as good but can't seem to press on the right buttons.

---

### Post by seawolf167 on 2011-08-22
So... like a higher monitor resolution? You can change your resolution under the "Monitors" preference panel. Or if needed install video drivers under "Additional Drivers" for your device to allow you to change your resolution to the max supported.

---

### Post by goldshirt9 on 2011-08-22
i run both Windoze and Ubuntu and to be truthful the only thing that may improve the 'look'
could be the graphic card you have installed.:confused:

i find no difference what so ever and would say that my Ubuntu set up is better.
More desktop app's and the like.

mess around with you settings in the linux set up you have or try something newer :D

---

### Post by Mark Phelps on 2011-08-22
If you tell us the make and model video card you're using, we can probably tell you if restricted drivers are available for it.  If you don't know the make and model, open a terminal and enter "lspic" -- and look for the line containing "VGA".  Post that information back here.

But, be forewarned that the open-source drivers have been improving considerably over the years.  I recently upgraded my home PC to newer hardware, and was able to switch over from the open-source ATI drivers to the latest restricted AMD drivers -- and have noticed no change at all in the quality of the graphics.  This is not so much a criticism of the new drives as it is praise for the quality of the open-source drivers.

Also, you can install the Microsoft fonts -- but that will only make your desktop look more like MS Windows. It won't really change the quality of the graphics.

---

### Post by 3rdalbum on 2011-08-22
> **DaComboMan said:**
> I find when in Windows7 that the graphics and fonts look better.

I've tried to configure Ubuntu to be just as good but can't seem to press on the right buttons.

Windows XP, Windows Vista7, Linux, KDE and Gnome all use different methods for font rendering.

As a result, sometimes it takes a little while to get used to the font rendering on a different system.

It's not "wrong" on any platform, it's just a bit different on each. Windows XP's font rendering used to give me headaches for days until I got used to it. Some Windows people have said the same thing about Ubuntu's. The feeling will pass.

There is a possibility that you're talking about a wrong screen resolution (which is something different altogether, if you're talking about graphics too) so keep in the thread and follow the suggestions given by others.

Good luck!

---

### Post by DaComboMan on 2011-08-22
@Mark,

I tried entering lspic but nothing happened...

As far as i can understand:

Video card is NVIDIA GeForce GT 130M
Monitor is Generic PnP 
Mode is 1366 x 768 with 32 bit color depth.

Font resolution 96dpi
Refresh rate 60Hz.

---

### Post by gandaran on 2011-08-22
> **DaComboMan said:**
> @Mark,

I tried entering lspic but nothing happened...

As far as i can understand:

Video card is NVIDIA GeForce GT 130M
Monitor is Generic PnP 
Mode is 1366 x 768 with 32 bit color depth.

Font resolution 96dpi
Refresh rate 60Hz.
```
lspci
```
not 'lspic', copy and paste to avoid typing error

---

### Post by seawolf167 on 2011-08-22
> **DaComboMan said:**
> I tried entering lspic but nothing happened...

You should have a bunch of lines of text, one of which will show your graphics card.

```
lspci
```

Here is the [driver ]("http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html")from Nvidia directly. You should have an entry under "Additional Drivers" to allow you to install this graphics card's drivers. I suggest to use this then you don't have to worry about rebuilding it each time the kernel is updated.

---

### Post by DaComboMan on 2011-08-22
@gandaran,

If you read the original suggestion by Mark,
you'll notice that i did copy/paste the code.
There was a discrepancy but that's okay.

Here's what i got:


0:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce GT 130M] (rev a1)
02:00.0 Network controller: Ralink corp. RT2860
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

@seawolf,

I couldn't install that driver you so kindly posted about.

---

### Post by seawolf167 on 2011-08-22
> **DaComboMan said:**
> ...
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce GT 130M] (rev a1)
...

So it is the correct card :P where you able to install any drivers through the "Additional Drivers" program?

---

### Post by seawolf167 on 2011-08-23
For the "Additional Drivers", in 10.10 and below, it is accessed through System -> Administration -> Hardware Drivers. In 11.04, it is accessed by clicking the power button in the upper right corner of the screen, selecting System Settings, then opening Additional Drivers.

---

### Post by DaComboMan on 2011-08-23
All i can find is an acceleration card for 3D something called Unity for which (after research) i don't find much use in installing.

---

### Post by seawolf167 on 2011-08-23
If its a graphics driver try installing it and then adjust the monitor's resolution so it is at its max.

---

### Post by DaComboMan on 2011-08-23
Just what i feared.

This Unity thingy installed a toolbar at the top that has no options to autohide anywhere and same thing for the one on the left for apps. Humongous buttons with no options to reduce or autohide.

All in all, i think graphics aren't that bad.
They may have improved a bit with this Unity thing but probably the fact that it's Linux and it's different from Windows is okay too.

---

### Post by seawolf167 on 2011-08-24
Take a look as these [two]("http://askubuntu.com/questions/9865/how-can-i-configure-unitys-launcher-auto-hide-behavior") [links]("http://askubuntu.com/questions/29553/how-can-i-configure-unity") and see if they help you with the Unity launcher.

---

### Post by DaComboMan on 2011-08-24
@seawolf,

Thanks for your ongoing efforts to help out!

I'm not sure 100% but i do believe that installing Unity did improve the general graphics appearance.

And yes, i don't why i didn't notice this before, but the Unity bar does autohide by default (as mentioned in your links) when an app is open.

What's bothering me now is the new Title bar that came along with Unity. Before i could set it up or down, autohide or not. The options to do this are hard to find.

BTW, with Unity which installed this Title bar, i was able to find CompizManager.



An eternal newbie and nerd to Ubuntu.

---

### Post by seawolf167 on 2011-08-24
I personally don't like Unity and fall back to "Gnome Classic", so I'm sure there is someone around here that could help you out better than I regarding Unity settings! I guess I'm resistant to change? You might want to mark this thread as solved, then start a new thread with your Unity questions so it gets more views.

---

### Post by debd on 2011-08-24
I think the font dissimilarities you are talking about are same as mine..
I have a Nvidia geforce 7025 card with a monitor supporting 1366x768 res.
but in ubuntu, with the installed graphics driver (either way.. manually or by jockey) the highest res I get that gives me a convincing graphics and readable text display is 1280x800
..but of course the clarity ain't as much as 1366x768.
The nearest possible res in nvidia control options is 1360x768 which gets the display out of the screen. Editing xorg.conf (is it depreciated?) didn't work..

and for your natty needs :) visit this [link]("http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html")..


btw, my installation is 10.10

---

### Post by DaComboMan on 2011-08-24
Thanks guys for your help and tips via different links to keep my interest!

I'm falling back to Classic for now.




BTW, i just read over at [www.askubuntu.com](www.askubuntu.com) (just discovered) that you can't modify that Titlebar. You can fade it out but you can't hide it.

---

### Post by seawolf167 on 2011-08-24
Even though it isn't exactly what you want - at least you found a solution that works

---

