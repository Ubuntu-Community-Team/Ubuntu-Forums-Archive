---
title: "Fail shutdown with ups low battery"
date: 2010-01-24
forum: General Help
---

### Post by ardvark on 2010-01-24
I recently purchased a UPS (Tripp-lite Internet 550U)to shutdown my PC during a power outage when unattended. This model of UPS is connected to the PC with USB. Upon plugging in the UPS USB cable the Gnome Power Manager started up and it appears to correctly show the condition of the UPS. During a power outage it showed battery discharge right down to the battery going critical, but never shutdown the PC. I have set the options in the power manager for low & critical battery shutdow. Seems something is blocking the Gnome Power Manager from shutting down, but I have no idea where to start looking..

PC: Abit mobo with Phoenix bios
Ubuntu 8.04
UPS: Trtipp-Lite Internet 550U

---

### Post by tgalati4 on 2010-01-24
Could be a permissions problem.  What user is the Gnome Power Manager running as?  Usually root access is needed to shut down a machine.  My experience is with apcupsd and it runs as a daemon and has saved my machines several times.

If Gnome Power Manager is running as something other than root, then you need to give shutdown privileges to that user.

Also check the last few entries of dmesg:

dmesg | tail -50

One other thing to check:  Don't run your batteries too low.  Your Triplite may be shutting down first before the power manager has a chance to send the signal.  You don't want to go below 30%.  You also don't want to overload your wattage capacity--if you have a 1000VA ups, don't load more than 800VA to account for battery and mosfet aging.

My experience with ups ratings is that the sticker rating is the "meltdown" rating.  Also, stick with metal-case ups's.  The plastic ones tend to melt and catch fire.  Not good if you are not home.  Your computer shuts down OK, but then your house burns down.

---

### Post by ardvark on 2010-01-24
Thanks for the quick reply. I guess my first question is how do you tell what a process is running as? Since I didn't load Gnome Power Manager, it just started up when I plugged in the UPS. I took a quick look at dmesg, the only thing I saw was where it recognized the UPS on the USB bus.

Oh,sorry, I think I answered the first part. If I did this right, even though the executable is owned by root, the process is running under my user. Where would I be set for shutdown privileges? Shouldn't I have that already?

---

### Post by tgalati4 on 2010-01-25
sudo shutdown -h now

Remove the sudo and see what happens.

---

### Post by ardvark on 2010-01-25
Ah yes, says I need to be root. So, I need permission to shutdown or Gnome Power Manager should be running under root. You would think that this type of program should be under root, this is one of the main things I just don't understand about Linux. What would be the easiest way to fix this?

---

### Post by tgalati4 on 2010-01-25
To improve security, the trend is to run few services as root.  So you can add shutdown privileges to your user account.  Search the forums for how to add that specific permission.

---

