---
title: "Can't reach 1680x1050 res"
date: 2010-04-30
forum: General Help
---

### Post by mankanit on 2010-04-30
Intel motherboard DG33TL, chipset G33. I use the on-board graphics. The display is an Fujitsu-Siemens 22" with 1680x1050 res. The latest four versions including 10.04 of Ubuntu selects wrong resolution at boot up, 1024x768. There is no option for higher res. It should be 1680x1050 and I can't change it. Have not found a solution. It works on other quite modern motherboards, but just NOT DG33TL.
Please give me advices.

Magnus

---

### Post by dino99 on 2010-04-30
lucid dont need xorg.conf so remove it:

sudo rm -f /etc/X11/xorg.conf

then 

sudo dpkg-reconfigure jockey-gtk

---

### Post by mankanit on 2010-04-30
Thanks for the suggestion. 
I tried it and rebooted. 
But there is still no difference. Resolution is max 1024x768.
Should I add something to Your suggestion?

Magnus

---

### Post by dino99 on 2010-04-30
seem that devs are working on some issues with G33

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/504548](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/504548)

" We hear from upstream that a number of bugs (possibly including
this one) have been fixed in the newer DRM code from the 2.6.33 kernel.
I don't know if your bug is one of the ones fixed in this release,
though, but we've prepared a PPA with this DRM update. Would you mind
installing this, rebooting, and testing if the original issue can be
reproduced with it or not?

The DRM PPA is here:

    [https://edge.launchpad.net/~apw/+archive/red](https://edge.launchpad.net/~apw/+archive/red) "

---

### Post by dino99 on 2010-04-30
looking at [https://edge.launchpad.net/~apw/+archive/red](https://edge.launchpad.net/~apw/+archive/red)

i can see yet this new package, so have to wait a few days i guess, or try with the latest kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

---

### Post by mankanit on 2010-04-30
I installed:
linux-image-2.6.34-999-generic_2.6.34-999.201004301209_i386.deb
and restarted.

No change. Do You think I should wait for the next kernel?

---

