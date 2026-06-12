---
title: "video tearing in compiz and video playback with ATI HD 5700"
date: 2010-07-01
forum: General Help
---

### Post by darthpenguin on 2010-07-01
OK. This is starting to grind my gears. I am running Ubuntu 10.04 and have an ATI HD 5700 video card. I have video tearing issues whether I'm watching a video or dragging windows across my screens or whatever. I have looked over many forums and tweaked many settings in CCSM and AMDCCC in an attempt to fix this. I have changed refresh rates of the monitors and compiz and enabled vsync where possible to no avail. I swapped out my ATI card for an nVidia 7300 se and installed the proprietary nVidia drivers, just as a test, and everything was super smooth; no video tearing. Of course the nVidia doesn't support 2 screens (;_;). I have read that others have had issues with ati on Linux but I can't find a solution. I have heard that the open source ati driver works better than the ati's proprietary one but I have no idea if my card is supported by the open source driver or how to install it. (unless "open source driver" means the default video driver in Ubuntu in which case something is obviously wrong because I can't run compiz or multiple screens on that driver). Is this video tearing truly a driver issue? Is there any way to get my card to work smoothly? or should I just buy a second nVidia card for my other screen? (my MB has 3 PCIe expansion slots) If this is an issue with ATI's driver they should really get their act together.

Any input or help is appreciated. thank you.

---

### Post by emergence on 2010-07-01
I posted this today:
[http://www.phoronix.com/forums/showthread.php?t=24494](http://www.phoronix.com/forums/showthread.php?t=24494)

---

### Post by darthpenguin on 2010-07-02
> I posted this today:
[http://www.phoronix.com/forums/showthread.php?t=24494](http://www.phoronix.com/forums/showthread.php?t=24494)

Sorry to hear you have been having the same issues. It really is a very annoying problem. I have installed my GeForce 7200 and am just using one screen for now. I am just going to pick up a cheap nVidia card tomorrow for my other screen. I just need to run compiz and watch video anyway. It's not like Linux supports high end gaming. I have a Windows PC that can use the expensive ATI HD 5700.

I will leave this thread open in case someone has any more information on getting ATI to play nice with Linux. Until then you (and anyone else reading this) may want to just pick up an nVidia card as well.

ATI :x

---

### Post by darthpenguin on 2010-07-02
OK, maybe I should open a new thread for this but... I got another nvidia card from a friend so I can run a dual head setup with no video tearing. When I plugged it in I got no video at all on my second monitor. I thought it was a MB issue or a bad video card but then I booted into Windows (yes i still keep a Windows partition, so sue me) and I found that all i needed to do was install the drivers and I got both monitors working. (Windows 7 may be but ugly but it works). So how can I get the second display to work in Ubuntu? the "Detect Displays" button in nvidia-settings does nothing (no displays detected - no error message).

---

