---
title: "ati catalyst"
date: 2010-02-01
forum: General Help
---

### Post by Hogosha on 2010-02-01
so i installed the latest ATI Catalyst Control Center and this made things so much worse for my laptop. There is no now driver found for the video card. Is there a way to undo this and go back to what it was at default?

---

### Post by skymera on 2010-02-01
Try using EnvyNG to install Nvidia/ATi drivers.

I've read ATi performs notoriously bad on Linux

---

### Post by Hogosha on 2010-02-01
now it will only run in low graphics mode

---

### Post by wolfmanjack on 2010-02-01
you have to remove the fglrx driver and the ati catalyst control center via synaptic or apt-get

the fglrx driver package should be called xorg-driver-fglrx, i'm not sure what the catalyst package is called, something with accc in it iirc. also only removing the fglrx driver should do. ```
sudo apt-get remove xorg-driver-fglrx
```
afterwards reconfigure your x-server via
```
sudo dpkg-reconfigure xserver-xorg
```
or load your last good xorg.conf and you should be good to go again.

certain ati graphic cards perform rather poorly or not at all with the ati driver under linux, especially older cards in my experience.

---

### Post by deadalus.globalnode on 2010-02-01
What card is it? Sometimes you can edit your xorg.conf to get it to work. I have an ATI Mobility fire GL which does not like linux and I got it to work by editing my xorg.conf.

---

### Post by Hogosha on 2010-02-01
it is an x1250

---

### Post by Hogosha on 2010-02-01
nothing happens when i run sudo dpkg-reconfigure xserver-xorg

---

### Post by wolfmanjack on 2010-02-01
have you rebooted or restarted your xserver? the xorg.conf should be reset to default settings afterwards and you should be back to what your settings were after install. at least for me this worked repeatedly...

if you want to go down the road of trying to get the driver to work (i have a x1950xt running on 9.04, for which the driver performed quite well und 8.04, but which i never got to work under 9.04) head over to
[http://wiki.cchtml.com](http://wiki.cchtml.com)
and see if anything changes if you install the driver by hand instead of using the installer provided by ati/amd. maybe you have more luck than me :)
ever since support for older cards was dropped a while back, the driver never really worked under more recent versions of ubuntu, because no drivers are included in the newer packages.

---

### Post by Hogosha on 2010-02-01
i have restarted the machine and i am still in low graphics

---

### Post by clhsharky on 2010-02-01
HI

 Remove fglrx, it does not support legacy chips in Jaunty or newer.

Sharky

---

### Post by ajgreeny on 2010-02-01
> **Hogosha said:**
> nothing happens when i run sudo dpkg-reconfigure xserver-xorg
That command is now deprecated, and as you found, does nothing any more, I'm afraid.

You will need to install the appropriate driver, or perhaps just use the open source driver, and then use the various options available in System menu to get the screen and display how you need it.

---

### Post by Hogosha on 2010-02-01
finding a driver for an x1250 has been a goal of mine for about a year now

---

