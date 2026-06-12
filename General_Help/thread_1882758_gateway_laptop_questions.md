---
title: "gateway laptop questions"
date: 2011-11-17
forum: General Help
---

### Post by thatstrangeguy on 2011-11-17
I have the opportunity to get a Gateway M285-E Laptop Notebook Convertible Tablet PC Core Duo Intel Video as seen here for pretty cheap now i am going to up grade the ram and a few other things. pretty much modernize it for use today. Any way it comes with a Gateway M285 285-E Tablet Laptop Stylus Pen to make the tablet part of it all work. now i know that in windows you need the drivers for the pen and its systems to make it work as a tablet. now dose any one out there have or have hear of another person trying to use Ubuntu on a system like this is already available for Ubuntu. if not would i be able to install the drivers in question in wine to make the whole thing work in wine standers or m i a hopeless dreamer lol just kidding let me know thoughts comments questions let me know thank you

---

### Post by thatstrangeguy on 2011-11-17
I just double cheacked on dell driver sight thy have drivers for xp and vist thats all there as a up date fyi

---

### Post by thatstrangeguy on 2011-11-19
wow no one has attempted it ill try on some other linux forums

---

### Post by Favux on 2011-11-19
Hi thatstrangeguy,

I believe we've gotten the Gateway M285-E tablet PC's Finepoint digitizer working using the fpit X driver and a xorg.conf in Lucid.  Or at least a similar model.  As long as the battery in the stylus is good.  I think the driver in the repository was used.

Despite there finally being a new release of the fpit driver:  [http://cgit.freedesktop.org/xorg/driver/xf86-input-fpit/](http://cgit.freedesktop.org/xorg/driver/xf86-input-fpit/)  we weren't able to get it working in Natty with a fpit.conf in xorg.conf.d or a xorg.conf.  But I notice there have been several commits that may have fixed the issue.  I did contact Peter Hutterer with proposed fpit.conf's for non-Fujitsu Finepoint digizers and told him the driver wasn't working for them, so that may be reflected in the commits.  But no maintenance of the driver was declared on 9-27-11.  So this is it unless users are willing to maintain the code themselves.

---

