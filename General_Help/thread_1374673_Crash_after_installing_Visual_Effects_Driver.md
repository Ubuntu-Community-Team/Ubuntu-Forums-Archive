---
title: "Crash after installing Visual Effects Driver"
date: 2010-01-07
forum: General Help
---

### Post by rippsnorter on 2010-01-07
I just downloaded and installed the latest version of Ubuntu on my laptop. After installing the drivers for the visual effects I restarted the computer, and now after the all black screen with the little white Ubuntu symbol in the middle the screen goes blank, lots of horizontal lines appear and it contrasts out to a completely blank, white, useless screen. Any suggestions?

EDIT: laptop is a Toshiba 5105, bumped up to 1.2gb of RAM

---

### Post by sanderd17 on 2010-01-07
Do you have an ATI graphical card? did you install proprietary drivers or did you do it via apt-get or synaptic?

If you installed proprietary drivers, the following code helped for me:

```

apt-get update
apt-get install xorg-driver-fglrx
dpkg-reconfigure xserver-xorg

aticonfig --initial -f
reboot

```

---

### Post by rippsnorter on 2010-01-07
No, its not an ATI card. its an NVIDIA GeForce4 440 Go graphics controller; 32MB 220MHz
DDR external video memory. I installed the driver by clicking on the "Extra" visual effects option; it searched for the drivers, found them, installed them, told me to reboot, i rebooted, now it doesnt work.

And there is no way I can enter any codes, as the computer is useless once this happens. and there is no user interface before it happens, just booting. is there any way that i can boot ubuntu in safe mode? that would probably let me in to fix the problem

---

### Post by sanderd17 on 2010-01-07
Can't jou boot into terminal mode?

In grub, select the second option and choose for something like terminal.

---

### Post by rippsnorter on 2010-01-07
ok, so i got it to boot to terminal, and sat here for about an hour goin through different code that i found on google to try, finally one worked:

```
sudo apt-get install nvidia-glx-185 --fix-missing
```that lets me get to the desktop, but its in safe graphics mode. when the prompt comes up telling me this there are 2 errors, one says (EE)Failed to load module "nvidia" (module does not exist), the other says (EE) No drivers availble

I press OK, it gives me 4 options. run in low graphics mode for 1 session, reconfigure graphics, troubleshoot the error, exit to console login. I ran in low graphics mode, went to Hardware Drivers, and tried reinstalling the driver that it has in there, called NVIDIA accelerated graphics driver (version 96) [Recommended]. After that I rebooted, and the crash came back. so, what im thinking is that i need to roll back the driver. is there a way i can do that in ubuntu?

EDIT: Also, if its worth mentioning it says that the driver is proprietary

---

### Post by rippsnorter on 2010-01-08
well ive decided to throw in the towel on this one and just format the hd and reinstall ubuntu. ive only had it on there for about 48 hours, so no big losses. thanks for the help

---

