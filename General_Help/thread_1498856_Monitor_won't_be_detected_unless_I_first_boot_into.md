---
title: "Monitor won't be detected unless I first boot into windows"
date: 2010-06-01
forum: General Help
---

### Post by felixtheratruns on 2010-06-01
So I have a Samsung monitor at work (model 2343BWX) that I use in addition to my laptop screen. My computer is a T500 think pad. When I boot into ubuntu 10.04 from previously shutting down the computer in ubuntu I can't detect the monitor. If I however boot first into windows (I don't even have to enter my password, I can just press shutdown on the menu instead of logging in, and then boot into ubuntu) and it auto detects the monitor. 

I have tried going to System -> Preferences Monitors and clicking "Detect Monitors" it doesn't work. Anyone know how this could be? Thanks.

---

### Post by dino99 on 2010-06-01
check "system admin hardware driver": is it activated ?

[http://incise.org/samsung-2343bwx-xorg-config.html](http://incise.org/samsung-2343bwx-xorg-config.html)

found this comment:

The T500 has two graphics cards. Try disabling the automatic switching in the BIOS:

press the blue button while startup>F1>Display - there you will have to change two settings (don't have a T500 here, so I don't know the exact names, but it's described on the settings page of the BIOS), one that switches the graphics card (set to the one you want to use) and one that tries to detect your OS (disable that one).

---

### Post by felixtheratruns on 2010-06-02
>check "system admin hardware driver": is it activated ?
When I activated it it caused ubuntu to not start up at all. But then when I tried to booting first into windows I was able to shutdown and start up in ubuntu and deactivate it.

>The T500 has two graphics cards. Try disabling the automatic switching  in the BIOS:
I fooled around with several different bios settings. I finally noticed that "switchable graphics" was enabled and that this was only supposed to be enabled under windows vista and if the proper drivers were installed. (this was probably what fixed it) However, I changed a few other settings., here's all of them
1 I set the default graphics card to "PCI express" (it was previously internal)
2 I set the default display device to something like "analogue vga" (it was previously LCD)
3 I disabled OS detection for switchable graphics mode
4 As I already mentioned I changed the graphics mode to "discrete graphics" (it was previously switchable)

Sorry that I didn't narrow things down more because I have to get back to work. Although I think it was just that I disabled switchable graphics. It works now; I can boot straight into ubuntu and use both monitors, thanks.

---

