---
title: "Installation broken after trying to install proprietary GPU driver"
date: 2011-07-19
forum: General Help
---

### Post by am6465 on 2011-07-19
My laptop runs really hot and after reading a few threads around the forum I came across one that said it was because of the fact that ubuntu comes with an open source driver. All you have to do is update to the proprietary driver and everything is fixed. So I went to the menu and looked for the driver. I honestly didn't check if the one that was found was compatible with my graphics card, I just assumed that the one that it found was the right one. I installed it and restarted and ubuntu wouldn't load. It goes through the initial load but when it comes time to bring up the login page, it stays black and never advances. 

I assumed that this was a result of an incorrect driver. Again, I turned to the forums and found that other people had this problem. So I grabbed my trusty live CD and tried to load up a live session and remove the config file that points to the driver ([http://ubuntuforums.org/showthread.php?t=1422660](http://ubuntuforums.org/showthread.php?t=1422660)). 

The live CD wouldn't load. Same thing for recovery mode. It gets to a certain point and stops. This link is an image to where the boot stops: [http://dl.dropbox.com/u/5952515/IMAG0338.jpg](http://dl.dropbox.com/u/5952515/IMAG0338.jpg)

I'm not really sure where to proceed. Any help?

Other info:
My window's partition works just fine.
I have a Mobile Intel(R) 4 Series Express Chipset

---

### Post by dino99 on 2011-07-19
its a known issue with some chipsets. It is a kernel trouble, the last one working is 2.6.35, the newest have this temp problem. You dont tell which card/driver is installed, so cant speak a lot, but "nouveau" runs better than "nvidia" for example (xserver-xorg-video-....)

---

### Post by am6465 on 2011-07-19
I can't get into the ubuntu partition so I can't tell you exactly what I installed there. Under the device manager->Display Adapters all it says is Mobile Intel(R) 4 Series Express Chipset Family. 

Here is a screenshot of the device manager and driver info screen.
[http://dl.dropbox.com/u/5952515/chipset-driver.JPG](http://dl.dropbox.com/u/5952515/chipset-driver.JPG)

---

### Post by am6465 on 2011-07-25
Anybody have an idea?

---

