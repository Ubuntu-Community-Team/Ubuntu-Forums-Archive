---
title: "Nvidia problems with 12.04"
date: 2012-04-26
forum: General Help
---

### Post by geovino on 2012-04-26
Just installed 12.04.

It wanted to install the Nvidia drivers (geforce 6100) like in the past. This time after install the log in screen comes up I log in then the screen goes black! I've had trouble with Nvidia drivers for the past five years and its always the same.

How do I just use the generic drivers that come with Ubuntu and forget about Nvidia altogether?

I'll have to reinstall 12.04 and just ignore the driver pop up. Maybe the Ubuntu logo will show up on start up and shut down like it should. I'm sick of proprietory drivers! They are nothing but trouble.


note: there were many replies, but the thread was closed. I moved it to here, hopefully the admins will leave it up for a while. :)

---

### Post by geovino on 2012-04-26
In the past I used to install nvidia-173. Maybe that one will work as opposed to whatever Unbuntu wants you to install for 12.04. This may make a big difference. 

In the meantime, Ubuntu 12.04 is running fine after reinstalling and not installing the proprietory drivers which did not work at all with my PC which has a Geforce 6100 video.

---

### Post by Chriske on 2012-04-27
I found that when I install Nvidia ("additional") drivers the desktop simply will not work - all I see is the wallpaper.

If I don't install them, the display works, but it is quite dark and even 100% brightness is not satisfactory. Not good :(

(This is besides *a lot* of other problems I had with the install).

---

### Post by pqwoerituytrueiwoq on 2012-04-27
i have heard that the nvidia driver does tot get along with lightdm you can switch to gdm
```
sudo apt-get install gdm;sudo apt-get remove lightdm
```

---

### Post by searchfgold6789 on 2012-04-28
The nVidia drivers don't work with 12.04. NVidia needs to update them so that they work with the latest X.org version. Until then you'll have to use the noveau driver :(

---

### Post by SeijiSensei on 2012-04-28
Maybe that's true for Ubuntu with Unity, but it most definitely isn't true for Kubuntu 12.04.  I've been running that for a couple of months now and have gone through at least one and maybe two updates to the proprietary NVIDIA drivers.

Maybe it depends on the NVIDIA adapter being used.  I'm running a 9500GT.  The people I see having trouble are using adapters from the 6xxx series.

---

### Post by geovino on 2012-04-28
> **SeijiSensei said:**
> Maybe that's true for Ubuntu with Unity, but it most definitely isn't true for Kubuntu 12.04.  I've been running that for a couple of months now and have gone through at least one and maybe two updates to the proprietary NVIDIA drivers.

Maybe it depends on the NVIDIA adapter being used.  I'm running a 9500GT.  The people I see having trouble are using adapters from the 6xxx series.

That's me. ;)

I just ordered a EVGA 512-P3-1300-LR GeForce 8400 GS Video Card - 512MB 
Should be an improvement over the geforce 6100.

---

### Post by 62chevy on 2012-04-28
Same here nvidia drivers are working fine with my 8400GS on Ubuntu 12.04 with Unity.

---

### Post by geovino on 2012-05-07
> **62chevy said:**
> Same here nvidia drivers are working fine with my 8400GS on Ubuntu 12.04 with Unity.

...installed an nvidia geforce 8400 card. All's well now. :)

---

