---
title: "No 3D graphics in Natty beta 1"
date: 2011-04-05
forum: General Help
---

### Post by bovender on 2011-04-05
Hi all,

I wanted to try out the Natty beta 1, but apparently it fails to load the graphics drivers. When I run the "Additional drivers" app, no drivers are listed. I installed the nvidia-current package and rebooted, but nothing happened. This problem occurs with an install in a VirtualBox machine, as well as with the live CD.

Running Maverick with Compiz and the proprierary Nvidia drivers on a Lenovo T61 with Nvidia Quadro NVS 140, built in 2008. I hope this machine is not too old already to upgrade to Natty?!

What can I do to see the fully graphics-enabled Natty/Unity desktop  on my laptop?

---

### Post by ajgreeny on 2011-04-05
I do not use VB or any other virtualisation, but I don't think you need a separate graphics driver in a virtual install, as it uses whatever your host system is using, not its own.  Don't forget that when you reboot a live CD to use the new driver you just installed, that driver is immediately lost.

---

### Post by coffeecat on 2011-04-05
Installing the nvidia driver in VirtualBox isn't going to help as you are using a virtual graphics card in the guest machine which has its own driver.

You need to install the latest version of VirtualBox and install the guest additions in the guest OS before you have any hope of activating 3-d in VirtualBox. I believe there was some discussion about the compatibility of Natty in VirtualBox in the Natty subforum, but I can't remember the details. It may be that it won't work yet but will by final release day, but you'd need to search the Natty subforum for this.

And as ajgreeny points out there is no point installing a proprietary video driver to a live CD session. You could try creating a live USB with persistence. That might work.

---

### Post by andrew.46 on 2011-04-06
I believe the official Virtualbox line at the moment is that Virtualbox 4.0.4 does not support Natty Narwhal but will do so in the next release. Some discussion [here]("http://www.virtualbox.org/ticket/8635") although the suggested workaround did not work on my system.

---

### Post by techunit on 2011-04-06
Support for Natty has been pretty on and off lately and can't be depended upon I hope they release a new patch soon so the Ubuntu Video Tutorials can begin.

---

### Post by bovender on 2011-04-07
Thanks for the info. Indeed, after installing the virtualbox-guest additions (all packages that I could find using the terms "virtualbox" and "guest" in Package Manager), I get the Unity interface. It is terribly slow though and crashes a lot, but heck, it's work in progress.

It's puzzling me though that I also didn't get to see Unity running the Live CD, and that no graphics drivers were offered to install. This was different in previous live CDs.

(On a side note... I more and more get the impression that I'll stick with the 10.10 release and wait for a matured 11.10...)

---

### Post by coffeecat on 2011-04-07
> **lazy_leukocyte said:**
> It's puzzling me though that I also didn't get to see Unity running the Live CD, and that no graphics drivers were offered to install. This was different in previous live CDs.

The reason you didn't get Unity in the live CD session is that you have a nvidia card. The open source nouveau driver isn't quite there yet for 3-d out-of-the-box. There is an experimental package to supplement the nouveau driver to get 3-d but you have to have a permanent installation to see it in action.

Unity works in the live CD session if you have a (suitable) Intel or ATI graphics chip since the ATI and Intel open source drivers have reasonable 3-d support.

Unfortunately, there's no point installing the proprietary nvidia driver in the live session because you have to reboot to activate it and in the live session you lose any installed packages when you reboot. Unless you use a live USB with persistence, that is.

---

