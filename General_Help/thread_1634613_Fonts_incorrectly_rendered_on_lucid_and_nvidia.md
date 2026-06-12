---
title: "Fonts incorrectly rendered on lucid and nvidia"
date: 2010-11-30
forum: General Help
---

### Post by drsar on 2010-11-30
Some of my rather useful applications have stopped being useful after a fresh installation of lucid. In particular, the fonts rendered on emacs, openoffice and others look awful to unreadable. Attached is an example screenshot for emacs but it doesn't appear to be application specific. Also, I have a hunch it has to do with my graphics driver
(Linux-x86, Nvidia Driver v195.36.24 ona GeForce 6200 TurboCache).

Any pointers to solving and diagnosing would be much appreciated. Thanks, SAR

---

### Post by drsar on 2010-12-02
Let me answer my own question:
I played a bit more and decided to deinstall the proprietary graphics drivers. (System/Administration/Hardware Drivers)

After a reboot, it all worked and fonts in emacs and openoffice looked fine. At that point the problem was solved and I could have stopped. Having a sense of adventure, I reinstalled the proprietary NVIDIA drivers and things still worked!? 

I have two monitors so I decided to switch the second screen on using twinview. After that, font rendering was buggered as per the original emacs screenshot. However, when using the NVIDIA accelerated graphics drivers and X to drive my two monitors all seems to work including the fonts.

Small downside: When I now go to System/Preferences/Monitors I get a 'Could not get screen information: RANDR extension is not present'. Apparently, this can be solved ([http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1566113](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1566113)) but is of no concern to me at the moment.

---

