---
title: "Help setting resolution of new monitor."
date: 2011-06-26
forum: General Help
---

### Post by jsel21 on 2011-06-26
I just upgraded from a smaller 1024x768 monitor to a 23" 1920x1080. However in system->preferences->monitors, The highest resolution is still 1024x768. How can I fix this? Thanks.

---

### Post by doas777 on 2011-06-26
what kind of video card do you have and do you have a proprietary driver installed for your vid card? Check the Hardware Drivers applet to see.  both nvidia and ati drivers have a seperate console for settings, so are you using one of those, or the ubuntu  resolution applet?

---

### Post by jsel21 on 2011-06-26
> **doas777 said:**
> what kind of video card do you have and do you have a proprietary driver installed for your vid card? Check the Hardware Drivers applet to see.  both nvidia and ati drivers have a seperate console for settings, so are you using one of those, or the ubuntu  resolution applet?

I fixed it. I booted into windows and set the res there, then booted back into ubuntu and it now works.

I do have a couple questions though. I am using a very old Geforce 6200 PCI card. How is Ubuntu able to get any functionality out of my card if I never installed any drivers in Ubuntu? There is also an Nvidia control panel installed in Ubuntu somehow but I have no idea how it got there without any driver installation. I am also curious why setting the res in windows fixed the problem.

---

### Post by doas777 on 2011-06-26
the vast majority of drivers are part of the linux kernel already. since most device manufacturers do not distribute a linux driver, the community has written their own over the years and included them in the kernel. the folks at cannonical add some additional versions of common drivers that are not in the mainline kernel as well.

most devices are designed to meet certian basic standards for functioning, and there are generic drivers that support these functions. a "generic VGA" driver should work for all video cards, but it only exposes minimal functionality.

there are two primary types of driver code; Opensource drivers that can be shipped with ubuntu/linux and Proprietary drivers, that the user must elect to use, and may have to manually download and install.

the vast majority of your drivers are open, but one item people often use proprietary drivers for is video cards. ATI and Nvidia both have downloadable drivers, and they have both worked with cannonical to provide a means to install tested proprietary drivers on ubuntu systems via the Hardware Drivers applet.

your video card is no longer supported by modern drivers, so you will either have to use the old proprietary driver (1.73 I think?) or 'nv'. that is, if you are not satisfied with your card as is.

---

### Post by jsel21 on 2011-06-27
Very helpful, Thanks.

---

