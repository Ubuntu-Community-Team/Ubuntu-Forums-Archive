---
title: "Nvidia only works until i reboot"
date: 2009-10-19
forum: General Help
---

### Post by Crowder on 2009-10-19
I recently changed from ubuntu 9.04 to kubuntu. I've mostly been pleased witht the differences but have had some stability issues. Most noticeably, my nvidia card seems impossible to maintain functional under kde.

I've searched around a bit and not really found anything about my specific issue, or at least nothing that fixed the problem - and frankly it's over my head. For some reason, every time i reboot I end up in low-graphics mode without my nvidia drivers being detected. If I boot the previous kernel, everything works fine. Through some research Ive found that it's probably due to my drivers/settings being stored in a volatile directory, but how and why did this happen? How can I fix it? 

Please get back to me with any suggestions.

Btw, I'm running the following:
Kubuntu 9.04 (with all recent updates)
Lenovo Thinkpad T61 (6459-CTO)
w/ NVidia Quadro NVS 140m and 180-glx installed (173 didn't work either)

---

### Post by P4man on 2009-10-19
hmm could be an issue with the kernel, or the drivers not being installed properly. Id try rebooting the machine in recovery mode (latest kernel) and from a root shell, remove the nvidia drivers and reinstall them with apt-get.

Either way, ubuntu or kubuntu would make no difference here as they use the same kernels, same X and same drivers.

---

### Post by Crowder on 2009-10-20
> **P4man said:**
> hmm could be an issue with the kernel, or the drivers not being installed properly. Id try rebooting the machine in recovery mode (latest kernel) and from a root shell, remove the nvidia drivers and reinstall them with apt-get.

Either way, ubuntu or kubuntu would make no difference here as they use the same kernels, same X and same drivers.

True. What I should have said was "by the way, I used jockey-kde to install these drivers." That's the only reason it would be important. Either way, can't really go wrong by giving too much information. I've had plenty of times when people give me trouble for leaving things out.

I've already tried re-installing with apt-get, though I'm not sure I was using the most recent kernel. So far my solution has been to always boot into the second option on my list. I've been using ubuntu for a while now, but if you remove me from a graphical desktop environment I'm still useless. I have no idea what to do from the pre-boot command line.

Anyway, it definitely seems to be a kernel issue. I tried a tip that involved adding "nv" to my kernel exclude list or something, to be honest I don't remember exactly (kind of hazy this morning) but it was in the forums and didn't work.

---

### Post by P4man on 2009-10-20
boot in to recovery mode for your most recent kernel. Then select the xfix option, try that first. If that doesnt help, try the root shell and type:

```
sudo apt-get remove nvidia-glx-xxxx
```

replace xxx with your actual driver version, or press TAB to complete the line. now if you blacklisted the nv module last night, you probably want to undo that first because if you remove the binary driver and blacklist the opensource nv driver, then you wont have much left. Im guessing you added a blacklist line  to /etc/modules. To undo that

> gksudo gedit /etc/modules


remove the line, save, reboot, then try the above suggestions.

If that helps booting you into a gui again ( that is painfully slow), then try reinstalling the nvidia drivers through the system > hardware > drivers applet. Or grab newer ones from the nvidia site, though i wouldnt recommend that first.

---

