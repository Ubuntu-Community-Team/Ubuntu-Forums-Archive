---
title: "OS-uninstaller"
date: 2012-05-06
forum: General Help
---

### Post by acutu on 2012-05-06
I had Ubuntu 10 happily installed on my second laptop but it is unsupported now so time to upgrade to the new long release 12 or so I thought. Not as smooth as expected: I burnt 12 onto disk - that was easy. Started the new install, the upgrade option was not available so had to install alongside 10. Seemed to work. Later I thought it would be a good idea to update the Nvidia driver from the Ubuntu settings. Chose the recommended option rather than latest version. That messed things up, got a blank colourful desktop with nothing to click on. Tried various tips online but no success so decided to reinstall. Same thing happened again, even without selecting Nvidia driver. Tried again, this time selecting latest Nvidia driver. Still no joy. By now I am frustrated because I just want to go back to using Ubuntu 10 and having that load automatically but now it is 4th on the list so I want to uninstall the v12 failures. I try downloading the OS-Uninstaller but can't get it to work either from within Ubuntu or from disk I burned. I've wasted an afternoon and evening on this so far, expected a one hour upgrade, but has gone seriously wrong. A disappointing start to Ubuntu 12, I think it is still a lot easier to use Windows systems despite their own imperfections.

---

### Post by Docaltmed on 2012-05-06
There is a problem with the 295.40 Nvidia drivers, which has been messing a lot of people up. Some people have found success with rolling back to .33 or earlier drivers.

If you go to the Nvidia website, it gives you instructions on how to uninstall a driver and re-install the previous one. I had problems with that because I couldn't even get a terminal or CLI running -- all I had was black screen.

I finally whipped that problem by logging onto the crumped computer via SSH and doing everything remotely. Not fun.

---

### Post by drs305 on 2012-05-06
Have you tried editing the Grub menu during boot and adding the 'nomodeset' option on the 'linux' line? That might allow you to get to the desktop and install/uninstall the video drivers.

If you don't find one of the posts on how to do this (there are quite a few) here on the UF and want to try it let us know.

---

