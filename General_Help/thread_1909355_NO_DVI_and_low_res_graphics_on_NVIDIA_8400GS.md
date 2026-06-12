---
title: "NO DVI and low res graphics on NVIDIA 8400GS"
date: 2012-01-15
forum: General Help
---

### Post by stefangr1 on 2012-01-15
A few months ago, I started to experience problems with my monitor. Now and then, the display would not be able to detect the computer again (showing the no source dialog). Rebooting then generally fixed the issue, sometimes not, and sometimes it would work but in a low graphics mode. At some point, this started to worsen (I had already tried a lot of things at that point, see list below), as sometimes even rebooting 10 times wouldn't work. Eventually I connected my display to the VGA port, which worked for about a month, but then it suddenly started to boot in a very low resolution (640x480) that couldn't be changed. At all the time I could ssh into the machine or connect using remote desktop.

I tried the following things to find the defect:
- Reinstall NVIDIA drivers
- Remove NVIDIA drivers
- Install older versions of the NVIDIA driver, from long before my problems first started
- Connect display to other systems (VGA always worked, I did seem to see a few glitches when first connecting to my MBP though after a few seconds it worked fine).
- Try other DVI cable.
- Boot the system using another OS (using a live CD).

During the early stages of the problem, the fact that the problem often went away after a reboot made troubleshooting really difficult. E.g. if you reboot after installing other video drivers you don't know if it works again because of the reboot or because the thing you did fixed it. Particularly the fact that - when using the DVI port - I wouldn't even get the bios screen made me thing that it was a hardware problem.

After I was ordered to buy a new computer, such that peace at home during the christmas break could be restored, and I wouldn't have to sit hours behind my pc in complete frustration to attempt trying fixing it, a few days ago I thought I could give fixing the old computer another try and found a solution.

THE SOLUTION: revert to a very old version of the NVIDIA drivers, version 173.14.31, using the installer that's on the website of NVIDIA.

So we now have a computer running Ubuntu almost anywhere in the house :).

I thought I'd post the solution here, such that other users who might run into something similar may find a solution quicker.

---

