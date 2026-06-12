---
title: "no display after changing graphics card in 9.04"
date: 2009-12-08
forum: General Help
---

### Post by charonred on 2009-12-08
Short story 
How do I reconfigure the graphics card selection from the recovery mode root prompt - I know it's a simple script, I just don't know it.

Long story
Brothers PC has a Gigabyte m/board with on-board ATI graphics. When I installed Jaunty 9.04, I did so with the NVidia PCIe card from his previous PC. 

All worked fine, but a few weeks later he complained the GPU was running hot (lmsensors). So I took the NVidia card out and set it to use the on-board graphics. This was ok, but he said it now ran slower; so I went back and installed a ASUS HD2600 512MB card I had spare hoping that would fix it.

This worked ok in his account, but his wife's account had a blank screen; so today I went back and re-installed the original NVidia card - but now I can't get any display past the Ubuntu loading progress bar, it's just a blank screen.

---

### Post by bluenova on 2009-12-08
Hi charonred,

It's:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by charonred on 2009-12-08
can't get into Ubuntu GUI at all, so sudo is not an option, only recovery mode which allows me to run as root,  and so ran
```
dpkg-reconfigure xserver-xorg
```
but it made no difference, let me 'reconfigure' keyboard selection etc, but not graphics, so still have a blank screen, just need to get the NVidia drivers loading /working again

---

### Post by bluenova on 2009-12-08
Ah ok, assuming you have the nvidia drivers installed try:

```
nvidia-xconfig
```

---

### Post by charonred on 2009-12-08
tried that, only get 'no such command' ??

*unfortunately my wireless client in garage is dead, so I'm going between this PC in my room and brother's PC in garage (where spare monitor is)*

---

### Post by bluenova on 2009-12-08
Otherwise try editing your xorg.conf to the open drivers and then reapplying the nVidia drivers using the GUI tool.

nano /etc/X11/xorg.conf

Change driver to: NV

**Edit:**
No such command, do you have the drivers installed:
apt-get install nvidia-glx-new

---

### Post by charonred on 2009-12-08
I have no GUI at all, how do I do that from recovery root

ps no network in garage at moment

---

### Post by bluenova on 2009-12-08
try the open drivers

```
nano /etc/X11/xorg.conf
```

Change driver to: NV

that should hopefully get you back to a GUI.

---

### Post by charonred on 2009-12-08
did that, but none of it made sense to me, I just don't know that much linux.

I know there's a screen that lets you configure/choose graphics, but don't know how to get it.

thought; If I boot using a live CD, could I edit the relevant PC system file for Jaunty?, or would doing an upgrade to Karmic fix the problem.

---

### Post by bluenova on 2009-12-08
So did you get a GUI after changing the driver to NV and re-booting?

I think as the command 'nvidia-xconfig' came back with 'no such command' because you don't have the closed source nVidia drivers installed but xorg is still looking for them thus not able to boot the GUI. So by changing xorg the open source NV drivers (which should be installed) you should then have your GUI back and be able to use the normal GUI 'restricted drivers' tool to install and apply the closed source nVidia drivers.

---

### Post by charonred on 2009-12-08
did that in as much as I tried the command, but couldn't make head nor tail of what to do; just not good with command prompt stuff when it goes page after page, can't navigate around.

so that's why I was wondering if I used a live CD, could I edit the xorg.conf via live CD's GUI ? If so, then I'll try tomorrow morning; I've done enough PC for the day, it's up time is 16 hours, and I should watch some TV or something before getting some ZZZZ's

Wouldn't the NVidia closed and open source drivers still be there from the initial install; I assembled PC, then installed 9.04 with NVidia card in place using open source, once at desktop I installed closed source.

---

### Post by charonred on 2009-12-08
Update:
tried a bunch of different scripts from here and google results, but nothing fixed it.

So I dragged the PC into my room, squeezed it into a corner and hooked it up to power, Ethernet etc.

Booted to recovery mode, and selected prompt with networking and did as suggested earlier
```
apt-get install nvidia-glx-new
```
'new' didn't exist, but it listed 4 that did, so re-entered with latest/highest number eg 'nvidia-glx-180' and that got things going; it downloaded the new driver, uninstalled amdccc and installed new nvidia; rebooted and I now have a GUI/Desktop again for both users :D

many thanks bluenova; brother will collect PC later today.

---

