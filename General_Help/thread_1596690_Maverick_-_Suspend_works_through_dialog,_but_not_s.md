---
title: "Maverick - Suspend works through dialog, but not shortcut"
date: 2010-10-14
forum: General Help
---

### Post by ssj71 on 2010-10-14
I was having issues with karmic on my Lenovo T400 so I wiped the drive and installed maverick from CD yesterday. I made some tweaks ([COLOR=Blue][trackpoint scrolling]("http://psung.blogspot.com/2010/04/thinkpad-trackpoint-scrolling-in-ubuntu.html")[/COLOR]) and found suspend didn't work any longer. I used the solution from [COLOR=Navy][this thread]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9966400")[/COLOR] to get it working intermittently. 

After some testing I found that I can always suspend using the shutdown dialog in the menu. It works every time, but my shortcut button (fn+F4) will work once or twice after booting, but inevitably after a few times suspending and resuming the system hangs while suspending and the indicator blinks. It often hangs on the "checking battery status" part on the process, but not always. I also found I can suspend fine using  "sudo acpitool -s" in the terminal (after installing the acpitool package, naturally). I had tried laptop-mode-tools without success so I went back to acpi-support.

In a nutshell my question is: what is the difference between my shortcut button and the shutdown dialog? Or where can I find what scripts these run?

---

### Post by ssj71 on 2010-10-16
Ok, here's a follow up for completeness.

I messed up my hard drive somehow with Grsync so I formatted and started over. I discovered that it was my trackpoint scrolling enable code that was somehow getting in the way of suspend, so I deleted the file I'd created and instead added the code

```

Section "InputClass"
     Identifier    "Trackpoint Wheel Emulation"
     MatchProduct    "TPPS/2 IBM TrackPoint|DualPoint Stick|Synaptics Inc. Composite TouchPad / TrackPoint|ThinkPad USB Keyboard with TrackPoint|USB Trackpoint pointing device|Composite TouchPad / TrackPoint"
     MatchDevicePath    "/dev/input/event*"
     Option        "EmulateWheel"        "true"
     Option        "EmulateWheelButton"    "2"
     Option        "Emulate3Buttons"    "false"
     Option        "XAxisMapping"        "6 7"
     Option        "YAxisMapping"        "4 5"
EndSection 
```to the end of the file usr/share/X11/xorg.conf.d/50-synaptics.conf

and it *SEEMS* to be working. It sometimes takes a minute, but it does suspend and the trackpoint scrolling works after resuming. So I'm happy.
Hope this helps someone.

---

### Post by ssj71 on 2010-11-09
Well, this fix helped, but it still hangs once in a while when trying to suspend. I always use the shortcut. I'd guess it hangs maybe once every 10 times.

---

