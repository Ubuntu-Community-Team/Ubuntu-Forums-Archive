---
title: "1920x1080 on netbook with ubuntu"
date: 2010-07-19
forum: General Help
---

### Post by firefdr on 2010-07-19
Could I connect my netbook to my external monitor with a VGA cable and set the resolution to 1920x1080? Which netbooks support that? How do I do that?
Thanks

---

### Post by lordskid on 2010-07-19
I haven't try but resolutions will depend so much on hardware. You can use

```

*press alt-F2 or open a terminal
gnome-display-properties

```

to configure this. or go to System -> Preferences -> Monitors

---

### Post by firefdr on 2010-07-19
Thanks

Anybody tried this yet?

And uhm, how do I know which computers support that and which dont?

---

### Post by firefdr on 2010-07-19
up

---

### Post by blur xc on 2010-07-19
I manged to do this with my Wife's Dell Mini 10 and the cursed GMA500 graphics chip.  I just plugged it into the Mini's hdmi port, and played around in the display settings unitl it work.  It was a pain, at one point I ended up in low graphics mode, but was able to revert to some settings that worker properly again.  To get the sound to work, I had to screw aorund in the sound preferences dialog as well (and again to get it back to the netbook speakers).

Video playback could have been better.  Playing DVD's with a usb dvd drive resulted in some slight jumping / skipping during playback.

Good luck.
BM

---

### Post by valbaca on 2010-07-19
This has nothing to do with Ubuntu and everything to do with the actual netbook. 
The specifications for particular netbooks are provided by the maker. Any modern computer (netbook or not) supports this output, it really depends on if your **monitor** supports it. If it does, you should be find. 
 
Again, run searches for the specific netbooks you are interested in, probably with "maximum output resolution." Asking for a list of all netbooks that will will get you nowhere.

---

### Post by Mikecore on 2010-10-27
> **valbaca said:**
> This has nothing to do with Ubuntu and everything to do with the actual netbook. 
The specifications for particular netbooks are provided by the maker. Any modern computer (netbook or not) supports this output, it really depends on if your **monitor** supports it. If it does, you should be find. 
 
Again, run searches for the specific netbooks you are interested in, probably with "maximum output resolution." Asking for a list of all netbooks that will will get you nowhere.

Seeing as Ubuntu worked with the OEM netbook manufactures to insure all hardware was supported. And the fact that Xorg doesn't use a config file by default anymore. It seems to me the ball was completely dropped in regards to insuring netbooks could be connected to an external monitor. Funny I hate windows, But guess what? it works with external monitors with no manual configuration.

---

### Post by alanmoore78 on 2010-10-27
I have a low-end full-size Acer Extensa laptop and it has Intel 4500MHD graphics, standard with the GL40 Intel chipset.  I use a 1920x1080 ASUS monitor with it and it's been flawless in Windows 7 and Ubuntu 10.04 and 10.10 but netbooks have much lower spec than this.  I still see no reason it won't work.  You have about half the memory bandwidth and you're DirectX 9.0 instead of 10, but it should be fine.

---

### Post by StephenDavison on 2010-10-27
My netbook has an Intel Atom processor and 945 graphics (VGA D-sub output) It works acceptably with an external monitor, and has no problem detecting and using a 1920x1080 monitor.  

When I was shopping for an external monitor, I took along my netbook and a VGA cable.  I told the salesperson that I wanted to buy a monitor, but wanted to try it out with my netbook before making the expensive purchase.  It was not a problem with the salespeople and turned out to be very helpful in making my decision.

---

