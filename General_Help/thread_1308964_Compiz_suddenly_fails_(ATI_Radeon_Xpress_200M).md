---
title: "Compiz suddenly fails (ATI Radeon Xpress 200M)"
date: 2009-11-01
forum: General Help
---

### Post by Altay_H on 2009-11-01
I recently did a fresh install of Ubuntu 9.10 (Karmic Koala) on my computer, and Compiz was enabled by default and working correctly. I wasn't using any proprietary drivers. I unsuccessfully tried to update my graphics card drivers, which didn't end up changing anything. I added fglrx-amdcccle and all of its dependencies, but it wouldn't run. It quit with an error telling me that it didn't detect an ATI graphics card and that I should run aticonfig.

Anyway, I noticed that Compiz had been disabled, and attempting to re-enable it lead to a "desktop effects could not be enabled" error. Running compiz from the terminal returns:
```
$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity
```

I tried removing fglrx-amdcccle, but that didn't change anything. Any ideas? Thanks in advance for any help.

---

### Post by lavinog on 2009-11-01
fglrx dropped support for radeon 200m back in march 09.

You should be using the open source radeon driver.

I haven't updated my laptop to karmic yet, but compiz was working with the radeon driver in jaunty. (it also has a 200m)

post your xorg.conf

you might want to try making a backup of xorg.conf, then removing it, and let xorg auto configure your display.

---

### Post by ublintu on 2009-11-01
I have 200m card and the open source driver is working 4 me in karmic. [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)  (I didn`t configure X.org and below it........, Am I need to?) and compiz is working.

---

### Post by Altay_H on 2009-11-01
Thanks for all the help!

I was fairly certain I forgot to remove some fglrx-related package, so I booted into the Live CD (which was able to use compiz) and checked to see which packages it had installed. It turned out all I needed to do was remove the packages "xorg-driver-fglrx" and "fglrx-kernel-source" and restart X. Everything is working smoothly now. Thanks again.

---

### Post by jsampaio57 on 2009-11-03
I had the same problem with my old Toshiba Satellite M 70 (Radeon Xpress 200M) I solved the problem with the following:

1: remove xorg-driver-fglrx if installed (complete removal)
2: remove fglrx-amdccale if installed (complete removal) 
3: copy xorg.conf
(ok, go to terminal, then cd /etc/X11 , then sudo cp xorg.conf xorg.MyCopy)
if things go wrong later, restart with recovery, login, and copy back into xorg.conf)

3 and then simply DELETE xorg.conf (ok, sudo rm /etc/X11/xorg.conf)

After this, I get my laptop working with the ati driver. To check, I type:

lspci | grep VGA 

and I get

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

and everything runs fine. I have the old 1440x800 resolution that I used to have with 9.04

Cheers...

---

### Post by jsampaio57 on 2009-11-03
... I meant, 1280x800

---

### Post by peakpc on 2009-11-07
I have a laptop (Compaq V5000) with a ATI xpress 200m. I did not upgrade but, started fresh 32bit... video does work with kernel 2.6.31-14, even Compiz and video seem to run smoother than in 9.04 however the kernel mode-setting ATI drivers seem to be still a work in progress as if I switch users, suspend or hibernate it resumes to a black (blank) screen with no recourse but to reset.  Has anyone had success with this? I hope that there is enough of us complaining to make this a priority to fix soon.

---

### Post by lavinog on 2009-11-07
I recall an issue way back that to fix the suspend issue, gdm had to be restarted...now that 9.10 is using a different login manager, I wonder if that issue came back.

---

### Post by Altay_H on 2009-11-08
> **peakpc said:**
> I hope that there is enough of us complaining to make this a priority to fix soon.
There is a lot of complaining about suspend resuming to a black screen on [this thread]("http://ubuntuforums.org/showthread.php?t=1307618"). I suspect there are multiple different issues there, but at least some of them involve ATI graphics cards and are likely to be complaining about this particular issue.

---

### Post by nardis_Miles1 on 2009-12-06
> **jsampaio57 said:**
> I had the same problem with my old Toshiba Satellite M 70 (Radeon Xpress 200M) I solved the problem with the following:

1: remove xorg-driver-fglrx if installed (complete removal)
2: remove fglrx-amdccale if installed (complete removal) 
3: copy xorg.conf
(ok, go to terminal, then cd /etc/X11 , then sudo cp xorg.conf xorg.MyCopy)
if things go wrong later, restart with recovery, login, and copy back into xorg.conf)

3 and then simply DELETE xorg.conf (ok, sudo rm /etc/X11/xorg.conf)

After this, I get my laptop working with the ati driver. To check, I type:

lspci | grep VGA 

and I get

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

and everything runs fine. I have the old 1440x800 resolution that I used to have with 9.04

Cheers...

I am running jaunty 9.04 and I have been running the free radeon driver (with direct rendering). However, because the 3-d acceleration is almost non-existent at this point, I attempted to build the AMD 9.3 driver for jaunty. It did build and install, but it also gave the incorrect xorg version. Removing the proprietary driver was stupidly problematic. I had done all of the --purging of packages. However, I had copied the fglrx.ko directly into the /video directory in the appropriate kernel tree. Without an xorg.conf file, the system actually loaded this flawed module! I only mention this as a cautionary story. The open source driver is quite adequate for viewing movies, and even for running compiz. However, for real 3-d applications, and I'm not talking about games, it's virtually dead in the water. I thank the group working on the open driver because what works, works very well. I also wish them the best of luck in wringing the best 3-d performance out of the Xpress 200M chip set.

---

