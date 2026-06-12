---
title: "Sometimes When Resuming from Suspend, Screen Flickers with White Lines"
date: 2011-05-29
forum: General Help
---

### Post by jlacroix on 2011-05-29
Hello everyone, I've been away from Kubuntu for a while but came back when Kubuntu 11.04 was released because it's awesome. I have a newer laptop since then, a Latitude E6410 with Intel graphics and 8GB of RAM. Everything works great, except...

...Sometimes when I resume from suspend to RAM, the screen flickers with thin white lines across the screen. I can switch to a tty and reboot it from there, but I'm unable to use KDE until I reboot. A lot of times resuming from suspend works without issue, but sometimes this problem occurs. I haven't figured out exactly what triggers it. In fact, the most recent time it happened, I didn't even have an application open.

I would like to figure this out because I use suspend a lot. I rarely turn off my laptop unless an update requires me to. I prefer to be able to close my lid and resume whatever I was working on later, but with this glitch I cannot trust it to do that. :(

Does anyone know a fix or work around for this problem?

---

### Post by Zorael on 2011-05-30
First, visit [the Intel video bug list over on Launchpad](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel) and see if any existing bugs fit what you're experiencing.

That said, you could try telling it to completely unload the Intel video module when suspending and then loading it from scratch when resuming. I have no idea if this helps, mind, but it can't hurt.

Create a file like **/etc/pm/config.d/00-suspend-modules.conf** with the following content;
```
SUSPEND_MODULES="$SUSPEND_MODULES i915 drm_kms_helper drm"
```
The worst thing that can happen is that the behavior persists, in which case just remove the file.

You could also be daring and add the **xorg-edgers** PPA (**ppa:xorg-edgers/ppa**) for some updated drivers. And/or the **kernel-ppa** PPA (**ppa:kernel-ppa/ppa**) for the new 2.6.39 kernel that's not part of natty. Each come with their own risks, of course.

To add a PPA;
```
*#### sudo add-apt-repository ppa:name/archive*

$ sudo add-apt-repository ppa:xorg-edgers/ppa
$ sudo add-apt-repository ppa:kernel-ppa/ppa
```
To completely remove a PPA and the packages it installed;
```
$ sudo apt-get install [ppa-purge](apt://ppa-purge)

*#### sudo ppa-purge ppa:name/archive*

$ sudo ppa-purge ppa:xorg-edgers/ppa
$ sudo ppa-purge ppa:kernel-ppa/ppa
```
Particularly removing a PPA that way could be a bit tricky and take some manual toiling, but it's never impossible.

---

### Post by jlacroix on 2011-05-30
> **Zorael said:**
> First, visit [the Intel video bug list over on Launchpad](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel) and see if any existing bugs fit what you're experiencing.

That said, you could try telling it to completely unload the Intel video module when suspending and then loading it from scratch when resuming. I have no idea if this helps, mind, but it can't hurt.

Create a file like **/etc/pm/config.d/00-suspend-modules.conf** with the following content;
```
SUSPEND_MODULES="$SUSPEND_MODULES i915 drm_kms_helper drm"
```
The worst thing that can happen is that the behavior persists, in which case just remove the file.

You could also be daring and add the **xorg-edgers** PPA (**ppa:xorg-edgers/ppa**) for some updated drivers. And/or the **kernel-ppa** PPA (**ppa:kernel-ppa/ppa**) for the new 2.6.39 kernel that's not part of natty. Each come with their own risks, of course.

To add a PPA;
```
*#### sudo add-apt-repository ppa:name/archive*

$ sudo add-apt-repository ppa:xorg-edgers/ppa
$ sudo add-apt-repository ppa:kernel-ppa/ppa
```
To completely remove a PPA and the packages it installed;
```
$ sudo apt-get install [ppa-purge](apt://ppa-purge)

*#### sudo ppa-purge ppa:name/archive*

$ sudo ppa-purge ppa:xorg-edgers/ppa
$ sudo ppa-purge ppa:kernel-ppa/ppa
```
Particularly removing a PPA that way could be a bit tricky and take some manual toiling, but it's never impossible.
Thanks. I did some further testing today, and I tested my laptop with Xubuntu installed instead of Kubuntu. Suspend to RAM and resume works fine with Xubuntu, so is it possible the problem is a KDE bug, or is it because Xubuntu doesn't use desktop effects like Kubuntu does?

I'll gladly try everything you mentioned, but I wanted to check that by you first. Let me know and I will run through your steps. Thanks soooooo much for your help!

---

### Post by Zorael on 2011-05-30
> **jlacroix said:**
> Thanks. I did some further testing today, and I tested my laptop with Xubuntu installed instead of Kubuntu. Suspend to RAM and resume works fine with Xubuntu, so is it possible the problem is a KDE bug, or is it because Xubuntu doesn't use desktop effects like Kubuntu does?
This is curious. 

It seems to me it should be a kernel/drm/driver bug and not something specific to KDE, but perhaps the bug *is* in the driver and only *exposed* by KWin when resuming with desktop effects enabled. Even Xfce's window manager (Xfwm4 if memory serves) should provide compositing the same way KWin does, so if that were what caused the bug, it should be happening in Xubuntu too.

I don't know if you can suspend from a live CD/USB, but the next time you're in KDE in some way or another, try suspending effects with Alt+Shift+F12 before suspending the machine to RAM.

---

### Post by jlacroix on 2011-05-30
> **Zorael said:**
> This is curious. 

It seems to me it should be a kernel/drm/driver bug and not something specific to KDE, but perhaps the bug *is* in the driver and only *exposed* by KWin when resuming with desktop effects enabled. Even Xfce's window manager (Xfwm4 if memory serves) should provide compositing the same way KWin does, so if that were what caused the bug, it should be happening in Xubuntu too.

I don't know if you can suspend from a live CD/USB, but the next time you're in KDE in some way or another, try suspending effects with Alt+Shift+F12 before suspending the machine to RAM.
Thank you, I will try this periodically and report back as soon as I can.

---

### Post by jlacroix on 2011-06-04
I've been playing with this off and on, and I'm still not certain what is causing this. I do know that I can repeat this problem easily when docking and undocking (I have a port replicator from Dell) but it hasn't happened lately other than docking and undocking. Strangely enough, my docking station works fine if I turn my laptop on while docked, but if the laptop is already on and I dock it, I am only asking for trouble.

When docking, I can do this to switch the displays properly:
```
xrandr --output DP1 --off --output HDMI1 --auto
```

And when undocking, this command puts the display on the appropriate screen:
```
xrandr --output HDMI1 --off --output DP1 --auto
```

But, I have no idea how to make those commands run automatically when the docking station is connected and disconnected. :(

Figuring that out may solve it, but then again I will keep testing.

---

