---
title: "Kubuntu laggs"
date: 2011-09-25
forum: General Help
---

### Post by Vasar on 2011-09-25
I have computer with 3.1 gHz CPU, ATI radeon 4850 HDMI GPU, 4GB DDR2 RAM. Okay it's bit outdated, but it shouldn't lagg, Windows 7 runs smoothly. I installed GPU driver, but it still laggs. 

I can't find anything useful in Google on this.

---

### Post by oldos2er on 2011-09-25
Here are some suggestions on how to speed up Kubuntu:

[http://www.numango.com/5527_simple-tips-speeding-kde-kubuntu.html](http://www.numango.com/5527_simple-tips-speeding-kde-kubuntu.html)

---

### Post by Vasar on 2011-09-25
So it's normal that my computer laggs with new KDE? I was hoping there's newer driver or something. :/

Damn I like KDE's new appearance. ( Last time I used KDE 3.6 )

---

### Post by oldos2er on 2011-09-25
It could be because of your video card, but I don't really know.

---

### Post by SecretCode on 2011-09-25
You probably need the proprietary driver for your ATI video card.

---

### Post by Vasar on 2011-09-25
[http://ubuntuforums.org/showthread.php?t=1141238](http://ubuntuforums.org/showthread.php?t=1141238)

I think he has similar problem, but no solution. 

Opening new browser tab, nothing else running in the computer, generates lagg and drives CPU over 70%. I installed latest video driver from AMD, but that didn't help at all. Could the problem be with CPU?

---

### Post by Vasar on 2011-09-25
> **SecretCode said:**
> You probably need the proprietary driver for your ATI video card.

I had that, but I just uninstalled it to install latest driver from AMD, nothing changed...

Sorry for double post.

**EDIT: ** Suspending all the desktop effects has no improvement on performance.

---

### Post by ankspo71 on 2011-09-27
Hi,
> So it's normal that my computer laggs with new KDE?
To me that isn't normal. I think your computer should be able to run Kubuntu comfortably. The computer I'm using now is an older 1.6ghz AMD (single core), 1.5gb memory, with Nvidia 6100 128mb graphics and it is running Kubuntu as good as expected, and even noticeably better after I tweaked the KDE settings like the settings in the link above that oldos2er posted.

Open your terminal (Konsole) and type in the command 'top', then press enter. Use top to see if you can narrow down any processes that cause the CPU to reach 70%. Even 10% is too high if your computer is idle.

It might be a process that can be turned off like... kio-thumbnail (file/folder previews), nepomuk/strigi/akonadi (semantic desktop search), knotify4 (system audio notifications), or krunner (the kde run dialog, by disabling krunner plugins), etc. 

High CPU usage with kwin (the KDE window manager that handles desktop effects) and xorg (the display server) are usually graphics driver related problems. 

If you can pinpoint some processes causing the high CPU usage, report back here and see if one of us knows what to do.

Hope this helps.

---

### Post by realzippy on 2011-09-27
> **ankspo71 said:**
> 
The computer I'm using now is an older 1.6ghz AMD (single core), 1.5gb memory, with Nvidia 6100 128mb graphics and it is running Kubuntu as good as expected, 
You use nvidia drivers.
...the ATI proprietary driver isn't that good.

---

