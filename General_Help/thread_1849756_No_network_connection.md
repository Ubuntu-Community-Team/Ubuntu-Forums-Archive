---
title: "No network connection"
date: 2011-09-25
forum: General Help
---

### Post by kullerhamPster on 2011-09-25
Hi there :)

I'm currently running the 11.10 beta on my notebook, which worked fine so far, apart from some minor glitches.
But when I booted the system today, I noticed that I had no internet connection, there also was no Wifi-symbol in the status bar at the top of the screen.
I first thought this might be some driver problem caused by a recent update and tried to use my old USB Wifi stick instead - without success, not even the LED on the stick started to blink...
So I plugged in an ethernet cable, but even that showed no effect.

ifconfig shows no interfaces apart from "lo". Booting older kernel versions also didn't change anything, so this doesn't seem to be a driver issue. Perhaps some system service/daemon doesn't start up correctly or crashes?!

Any ideas what might be going on here and how I could make my network connection work again?

EDIT: Just found this bug report here, which seems to describe the same problem:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/856101](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/856101)

I'll have to see if the described workaround works for me...

---

### Post by dcstar on 2011-09-25
> **kullerhamPster said:**
> Hi there :)

I'm currently running the 11.10 beta on my notebook, which worked fine so far, apart from some minor glitches.
.........

11.10 is still in Beta, so there is **NO support for pre-release versions** in any forum except the development forum.

---

