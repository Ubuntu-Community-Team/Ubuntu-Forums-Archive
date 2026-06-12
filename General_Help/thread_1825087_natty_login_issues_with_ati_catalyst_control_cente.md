---
title: "natty login issues with ati catalyst control center"
date: 2011-08-14
forum: General Help
---

### Post by airthimble on 2011-08-14
I did a quick search to see if this has been talked about, was unable to find anything.

I just did a fresh install of natty, installed a few programs along with the ati catalyst control center.

I am having serious login issues, here is what I do:

I am at the login screen right from start-up,
type in username and passward and hit enter,
screen goes blank, it appears I am logging in, ubuntu plays a sound and puts me back at the login screen.
I do not get an "Authentication Failed" error like I would expect.
Unable to login as myself or as root.

However, I am able to login if I select the "safe mode," I am not able to login under the normal mode or the ubuntu classic modes.

I suspect that this issue has to do with the ati proprietary drivers, after playing with the settings for a while in safe mode I am now able to login to the normal natty mode without any apparent issues.

Here is what I changed in ati catalyst control center to boot into natty mode:
I disabled the Xinerama and Tear Free options.
Under the 3D settings, I selected the "override application setting" for all the 3D settings I could.

I believe I still have some display issues as I am unable to drag windows from one display to another, my mouse is able to move just fine across displays though.

Oh, this is my first post as well, Thanks!

EDIT: I also found that enabling Xinerama prevented me from logging into the ubuntu and ubuntu classic modes, but I was able to login to the ubuntu with no effects mode.

---

### Post by WyleECoyote on 2011-08-14
I had this same problem, do not remember the exact fix but did you try this yet:

```
sudo aticonfig --initial
```

---

### Post by airthimble on 2011-08-14
I checked and saw that natty wasn't completely up to date, was able to update everything.

restarted and now I am unable to login in any mode.

I switched to the console(ctrl+alt+F1) and was able to login to that, I gave the 'aticonfig --initial' a shot and it came back with :

Found fglrx primary device section
Fail to link to fglrx-libglx.so, please check whether the driver is installed correctly

I suppose that it appears I'm missing a fglrx library, the ati driver must have gotten installed incorrectly.

I will try to uninstall and reinstall the latest ati driver to see what happens.

---

### Post by airthimble on 2011-08-14
Alright looks like we are now in business. I thought I would follow up with what I did in case someone else has a similar problem.

I did a fresh install of natty, chose the option to download updates as it is installing.

Went and installed the AMD-APP SDK.
Installed the ATI drivers through the Aplications->AdditionDrivers instead of a download/install.
Rebooted.

In the ati catalyst control center I went with the "Multi-display desktop with display(s) 2", Xinerama disabled and Tear-Free enabled.

Works well so I will leave it for now.

---

