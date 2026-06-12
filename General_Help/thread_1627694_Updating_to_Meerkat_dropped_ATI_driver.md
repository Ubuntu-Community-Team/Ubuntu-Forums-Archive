---
title: "Updating to Meerkat dropped ATI driver"
date: 2010-11-21
forum: General Help
---

### Post by tarekeldeeb on 2010-11-21
Hello all,

I was living peacefully with 10.04, till I upgraded to 10.10. The upgrade was smooth except for the ATI driver. I have:

description: VGA compatible controller
       product: RS482 [Radeon Xpress 200M]
       vendor: ATI Technologies Inc

Now I have no driver (nothing at System>Admin>Additional Drivers)

glxgears does not exceed 60 fps. Life is too slow.

Using synaptic, I installed fglrx, this broke everything!
glxgears now gives segmentation fault. Booting is not graphical anymore, but rather a low-resolution `Ubuntu 10.10' big-font text.

Can any1 help me install the correct ATI driver (if any) and get rid of the corrupted fglrx synaptic driver?

Thanks in advance,
Tarek

---

### Post by Naitsirhc Hsem on 2010-11-21
remove fglrx using synaptec and download and install the latest ATI driver for your card from their website.

---

### Post by tarekeldeeb on 2010-11-24
> **Naitsirhc Hsem said:**
> remove fglrx using synaptec and download and install the latest ATI driver for your card from their website.

I removed it, and installed the ATI 10.11 driver. Rebooted.
Nothing happened. glxinfo gave segm. fault. Desktop effects could not be enabled.

As far as I know, the ATI open source drivers are comparably good. How can I enable them again under Meerkat?

Any clue?

---

### Post by Naitsirhc Hsem on 2010-11-24
System> Administration > Additional Drivers

I believe it is in there

---

### Post by tarekeldeeb on 2010-11-25
> **Naitsirhc Hsem said:**
> System> Administration > Additional Drivers

I believe it is in there

Thanks for supporting.
Unfortunately, I find none!

Can I force their installation/enabling ?

---

### Post by dino99 on 2010-11-25
as i know you need xserver-xorg-video-ati as driver, nothing else.

So into synaptic:

remove/purge ALL the "ati" & "fglrx" & "amd" installed packages,

then: sudo rm -f /etc/X11/xorg.conf

then add this ppa : [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) 

then: update and install xserver-xorg-video-ati (and the dependencies if any)

reboot and check driver activation

sudo dpkg --configure -a
sudo apt-get install -f

---

### Post by tarekeldeeb on 2010-11-27
> **dino99 said:**
> as i know you need xserver-xorg-video-ati as driver, nothing else.

So into synaptic:

remove/purge ALL the "ati" & "fglrx" & "amd" installed packages,

then: sudo rm -f /etc/X11/xorg.conf

then add this ppa : [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) 

then: update and install xserver-xorg-video-ati (and the dependencies if any)

 I did this ..as you pointed. I had no /etc/X11/xorg.conf
Seems that Maverick auto detects everything

> **dino99 said:**
> 
reboot and check driver activation

sudo dpkg --configure -a
sudo apt-get install -f
I did this too, although those commands returned nothing on the STDOUT. No xorg.con was generated.

I rebooted another time, but with no luck.
No drivers, or any accelerations. Stuck with m old bad symptoms.

Did I miss anything?

---

