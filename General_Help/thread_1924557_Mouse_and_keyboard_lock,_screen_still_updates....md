---
title: "Mouse and keyboard lock, screen still updates..."
date: 2012-02-12
forum: General Help
---

### Post by spidey867 on 2012-02-12
My first experience with Ubuntu was awesome. I breathed new life into an old laptop. Several releases later, I experienced a problem where the mouse and keyboard would lock up. Frustrated, I built a new tower a year or two ago to dual-boot Windows 7 and Ubuntu on. The intention was to have Windows on one hard drive and Ubuntu on a second. Everything seemed to go fine during the install, but the problem persisted despite the hardware upgrade.

I eventually gave up and resorted to using only Windows for a while. Recently, I decided to wipe the whole thing and start over, hopefully having the problem get cleaned off after several releases had passed. Unfortunately, after reinstalling Windows today and then using a Live disc to boot into Ubuntu 11.10 for that install, the problem seems to still be alive and well.

So, here's some facts:
- The problem isn't Ubuntu-specific. I've also installed Linux Mint and experienced the same lock-up.
- The mouse and keyboard are both unresponsive during the lock-up, though the screen still updates. The clock will change, and if I were refreshing a webpage when the freeze occurs, the page will still load. Hitting the power button on the tower will bring up a shut down message and it will count down to 0, but when shutting down, it requests that I hit enter after ejecting the Live disc and I'm forced to manually power it down.
- Past research has made me think it is something to do with x.org or my NVIDIA card, though I have no idea what x.org is, so I could be completely wrong.
- I opened a terminal prior to the last freeze occuring and ran dmesg | tail -f based on something I saw in another thread and before the freeze occurred it registered something along the lines of "mouse lost synchronization by 3 frames" or something like that. No message came up after the freeze, but I'm not sure if I had to do anything for another message to show.

If anyone has any insight into this, please help. I'd really like to use Ubuntu again. I'll do any diagnostic procedure or answer any question as soon as possible. Thanks in advance!

---

