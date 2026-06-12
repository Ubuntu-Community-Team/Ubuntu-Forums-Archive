---
title: "Ubuntu live nvidia drivers vs installed ubuntu"
date: 2011-07-14
forum: General Help
---

### Post by golaod on 2011-07-14
Hello.

I know, that was many topics like this about nvidia drivers - but I still don't have the answer.

In Ubuntu live - before install - gnome seems to work properly( good resolution and windows movement quality ), but when ubuntu is installed drivers just stops cuz resolution going to minimum, quality sux.

Question is " Can I install Ubuntu with this settings ?"

If answer is no, I will say that have same issue as others.

After installing nvidia drivers and reboot, I see black terminal.

---

### Post by mikewhatever on 2011-07-14
Perhaps you could provide some more info about the problem to make it slightly less vague.
What version of Ubuntu do you use?
What's your nvidia card? Basically, that's a nice way of asking for the output of **lspci**.
What nvidia driver do you install, and how many?

Last, but not least, if you want to use the configurations as on the Live CD, just don't install any additional drivers.

---

### Post by golaod on 2011-07-14
Sry, I knew I forgot something.

Version: 10.10 and 11.04

```

golaod@Golaod:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)

``````
lshw
```
```

 *-display
                description: VGA compatible controller
                product: G84 [GeForce 8600M GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:c6000000-c6ffffff memory:d0000000-dfffffff memory:c4000000-c5ffffff ioport:2000(size=128)

```I install current recommended from additional drivers and one time from ppa:nvidia-x-swat/x-updates

> Last, but not least, if you want to use the configurations as on the Live CD, just don't install any additional drivers.     > In Ubuntu live - before install - gnome seems to work properly( good  resolution and windows movement quality ), but when ubuntu is installed  drivers just stops cuz resolution going to minimum, quality sux.Bad quality on brand new install, so config is not the same as live cd.

---

### Post by mikewhatever on 2011-07-14
You might need to run **sudo nvidia-xconfig** after installing the recommended proprietary driver. That commands writes some configurations for the driver to use. Hope that helps.

---

### Post by wildmanne39 on 2011-07-14
Hi, if I read your post correctly you have installed drivers from two sources in that case you need to open synaptic and type nvidia in the search box and make sure you do not have two installed this happened to me.

You can not go by it only showing one active in additional drivers if you installed two then they are probably both installed still, in my case removing one of them fixed my issue.

Also run this command in a terminal
```
/usr/lib/nux/unity_support_test -p
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by golaod on 2011-07-19
Hi, I'm back.

So, when I was busy I thought ' I will prepare brand new ubuntu', and I did it.

Ubuntu 11.04
```

lshw
*-display UNCLAIMED
                description: VGA compatible controller
                product: G84 [GeForce 8600M GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller cap_list
                configuration: latency=0
                resources: memory:c6000000-c6ffffff memory:d0000000-dfffffff memory:c4000000-c5ffffff ioport:2000(size=128)

```
```

golaod@pc:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

```
```

golaod@pc:~$ jockey-text -l
xorg:nvidia_173 - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)
xorg:nvidia_current - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)
pkg:sl-modem-daemon - Software modem (Proprietary, Disabled, Not in use)
xorg:nouveau - Experimental 3D support for NVIDIA cards (Free, Disabled, Not in use)
golaod@pc:~$ jockey-text -u -c
golaod@pc:~$ jockey-text -e xorg:nvidia_current
  
SystemError: installArchives() failed
golaod@pc:~$ jockey-text -e xorg:nvidia_173

SystemError: installArchives() failed

```

And here is printscreen from Synaptic:
[http://imageshack.us/f/577/przed.png/](http://imageshack.us/f/577/przed.png/)

---

### Post by tobiz on 2011-07-19
I had a similar issue installing 11.04 on an old machine with an nVidia card.  Running live was ok but after selecting 'install' and reboot the screen didn't display anything and the system went into a loop. It looked like a graphics problem so I did Cntrl+F1 to get into a new non-X screen, de-installed the nvida 173 graphics driver by apt, Cntrl+F7 to get back into X and all was ok. My conclusion was that there is a problem with the nvida-173 driver, use the opensource one. In the past the nvidia driver could be download from nVidia and installed using their instructions which I think built it from source on your machine, it worked in the past but may have changed, ie is now a standard package, but seems to have issues.

---

