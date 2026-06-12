---
title: "Xgl/ATI - keeps using Mesa drivers rather than fglrx"
date: 2006-06-05
forum: General Help
---

### Post by exclipy on 2006-06-05
Hi all,

I've been trying to get Xgl working on my ATI Radeon Mobility 9600, in Kubuntu.

With normal X.org, it seems to use the correct fglrx driver (according to fglrxinfo).  However, Xgl seems to always load the Mesa drivers.  As a result, compiz doesn't work and the display is extremely laggy (much worse than X.org on Mesa drivers).

I'm using Quinn's compiz-0.0.11 packages.  I've tried the [Xgl/compiz on an Ati video card](http://www.ubuntuforums.org/showthread.php?t=131253) howto, as well as the [Xgl-Kubuntu automatic Xgl installation](http://www.compiz.net/viewtopic.php?id=689) script with the same result on each attempt.

Has anyone seen this before and have any suggestions?

---

### Post by Flyn on 2006-06-06
First of all, install the latest drivers using the following commands.
(I'm not sure if you have to remove the restricted modules before installing or if this has been fixed, in any case try doing it without the modules first.)
(This should be done in the directory to which you downloaded the ati installer .bin file.)
```
 
sudo apt-get install module-assistant build-essential dpkg-dev debhelper fakeroot
sh ati-driver-installer-8.25.18-x86.run --buildpkg Ubuntu/6.06
sudo dpkg -i xorg-driver-fglrx_8.25.18-1_i386.deb fglrx-kernel-source_8.25.18-1_i386.deb fglrx-control_8.25.18-1_i386.deb
sudo module-assistant prepare
sudo module-assistant auto-install fglrx-kernel
depmod -aq
sudo /etc/init.d/gdm stop
sudo rmmod radeon drm
sudo modprobe fglrx
sudo /etc/init.d/gdm start
```
 
After checking you have the latest ATI drivers working with ```
fglrx
```
 
follow the instrcutions in [this thread]("http://ubuntuforums.org/showthread.php?t=168618") and you should be able to run XGL and Compiz properly.

---

### Post by exclipy on 2006-06-06
Thanks for the reply, but as I said, the latest fglrx drivers are working fine in for /usr/bin/X, it's just that Xgl doesn't pick them up.  Nevertheless, I tried reinstalling the drivers using your instructions to no avail.  I even tried installing ubuntu-desktop for gdm and Gnome to try it in there, but it wouldn't start under Xgl.

---

### Post by Lil_Eagle on 2006-06-06
That is the hard way.

If you have flrgx 8.15.18 already, and when you do fglrxinfo and it shows the mesa drivers, then you need to initialize the ATI drivers.  You do that by:

sudo aticonfig --initial
sudo aticonfig --overlay-tpye=Xv

then reboot and check fglrx again.  It should show your ATI card.

Like this:

```

joe@p4lr:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

I don't use GLX (Yet) so can't help you with that, but I can say that that's for Xorg, so you still need it.  (aticonfig will rewrite your xorg.conf file)

Keep in mind that these drivers are buggy.  You may not like them.

---

### Post by Flyn on 2006-06-06
I've tried all the XGL methods described in the forums and the only one that worked is in [this thread]("http://ubuntuforums.org/showthread.php?t=168618"). (I'm using a X800 XT PE.)
Give it a try and hopefully it will work.

---

### Post by ashrack on 2006-06-21
this fixed my problems:
[http://ubuntuforums.org/showthread.php?t=143283](http://ubuntuforums.org/showthread.php?t=143283)

---

### Post by mach3k on 2006-09-08
I am having the same problem here - when i start Xgl, fglrxinfo will report everything ok. I tried installing drivers 8.26.18, 8.28.18, but still the same thing happens - with Xorg everything works fine, with Xgl, things break. It must be something with the libGL locations / versions. Has anyone solved a  soimilar proble, and if yes, how?

---

### Post by infol on 2006-09-24
i had the same problem, and it feels like i've looked at every howto on the internet (just like many of you, i gather)...
anyway, the solution to my problem was very easy, and can be found on
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

i did not have the correct kernel drivers installed (and no other howto seems to point out that this can be the culprit in many cases)..

anyhow, good luck to the rest of you...   ;)

---

### Post by revfrsanctus on 2006-09-29
> **Lil_Eagle said:**
> That is the hard way.

If you have flrgx 8.15.18 already, and when you do fglrxinfo and it shows the mesa drivers, then you need to initialize the ATI drivers.  You do that by:

sudo aticonfig --initial
sudo aticonfig --overlay-tpye=Xv

then reboot and check fglrx again.  It should show your ATI card.

Lil, Eagle,

Thank you.  It works, sorta.  It works until I reboot.  When I reboot, I come back and it's back to the MESA drivers.  ARGGGGGGG!

Then, if do this...

```
sudo /etc/init.d/gdm stop
sudo rmmod radeon drm
sudo modprobe fglrx
sudo /etc/init.d/gdm start
```

Then afterwards, I get this....

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.6065 (8.29.6)


```

But everytime I boot, I'd have to repeat.  The fix is...

```
sudo gedit /etc/modules
```

Add:
agpgart
fglrx
dri

Remove:
radeon

Woohoo!  Thank You!

---

