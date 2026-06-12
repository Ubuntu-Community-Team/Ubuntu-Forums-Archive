---
title: "Desktop performance issue"
date: 2011-05-03
forum: General Help
---

### Post by Ameoba on 2011-05-03
Recently installed Ubuntu 11.04, dual booting on my gaming machine.

After a few minutes of basic window manager and internet use the performance of the machine slows and simple tasks feel sluggish. Dragging windows around or selecting icons on the desktop lag behind the mouse, application take longer to open etc.

According to top, the CPU and RAM are well below max. I manually loaded the latest NVIDIA drivers.

Closing all open applications doesn't help. I found it can be temporarily resolved by logging out, and logging back in, where it will work smoothly for a while before going slow again. :confused:

Is there any known issues or special drivers that may be at fault?

Specs are:
CPU: i7-2600K
RAM: 8GB Corsair
Mobo: ASUS P8P67 EVO
GPU: NVIDIA GTX570

---

### Post by Ameoba on 2011-05-04
tried to time how long it took to run slow this afternoon... and it's not doing it.

I'm not doing anything different, still playing music, browsing the net etc.

Installed and launched Armagetron Advanced (tron like lightcycle game) but performance in the menu was unusable, had to wait seconds for menu item to change.

How can I troubleshoot this?

---

### Post by ChrisWells on 2011-05-04
When I installed the nvidia drivers I couldn't drag windows it was too choppy, and the mouse kept skipping/freezing. It worked fine without the nvidia drivers for me. Not many people seemed to have mentioned it though

---

### Post by Ameoba on 2011-05-04
I uninstalled the drivers briefly while re-installing them. Unity doesn't work without them though. And I'd like to use unity.

---

### Post by Tares on 2011-05-04
It has to probably do something with compiz. Anyway which nvidia driver version did you installed ? Everything works fine here on GTX275 and 270.41.06

---

### Post by Ameoba on 2011-05-04
Yeah, thats the same version I installed.

---

### Post by rwsmith61 on 2011-05-04
This problem does not seem to relate to the actual video drivers. ATI users are reporting similar problems like myself. I have an ATI 4550 card and I am using the latest radeon drivers in Natty 11.04. The problem might be in compiz or the underlying drm.

Can someone else please confirm that the "Effects" tab in the Appearance Preferences has been removed in Natty? I much prefer Classic Gnome and do not plan to ever use Unity (its too limiting for me). Are we supposed to install Compiz Settings Manager manually?

--bs

---

### Post by catalin.soare on 2011-08-24
I am experiencing the same issues as you, it's like after a period of time (and this seems to become shorter) everything seems to simply degrade. It's as if the computer would be sitting in an oven. However, lm-sensors applet states different - about 40+ degrees, which I believe is not a very high temperature. It takes a reboot and this computer starts to run nicely again, but for short time. :(

My setup is (almost the same as Amoeba's):
[MB ASUS P8P67-EVO]("http://www.asus.com/Motherboards/Intel_Socket_1155/P8P67_EVO/")
[CPU INTEL CORE I7 2600K 3.4GHZ]("http://ark.intel.com/Product.aspx?id=52214")
[ASUS NVIDIA GeForce GTX560 1GB DDR5]("http://www.asus.com/Graphics_Cards/NVIDIA_Series/ENGTX560_DC2DI1GD5/")
RAM 8GB Corsair

I have tried Ubuntu 11.04, with the classic interface (no Unity), tried 10.04, and now I'm running 10.10, same problems. Recently I've installed a newer kernel than 10.10 was using, "2.6.37-020637-generic" but nothing new.
I have to mention that to me this seemed like a driver issue, since I've left Windows 7 running on the same computer for whole nights (just to make sure) and performance did not degrade.

Does anyone have any ideas where we could start troubleshooting?

---

### Post by Ameoba on 2011-08-24
If there is one problem that I find annoying, it's apparently random performance issues. This is the kind of issue that keeps my windows install in use (besides gaming)

The issue is definitely not our computers overheating or unable to handle the performance criteria. In windows it can handle Crysis on full detail, so a linux GUI should be no problem.

I'm using the linux install of my dual boot machine less and less with this issue, does anyone have an idea of what to look for?

---

### Post by catalin.soare on 2011-08-25
Hello,
I think I've nailed it.

Yesterday evening I was thinking about updating my EFI/BIOS and downloaded all updates I could find (all the non-betas) and was getting ready to enter BIOS and see what version I was running.

In this mobo's BIOS, in the Advanced mode, and again, on the Advanced tab (or page), you have an option "PCI Express X16_3 slot (black) bandwidth". This option is, by default, set to Auto. If you look in the comment/explanation area, on the right side, you will see what Auto/X4 mode/X1 mode mean. Namely:

```

[Auto]  PCIeX16_3 slot runs at X1 mode for system resource optimization. (PCIeX1_2 will be disabled).
[X4 mode]  PCIeX16_3 slot runs at X4 mode for high performance support. (USB3_34, eSATA ports, PCIeX1_1, PCIeX1_2 will be disabled).
[X1 mode]  PCIeX16_3 slot runs at X1 mode with all slots enabled. (USB3_34 will be disabled).

```

I've set this option to X4 mode, to see what does "high performance" mean, and quickly booted back to Ubuntu. And that was it!
I left the computer on overnight and I can say that the problem is gone. Will have to check when I come back from work too but I, well at least want to, hope that this problem is solved.

Now Amoeba, I really hope you like playing with your BIOS settings too, and I also hope you don't have those slots populated (the ones that can be disabled by modifying this setting).
If this works for you too, we'll drink a beer! :guitar:


Cheers!

---

### Post by Ameoba on 2011-08-26
Going away this weekend, but as soon as I can I'll give this a try and report back!

---

### Post by Duncan Williams on 2011-08-26
check these posts out, they may be of help:

[http://my.opera.com/internetsecurity/forums/topic.dml?id=1073222](http://my.opera.com/internetsecurity/forums/topic.dml?id=1073222)

[http://peppermintos.net/viewtopic.php?f=10&t=3867](http://peppermintos.net/viewtopic.php?f=10&t=3867)

[http://peppermintos.net/viewtopic.php?f=10&t=3733](http://peppermintos.net/viewtopic.php?f=10&t=3733)

---

### Post by Ameoba on 2011-08-30
Thank you catalin.soare, so far so good.

Made the BIOS change as you suggested and while using it last night did not encounter any issues regarding the speed.

If you're ever in Australia, I'll shout you a beer!

---

### Post by catalin.soare on 2011-08-30
Well, as all things eternal this one also lasted.. 3 days! :-)
 Yesterday I was transcoding/compressing a video clip and the "thing" came back.
 I was looking at the sensors' applet in the panel but the temperature  hardly jumped from 38-39 to 45 maybe? Also none of the CPU cores had an  utilization greater than 40%.
I wish I were a HW guru so I could solve and close this thread. Well, I guess my homework isn't done yet.
 I'll keep experimenting and post back if I manage to do something good or maybe blow up my computer. :P


Cheers!

---

