---
title: "Problem with nvidia 9600gt : resolution stuck on 640x480 with proprietary drivers"
date: 2010-10-20
forum: General Help
---

### Post by djiock on 2010-10-20
Hello

I have a BIG issue with my fresh Maverick install : when I install proprietary drivers via the graphic utility, either one proposed, the screen resolution is then max in 640x480. But I have hardware acceleration and compiz effects !

I tried, I think, everything. Forcing the resolution in xorg, in monitors.xml, try the newest ones via the ppa, install an older (and used to be working I'm positive) one with .run (which just prevent any graphic display)... I'm stuck.

And it's working fine under windows.

Thanks in advance !

---

### Post by Jebtrix on 2010-10-20
Try
```
sudo nvidia-xconfig
```
then reboot

---

### Post by djiock on 2010-10-21
That did write a new xorg.conf, but didn't change anything...

Tell me if you need any log file.

---

### Post by djiock on 2010-10-22
Still stuck in 640...

Actually it happened first under Lucid right after an electricity line cut, when I booted I was stuck in that resolution, so I decided it was time to install Maverick.

But with this fresh install, same problem. Plus ! I now need to put "nomodeset" option with the live cd/usb to get a display. With lucid as well, which was not the case before.

So I guess there is something wrong with my graphic card... But before I change it, given the fact it's working fine under windows, it should be the same with linux ! There must be a way to get a higher resolution, after all I *have * hardware acceleration !

---

### Post by djiock on 2010-10-23
I tried
```
sudo nvidia-xconfig --add-argb-glx-visuals --depth=24 --no-logo --mode=1650x1050
```

But it didn't change anything but the xorg.conf...

There MUST be a way !

---

### Post by Jebtrix on 2010-10-23
Check out

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by djiock on 2010-10-24
I tried everything in this page, nothing works.

By putting "cvt 1680 1050 60" I get
```
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
```

but when I try to add it
```
xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
```

I get the error "xrandr: Failed to get size of gamma for output default
"

same thing as root...


Starting to desperate here, my next card will be an ati. That's just too bad I can't get what I have with windows, even if it's buggy, but I know it's NVIDIA's fault

---

### Post by Jebtrix on 2010-10-24
This one is tough. I have a 9600GT at work running 10.10 64bit fine but not all are made the same. Manufacturers can either use the nvidia reference design or not. Did you try an older nvidia driver? Despite this problem jumping ship to ATI will not make you happier, imho. A newer nvidia will still be your best bet in linux land.

There is some modelines you can add to the nvidia device in xorg.conf to see if any help:

Option "ModeValidation" "AllowNon60HzDFPModes"
Option "ModeValidation" "NoMaxPClkCheck"
Option "ModeValidation" "NoEdidMaxPClkCheck"
Option "ModeValidation" "AllowInterlacedModes"
Option "ModeValidation" "NoMaxSizeCheck"
Option "ModeValidation" "NoHorizSyncCheck"
Option "ModeValidation" "NoVertRefreshCheck"
Option "ModeValidation" "NoWidthAlignmentCheck"
Option "ModeValidation" "NoDFPNativeResolutionCheck"
Option "ModeValidation" "NoVirtualSizeCheck"

---

### Post by djiock on 2010-10-25
Thank you very much for trying, but this doesn't work either.

I tried an older driver before, without any result, but the fact I can no longer boot on live CD makes me say that my card is done for...

Just, it's still breathing under windows... If you think of anything else, let me know.


I saw some good test on newest ati card, at least the free driver is providing 3D.

---

### Post by BobbyJoe on 2011-01-31
Have you found any fixes for this yet? I have a computer running OpenSuSE 11.2 that had this issue for a few days, after which it went away on its own. However, it did it again last night and I can't figure out how to fix it (as was the case last time). I've tried manually entering the resolution into /etc/X11/xorg.conf (last time, too) and updating the NVidia driver.

---

### Post by djiock on 2011-02-01
Actually I did fix it, but miraculously... I wanted to test the card on another motherboard in another PC, so I removed it... And never did test.
The card was not in any computer for a couple of week (I was away) and when I came back I put it back in my PC and... it worked !! :neutral:

Yes nothing more, I got my resolution back. Just like that. Yes. WTF.

Since then I got an ATI for Xmas and no more graphics problems in Windows (crashes, BSOD, windows' problems resolution crying every day), so obviously my card was defective. Sorry, but it may be the case with yours...

cheers

---

### Post by BobbyJoe on 2011-02-01
The first situation is basically what happened the first time.

Fortunately I think I found the solution to my problem: a flaky DVI to VGA adapter. I replaced it with a DVI cable and not only did the problem go away but a slight overscan problem with the terminal was fixed.

---

