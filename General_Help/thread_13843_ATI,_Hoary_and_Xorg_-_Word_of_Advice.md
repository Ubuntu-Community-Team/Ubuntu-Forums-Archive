---
title: "ATI, Hoary and Xorg - Word of Advice"
date: 2005-02-03
forum: General Help
---

### Post by oelph on 2005-02-03
This might have been said before but I didn't come across it when fixing this for my system...

I upgraded to Hoary, added in the FLGRX drivers but was stuck with Mesa for OpenGL and 300ish fps in GLXGears. What cured it for me was upgrading from kernel 2.6.8 to 2.6.10. After a reboot ATI was now registered for OpenGL and 3000+ fps in GLXGears.

Thought I'd post this in the hope it will help out someone else in a similar situation.

---

### Post by aToaster on 2005-02-03
[QUOTE=oelph]This might have been said before but I didn't come across it when fixing this for my system...

I upgraded to Hoary, added in the FLGRX drivers but was stuck with Mesa for OpenGL and 300ish fps in GLXGears. What cured it for me was upgrading from kernel 2.6.8 to 2.6.10. After a reboot ATI was now registered for OpenGL and 3000+ fps in GLXGears.

Thought I'd post this in the hope it will help out someone else in a similar situation.[/QUOTE]
 Just a word to those still in Warty, you can get the new ATI drivers to work in Warty.  So you don't have to switch just because of it.  Scottles has posted an excellent HOWTO on the new ATI driversr with Warty, check here [http://ubuntuforums.org/showthread.php?t=13226](http://ubuntuforums.org/showthread.php?t=13226)

---

### Post by shakin on 2005-02-03
[QUOTE=oelph]This might have been said before but I didn't come across it when fixing this for my system...

I upgraded to Hoary, added in the FLGRX drivers but was stuck with Mesa for OpenGL and 300ish fps in GLXGears. What cured it for me was upgrading from kernel 2.6.8 to 2.6.10. After a reboot ATI was now registered for OpenGL and 3000+ fps in GLXGears.

Thought I'd post this in the hope it will help out someone else in a similar situation.[/QUOTE]

For those who got 2.6.10 installed with Hoary, re-installing 2.6.10 doesn't fix the problem -- and in fact now I get 121fps in glxgears instead of the 305fps I was getting before. I'm still looking for a solution and will post it once the ATI driver is working.

---

### Post by Cred on 2005-02-05
[This](http://www.ubuntulinux.org/wiki/BinaryDriverHowto) made my 9500 work after upgrading to Hoary.

I also remember seeing on rage3d.com forums that the FPS does actually drop with the newest drivers but adds some stability and supports more cards.

---

### Post by songochain on 2005-02-09
I've done all but still i get 320 fps in glxgears :( Also my kernel is the last for hoary. When i type modprobe fglrx...
```
songochain@ximian64:~ $ sudo modprobe fglrx
Password:
FATAL: Error inserting fglrx (/lib/modules/2.6.10-3-amd64-generic/kernel/drivers/video/fglrx.ko): No such device

```And i've fglrx... ```
songochain@ximian64:~ $ sudo echo fglrx | sudo tee -a /etc/modules
fglrx

```
So if someone knows what happen...
And the syslog```
Feb 10 00:10:02 ximian64 kernel: [fglrx:firegl_init_32compat_ioctls] *ERROR* unable to register ioctl32 0
Feb 10 00:10:02 ximian64 kernel: [fglrx:firegl_init] *ERROR* Couldn't register compat32 ioctls!
Feb 10 00:10:02 ximian64 kernel: [fglrx] Maximum main memory to use for locked dma buffers: 424 MBytes.
```

---

### Post by Strider on 2005-02-10
Here's what I've experienced so far with the fglrx/ATI and Hoary...

I installed Warty and upgraded to hoary.  I upgraded to the 2.6.10-3-i686 kernel and all works well.  I also migrated from Xfree -> Xorg.  Had to grab the xorg-fglrx pacakge.  When I run glxgears I get about 1300-1400 fps. 

However, because I have an ASUS M6N notebook the battery status does not work.  There's a kernel hack to resolve this minor issue but it requires a recompiled kernel.  So I downloaded all the source, made the hack, and recompile.  After I recompile, rebooted, my battery status works but I lost my fglrx stuff.  It defaulted back to MESA and I only get about 200-300 fps.

Found out that I need to recompile the fglrx specifically for the kernel I'm using and after a bit of problems getting the fglrx recompiled I decided I'll wait a bit.  It seems the ATI driver is not working properly and everywhere I search there seems to be some problem compiling the source.  I went back to the 2.6.10-3-i686 kernel provided by the repository and I have fglrx working again but no battery status... seems I can't have both right now but I'm sure I will soon.

For those who want to compile the fglrx driver, take a look at this [link](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html).

If you're using the standard kernel (not a recompile) and you're on hoary with xorg you need to get the xorg-fglrx driver.  Just do an apt-get or grab it from synaptic.  That works great.  After a reboot you should have it listed in glxinfo.

If anyone has any ideas on a recompile kernel with the fglrx module let me know.  I tried the procedure outlined in the link I posted above but it does not work...  I'm not getting the correct stuff from ATI and it seems that this will only work with XFree86 and not xorg.

---

### Post by songochain on 2005-02-10
Thanks for reply. I think i've all deb to run xorg and fglrx correctly but if u say to me what archives you've installed, it would be a great help. I've installed: xorg-common, xorg-driver-fglrx, xorg-driver-synaptics, xserver-xorg and fglrx-control. May be i have to install fglrx-kernel-source??
Thanks 4 the link but i see that there are some people who get a greats fps using glxgears.
I've a Asus too but it's a A4K with a amd64 3200+ mobile, i think i've a friend that has the same asus than u The point is... sometimes x is freeze and i can see artifacts but with ubuntu live no but with 1024x768 and this's sux because the best resolution is 1280x800, although with 1024x768 using ubuntu installed version i get artifacts too, so i think the problem is with ubuntu installed version (warty and hoary)
I forgot it... my desktop uses 16 bit colors instead of 24bits and i dont know why...
Cya

---

### Post by Strider on 2005-02-10
As you stated there are the packages I installed:

xorg-common, xorg-driver-fglrx, xorg-driver-synaptics, server-xorg.

I also remove any old stuff that dealt with Xfree86 (xfree86-common, xfree86-driver-fglrx, xfree86-driver-synaptics, xserver-xfree86).  After I did an upgrade to xorg, there was still one or two packages remaining which had to be removed manually.

Make sure you also get the kernel-restricted-modules-<version>-<platform> package.  This will install the modules specifically for the kernel version you're using.

Since you installed the fglrx-control package you can run fglrxconfig to setup an Xconfig file.  It will be placed in the /etc/X11 directory.  Your actual configuration should be in /etc/X11/xorg.conf.  You can update it with the changes fglrxconfig made. 

Let me know if that helps.

---

### Post by songochain on 2005-02-10
Nothing... i've all deb I'm boring  :roll: May be it's better install ubuntu 32bits version

---

### Post by Strider on 2005-02-10
I know the feeling.  I've been back and forth between different distros and am still running into the same problem.  The recompile of the fglrx module for a custom kernel does not work for me.  Just craps out.

I do have the i686 kernel installed and the fglrx is working there but I loose my battery status.

I assume you're still having the MESA stuff show up?  Did you make the changes in your xorg.conf so it uses the fglrx?  Here's my device configuration in the xorg.conf:

```

Section "Device"
      Identifier     "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
      Driver          "fglrx"
      BusID          "PCI:1:0:0"
      Option         "UseInternalAGPGART" "no"
EndSection

```

You probably are aware of that already but just checking...

Hope you get somewhere with it...

---

### Post by songochain on 2005-02-10
Yes, i changed it in the xorg.conf and i'm still with mesa. Can u post your full xorg.conf?? Also can u post all i have to do: xfree86 to xorg with fglrx running?
Thanks

---

### Post by Strider on 2005-02-10
Here's what I did to upgrade from Xfree to Xorg w/fglrx on kernel 2.6.10-3-686 (initially using 2.8.1-4-386)

1) Upgrade to kernel 2.6.10-3-686 (linux-image-2.6.10-3-686, linux-restricted-modules-2.6.10-3-686, and some others.  Once you select linux-image-2.6.10-3-686 it will list the dependencies and it will install it).
2) Rebooted with the new kernel, all works fine on Xfree including fglrx.
3) From Synaptic I did a search for xorg and selectect the xorg stuff (xorg-common, xorg-driver-fglrx, xorg-driver-synaptics, xserver-org).
4) It installed and I rebooted.
5) After a reboot, loaded up Synaptic again and did a search for Xfree  and remove anything that was there.  There should only be one or two things still installed.
6) For some reason I had to do a reinstall of the xorg-driver-fglrx as it did not work for some reason (apt-get install --reinstall xorg-driver-fglrx or you can do it from Synaptic).
7) Rebooted and it was fine.

Prior to an upgrade to kernel 2.6.10-3-686 I had already made the change in my Xfree86 config file from "ati" to "fglrx".  So not sure if that was something migrated to xorg.conf.

Prior to step 6 I was getting about 200-300 fps and I was on the MESA stuff also.  After a reinstall of the xorg-driver-fglrx and a reboot I was able to get around 1300-1400 fps with glxgears.

Side note: I'm assuming you're using one of the kernels provided from the repository?  I recompiled my kernel and could not get the fglrx stuff working so I'm back to one of the kernels from the repository.

Here's my [xorg.conf](http://www.ecltech.net/tmp/xorg.conf).  I hope that may share some insight with the issue you're having.

You can also run fglrxconfig to create an XFREE config.  Check the above xorg.conf for the refresh rates as I think those may be set incorrectly for you and may be the reason why you're getting the red lines/artifacts on the screen.

Let me know how it works out.  BTW, you may have stated it already but which ASUS notebook do you have and is your battery status working?

Good luck!

---

### Post by songochain on 2005-02-11
Nothing... i probe your xorg.conf and all is the same... artifacts, mesa... I'll install gentoo. I've a friends that have gentoo with amd64 and they will help with it.
Thanks for all dude ;)
See you

---

### Post by Strider on 2005-02-11
Good luck with Gentoo... as I write this I'm installing Gentoo on my laptop also.  Figure it's worth a shot.  So far so good.  Have the base system in and system is up and running.  Pretty nice walkthrough if you don't mind spending the time to go through all the compile/etc.

---

### Post by songochain on 2005-02-11
Thanks ;) Just i'm installing gentoo, i did emerge sync and it's gonna to be long hehe
I will inform 
See you

---

### Post by songochain on 2005-02-15
HI dude, I'm back on ubuntu 64 hoary. Artifacts yet but I am customary to them. I'm trying to run fglrx with xorg. Now in my xorg.conf appear fgrlx module and it's all ok but i'm with mesa... when i type modprobe fglrx ```
FATAL: Error inserting fglrx (/lib/modules/2.6.10-3-amd64-k8/kernel/drivers/video/fglrx.ko): No such device

``` again... I saw wiki page of ubuntu [here](http://www.ubuntulinux.org/wiki/BinaryDriverHowto) but nothing...
Also while booting i can see this ```
[fglrx:firegl_stub_register] *ERROR* Unable to the open some already present DRM kernel module!
```
Now i use this kernel-image: linux-image-2.6.10-3-amd64-k8
Packages that i've installed:
fglrx-kernel-source,xorg-driver-fglrx,linux-restricted-modules-2.6.10-3-amd64-k8. Of course xorg-server...
And i dont know what's the problem  :roll: 
Thanks!
Edit:
xorg.conf uses fgrlx module but when i type modprobe fgrlx i get the error above So how X can run if i get a error loading fgrlx module??

---

### Post by songochain on 2005-02-16
Hi dude! i dont know why, but now i've fglrx!!! I boot this morning and i had not artifacts and then i did a glxgear and i go 1600fps at 1800mhz (cpu) i guest that with 2ghz i will get a bit more :D
Thanks!!
```
songochain@ximian64:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

```

---

### Post by Strider on 2005-02-16
songochain,
glad you got it working.  I know the feeling when you've been at something for a while and finally got it. :)  Hope everything else goes smoothly for you on the laptop now.

---

