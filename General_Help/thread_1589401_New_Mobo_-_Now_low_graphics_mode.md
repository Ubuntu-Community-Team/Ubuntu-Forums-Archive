---
title: "New Mobo - Now low graphics mode"
date: 2010-10-06
forum: General Help
---

### Post by Drainy on 2010-10-06
Hey,

So my mobo (X58A-UDR3R Rev 1) packed up on me completely, got it replaced with a Rev 2 model. Have been using Windows alot as of late, anyway I went to load Ubuntu today and the first thing it displays is;
Ubuntu is running in low-graphics mode.

Failed to load usr/lib/xorg/extra-modules/libglx.so
Failed to load module "glx" (loader failed, 7)
NVIDIA: Failed to load the NVIDIA kernel module
a few more lines about nvidia.. and
No drivers available.

Now I assume that this is probably due to the re-connecting of hard drives in a different order, possibly because the addresses are different on this motherboard. Either way, does anyone know an easy work around to fix this?

It has a mouse cursor on the screen, but the mouse is no responding. The Ok button on the dialogue is also highlighted but the keyboard is also un-responsive.

---

### Post by Drainy on 2010-10-07
Anyone with any suggestions? I'm open to trying anything at the moment.

---

### Post by coffeecat on 2010-10-07
> **Drainy said:**
> Now I assume that this is probably due to the re-connecting of hard drives in a different order, possibly because the addresses are different on this motherboard. Either way, does anyone know an easy work around to fix this?

I wouldn't have thought that the order of the hard drives has anything to do with it. What do you mean by the addresses being different? The file /etc/fstab (and grub) uses UUIDs to identify partitions so it doesn't matter whether sda becomes sdb and vice versa.

The error message is about a failure to load the nvidia kernel module. What graphics chipset are you using? How did you originally install the proprietary nvidia driver? Have you tried re-installing it?

---

### Post by Drainy on 2010-10-07
Hey,

The addresses was just a wild stab in the dark, I don't know how Ubuntu references these.

I can't get any access to anything as the mouse and keyboard refuse to do anything, this appears to have only happened because I have installed a new Motherboard (albeit a new version of the old one)

---

### Post by oldfred on 2010-10-07
New motherboard's defaults may account for mouse. Check USB mouse/keyboard settings in BIOS.

Also check if IDE compatibility mode is set in BIOS.

If you can get a grub menu or use shift to get grub menu use e for edit and add nomodeset in place of quiet splash. 

If you can boot to low graphics check System, Administration, Hardware Drivers to see if you can install the Nvidia driver.

---

### Post by coffeecat on 2010-10-07
> **Drainy said:**
> I can't get any access to anything as the mouse and keyboard refuse to do anything, this appears to have only happened because I have installed a new Motherboard (albeit a new version of the old one)

This is most unusual. Linux is very tolerant to being booted up in a completely different hardware environment to what it was installed in because hardware gets probed during bootup and appropriate drivers installed. The big exception is when you install nvidia or ati proprietary drivers which write a custom xorg.conf which can complicate things. Which is why I asked about your graphics card and driver.

I should imagine something may have happened coincidental to changing the motherboard - but I keep an open mind. Let's see what we turn up.

OK - you can boot into low graphics mode but the mouse and keyboard won't work. All consistent with a video driver problem. You will probably  have to boot up in recovery mode to rescue this system from a root console. Post details of graphics chipset on the new motherboard and what driver you previously installed and we can take it from there.

---

### Post by Drainy on 2010-10-07
Hey,

Sorry, I forgot to post, I have a NVIDIA GeForce GTX 260, but this is the same card that was present before.
No on board graphics with this mobo.
Thanks for the suggestions, I will go and try them now and post back.

---

### Post by jeebustrain on 2010-10-07
regarding the low graphics issue - that happens occasionally to me with certain kernel updates. I use the closed source Nvidia driver. I just boot into low graphics mode, launch the Hardware Drivers app in settings, remove/readd the Nvidia drivers and reboot. This fixes it every time.

---

### Post by Drainy on 2010-11-15
Hey,

So some time has passed and I have only just got the time to try and solve this.
But I have hit a fairly basic problem, how do I boot into recovery mode? :/

I have been trying esc but it just continues to load until it eventually completely freezes at the previously mentioned error

---

### Post by coffeecat on 2010-11-15
> **Drainy said:**
> I have been trying esc but it just continues to load until it eventually completely freezes at the previously mentioned error

I presume you are trying to get the grub hidden menu. Your profile says you are running 9.10. If this was a fresh install of 9.10, not an upgrade from an earlier version, the you will have grub 2 for which you need to press the shift key, not escape to get the grub menu.

---

### Post by Drainy on 2010-11-15
Hi,

It was a fresh install but the top of the screen says Grub 1.98.
Pressing esc or shift are producing no results. When should I be pressing it?
I have tried before the grub menu loads, while its on the screen and after selecting Ubuntu (there are a few old kernel versions and then an option for Windows on the menu)

---

### Post by Drainy on 2010-11-15
Right, i've stopped being stupid.
When recovery mode is loading it stops dead with this message;

init: udevtrigger main process (505) terminated with status 1
init: udevtrigger post-stop process (509) terminated with status 1
init: udevmonitor main process (503) killed by TERM signal

---

