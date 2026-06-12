---
title: "Nouveau or Nvidia proprietary drivers? (cur. status)"
date: 2012-05-08
forum: General Help
---

### Post by A2llex on 2012-05-08
Hi, what do you think, what is better choice now for drivers? I really don't play games at all, but i play HD videos and so on.

How is it with performance of those drivers?

My ubuntu 12.04 laggs a little so i thought I'd try nouveau..

---

### Post by markbl on 2012-05-08
This is an interesting question. I have always installed the proprietary driver within seconds after I boot each new ubuntu install. The "Additional Drivers" icon stares at you and the words on that window say that:

"3D accelerated proprietary graphics driver for NVIDIA cards are required if you want to run Unity."

and also:

"You need to install this driver if you wish to use the Unity desktop, enable desktop effects, or run software that requires 3D acceleration, such as some games."

I found out only yesterday that these statements are not true. After experiencing various serious problems with the v295.40, v295.49, and v302.07 nvidia drivers, I gave up and installed the open nouveau driver and found that it works well with Unity and gnome-shell with full 3D effects etc. I have found no disadvantages at all and I don't get the seg faults I have been experiencing with the nvidia driver. Also virtual terminals work now (they are just a black screen using nvidia). It is nice that xrandr works also (which means you can the standard display settings controls with nouveau, unlike nvidia).

Maybe my fps number is down but I don't play games so it does not really make a difference to me. I'll probably try out the next version of nvidia driver but nouveau has been a surprise and currently working well for me.

---

### Post by zombifier25 on 2012-05-08
Agree. NVIDIA proprietary drivers suffer from a lot of bugs. If Noveau works for you, then there is no reason to switch.

---

### Post by kelvin spratt on 2012-05-08
Never had a problem with Nvidia in 6 years, always download from Nvidia and install the Nvidia way.

---

### Post by carranty on 2012-05-08
> **markbl said:**
> I gave up and installed the open nouveau driver 

How did you install this?  Its my understanding the nouveau drivers are the ones you start with.  I'm having trouble with both the drivers I start with after a fresh install and Nvidia's proprietary ones so if I'm missing another option please let me know!!

---

### Post by markbl on 2012-05-08
> **carranty said:**
> How did you install this?  Its my understanding the nouveau drivers are the ones you start with.  I'm having trouble with both the drivers I start with after a fresh install and Nvidia's proprietary ones so if I'm missing another option please let me know!!

Just fire up the Settings/Additional Drivers dialog and disable the proprietary driver. Ubuntu will fall back to the nouveau driver, if appropriate for your card. Best also if you delete or move /etc/X11/xorg.conf before you reboot to nouveau to start afresh.

Note that I still have the xorg-edgers ppa enabled (remnant from my attempts to get a working nvidia driver) so I will have a slightly updated nouveau driver + xorg from there.

---

### Post by markbl on 2012-05-08
> **kelvin spratt said:**
> Never had a problem with Nvidia in 6 years, always download from Nvidia and install the Nvidia way.
Me either previously, but here [is my experience this time](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485/comments/136) with ubuntu 12.04.

---

### Post by ubuntu27 on 2012-05-09
Currently, the [nVidia regression bug]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485") has been fixed for Ubuntu Quantal Quetzal. The bug fix (a new nVidia driver)  for Ubuntu Precise Pangolin is in [precise-proposed]("https://wiki.ubuntu.com/Testing/EnableProposed"). So, we will appreciate if the affected users could test it and tell us about their experience.

Good luck everyone!
**Fingers Crossed**


We can provide feedback by posting a comment on [bug#982485]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485")

---

### Post by A2llex on 2012-05-09
well, I've just tried out  nouveau and it works great so far.
there are still some issues with rendering windows (if i move them) etc., but with nVidia drivers it was more horrible :)

---

### Post by Papex on 2012-05-09
> **ubuntu27 said:**
> Currently, the [nVidia regression bug]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485") has been fixed for Ubuntu Quantal Quetzal. The bug fix (a new nVidia driver)  for Ubuntu Precise Pangolin is in [precise-proposed]("https://wiki.ubuntu.com/Testing/EnableProposed"). So, we will appreciate if the affected users could test it and tell us about their experience.

Good luck everyone!
**Fingers Crossed**


We can provide feedback by posting a comment on [bug#982485]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485")

Enabled precise-proposed. What is the name of the driver to look for then?

---

### Post by ubuntu27 on 2012-05-09
> **Papex said:**
> Enabled precise-proposed. What is the name of the driver to look for then?

Accordig to [Martin Pitt]("https://launchpad.net/~pitti") the package name is "**nvidia-graphics-drivers-updates**." though I did not find it when I enabled Precise-Proposed. Perhaps it still hasn't arrived on the server that I use.
[URL="https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485/comments/135"]
Source[/URL]

---

### Post by Papex on 2012-05-09
> **ubuntu27 said:**
> Accordig to [Martin Pitt]("https://launchpad.net/~pitti") the package name is "**nvidia-graphics-drivers-updates**." though I did not find it when I enabled Precise-Proposed. Perhaps it still hasn't arrived on the server that I use.
[URL="https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485/comments/135"]
Source[/URL]

Couldn't find it either ;-)

---

### Post by Paqman on 2012-05-09
> **A2llex said:**
> I really don't play games at all, but i play HD videos and so on.


You definitely want the proprietary driver then. You can't use VDPAU with nouveau. VDPAU will make HD video playback a lot smoother and you'll use a lot less CPU, which means your machine won't sound like a hovercraft when you're trying to watch a movie.

---

### Post by vegarend on 2012-05-09
Using drivers from nvidia has never worked very well for me, so I've stayed with open source. 

Noveau works well for me in 12.04, but bumblebee is what saved the day for my laptop :)

---

### Post by ubuntu27 on 2012-05-09
> **Papex said:**
> Couldn't find it either ;-)

According to [eros2]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485/comments/146"), the package is **nvidia-current-updates**.

I don't have an nVidia card, so all I could do is observe. :(

---

### Post by A2llex on 2012-05-10
> **ubuntu27 said:**
> 

I don't have an nVidia card, so all I could do is observe. :(

hehe :lolflag:

---

### Post by A2llex on 2012-05-10
> **Paqman said:**
> You definitely want the proprietary driver then. You can't use VDPAU with nouveau. VDPAU will make HD video playback a lot smoother and you'll use a lot less CPU, which means your machine won't sound like a hovercraft when you're trying to watch a movie.

i just tried HD videos, and works better than with nVidia driver.

---

### Post by A2llex on 2012-05-23
well.. looks like it wasn't best idea to install nouveau.
my Ubuntu was freezing once a time, cuz nouveau has not best support for compiz.

so I've returned back to nVidia. :(

---

### Post by sgage on 2012-05-23
I have always used the nvidia proprietary drivers, but now I find that nouveau has come a long way. For my needs, performance-wise nouveau works just fine. The only complaints I have at this point are 1) the ugly tearing weirdness at boot time for a few seconds and 2) a few degrees C of extra heat on the GPU. This thermal difference has come way down over the evolution of nouveau - it used to be more like 10 degrees.

For me, the nvidia proprietary drivers also work just fine, except that lately they do not allow the use of virtual terminals. This is a known bug, associated, I believe, with the 8xxx series of GeForce cards (I have an 8500 GT). I expect it will be fixed fairly soon.

Right now I'm just sticking with nouveau, because it makes me feel better to have VT's available :KS

---

### Post by sudodus on 2012-05-23
I have 'installed' Lubuntu (plus xubuntu-desktop) to a USB pen drive, where I keep Nouveau, because I want it portable. The graphics work well on most computers :KS

That USB system is completely upgradeable (in contrast to a persistent live system). The only problem is that upgrading is slow. I have a clone of it on an internal HDD in an old computer in order to make big upgrades faster. Writing many small files is really slow on my USB drive, so it is faster via the HDD even if it implies cloning back and forth.

---

### Post by UltraZone on 2012-05-24
I used to have lots of problems with the nVidia drivers 295.40 (the default "proprietary" drivers).

Then, I upgraded to 295.53.  It made all the difference.

The fix is described here:

[http://ubuntuforums.org/showthread.php?t=1983061](http://ubuntuforums.org/showthread.php?t=1983061)

Enjoy.

---

### Post by windfix on 2012-07-02
> **markbl said:**
> Just fire up the Settings/Additional Drivers dialog and disable the proprietary driver. Ubuntu will fall back to the nouveau driver, if appropriate for your card. Best also if you delete or move /etc/X11/xorg.conf before you reboot to nouveau to start afresh.


Thanks! Worked fine for me, and has ended NVIDIA's reign of terror on my laptop.  It was SOOOO annoying that I could not use Ubuntu's standard displays settings... now I can!

---

### Post by markbl on 2012-07-02
> **windfix said:**
> It was SOOOO annoying that I could not use Ubuntu's standard displays settings... now I can!
Actually, the latest nvidia proprietary driver (currently v302.17) does now support the xorg RANDR extension so you can use the standard display settings.

Although of course, that latest version still suffers the segmentation abort that all versions since v295.33 exhibit, at least for many of us.

---

