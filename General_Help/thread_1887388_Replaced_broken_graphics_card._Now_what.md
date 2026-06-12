---
title: "Replaced broken graphics card. Now what?"
date: 2011-11-26
forum: General Help
---

### Post by JC Cheloven on 2011-11-26
Hi, my Nvidia Graphics card died today. I Just bought a new one in a hurry (a GForce GT520) and plugged it in. I naively hoped it to be automagically recognised and configured, but it's not the case.

At boot time the pc stalls at a point where it says "enabling additional executable binary formats binfmt-support". Nevertheless I can get a terminal with ctrl-alt-F1.

I tried a few things from there, as "dpkg-reconfigure xserver-xorg", or installing "nvidia-current" (without uninstalling anything before, I'm afraid). No luck so far.

If anyone with a more precise idea on how this works could give me a hand, it would be great. Thanks.

JC

---

### Post by oldtimer7777 on 2011-11-26
Are you able to login with failsafe graphics mode? 

Are you able to remove your previously installed graphics driver packages? 

Is your card even supported? 

[http://www.nvidia.co.uk/object/linux-display-ia32-270.41.19-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-270.41.19-driver-uk.html)


> **JC Cheloven said:**
> Hi, my Nvidia Graphics card died today. I Just bought a new one in a hurry (a GForce GT520) and plugged it in. I naively hoped it to be automagically recognised and configured, but it's not the case.

At boot time the pc stalls at a point where it says "enabling additional executable binary formats binfmt-support". Nevertheless I can get a terminal with ctrl-alt-F1.

I tried a few things from there, as "dpkg-reconfigure xserver-xorg", or installing "nvidia-current" (without uninstalling anything before, I'm afraid). No luck so far.

If anyone with a more precise idea on how this works could give me a hand, it would be great. Thanks.

JC

---

### Post by JC Cheloven on 2011-11-27
> **oldtimer7777 said:**
> Are you able to login with failsafe graphics mode?  
Not from the LUbuntu 11.04 install I'm interested in. But I'm able to do so in an old (now unsupported) ubuntustudio install in another partition. This doesn't help much, I'm afraid.

> 
Are you able to remove your previously installed graphics driver packages? 

THIS is a keypoint. I uninstalled (using apt-get remove) some related packages before installing nvidia-current, but I think I need to edit some files as well, and I'm not sure which ones.

> 
Is your card even supported? 

Yes, it is. I had a look before purchasing ;)

In case it matters, the previous gpu was a nvidia 7300 GT, also supported. Running 64bits LUbuntu.

---

### Post by JC Cheloven on 2011-11-27
Some progress: 
I can now at least boot in vesa graphics mode, which isn't a solution but hopefully is a start. 

What I did is copying a file /etc/X11/xorg.conf.failsafe to /etc/X11/xorg.conf and reboot. It specified 'vesa' driver.

Once in the desktop, from the 'additional drivers' utility, i deleted the nvidia driver installed, and activated the 'current' one, which is (natty) 270.41.06.
EDIT: according to the [manufacturer page]("http://www.nvidia.com/object/linux-display-ia32-270.41.06-driver.html") this version should suffice.

In the same 'additional drivers' utility it says that "it is set, but not currently in use". I tried removing the xserver-xorg-video-nouveau package from synaptic (as perhaps the nouveau driver is interfering...), but it keeps saying that curent nvidia driver is not in use. Any ideas?

---

### Post by cwwilson721 on 2011-11-27
That's a known issue in Natty.

The 'real' test is to start nvidia-settings. If that works, the driver is working.

---

### Post by JC Cheloven on 2011-11-27
> **cwwilson721 said:**
> That's a known issue in Natty.

The 'real' test is to start nvidia-settings. If that works, the driver is working.

Thanks a lot, I wasn't aware of that bug. Your info has been useful. 

In fact it seems to be working now: nvidia-settings responds as expected, and the glxgears test gives me about 7750 fps, which is not bad at all, I guess.

At some point, I tried glxgears (before uninstalling the nouveau package, I think), and it simply refused to run. So, at some point I must have done the right thing :)

Also, there is an issue with the driver and this card: whenever I open a terminal, an additional equivalent portion of the screen gets black (see attachment). This is minor annoyance, as it gets painted again as soon as another window is moved, but it kept me thinking that I was still in vesa mode. Anyway, I think this is unrelated to the subject of the thread. Marking as solved, which is not a prohibition for someone else to post about this last issue ;)

Thanks
JC

---

### Post by amjjawad on 2011-11-29
Hello JC,

Are you running 11.04 still? have you tried 11.10? at least it has a newer Kernel :)

Just give it a go from LiveCD or LiveUSB.

---

