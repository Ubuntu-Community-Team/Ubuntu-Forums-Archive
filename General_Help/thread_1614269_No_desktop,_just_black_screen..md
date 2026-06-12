---
title: "No desktop, just black screen."
date: 2010-11-05
forum: General Help
---

### Post by rdh61 on 2010-11-05
Hi,

This morning I did some recommended updates for Lucid with update manager. This afternoon at start up I get a black screen after booting. I can hear the sound effect for the login, and if I key in my password, I hear the Ubuntu signature tune, i.e. it is booting and starting up. But my screen is just black with the arrow-shaped pointer, which I can move across the screen with the mouse. Other than that, nothing. Please, how can I get my deskop back?!

Many thanks.

---

### Post by drs305 on 2010-11-05
It could be a video driver problem caused by the update. If you are using Grub2, at the boot menu press "e" and edit the menuentry. Go to the "linux" line and add **nomodeset** to the end of the line (probably after "quiet splash"). Press CTRL-x and see if it now boots.

If it does, you may have to reinstall your video drivers via System, Administation, Additional Drivers/Hardware Drivers.

You could also try an older kernel if you have that option in your boot menu.

---

### Post by rdh61 on 2010-11-05
Hi,

Thanks for the answer. but nomodeset doesn't work, neither does booting into an older kernel.

A question of some importance to me is this. If I can't get my desktop back, is there any way I can access and back up my files onto an external disk? I have verified that Ctrl+Alt+F1 brings me up a terminal. 

Thank you.

---

### Post by drs305 on 2010-11-05
Have you tried booting into the Recovery mode? From there, choose the option to boot into a failsafe graphic mode (or equivalent).

As far as retrieving files, you can mount your Ubuntu parition from the LiveCD and then access them with the file browser. Open your browser and look under Filesystem, mnt.  

You can then copy them to an external drive or another partition.

Substitute your Ubuntu partition for **XY**. If you aren't sure which partition is your Ubuntu partition, run "sudo fdisk -l" (lowercase L) and look for the "Linux" partition.
```
sudo mount /dev/sd**XY** /mnt
```

---

### Post by B.Blackbird on 2010-11-05
I've got the same problem on my old notebook and adding "i915.modeset=0" in the GRUB-bootline did the trick for me. Not sure if it is releated to that weird bug with some Intel-Chipsets, my workaround-driver doesn't seem to work properly anymore since the update from yesterday.

---

### Post by rdh61 on 2010-11-05
@ drs305:-

Thanks. Booting into recovery mode (failsafe graphic mode) worked. Should I now try to uninstall my updates of this morning?

---

### Post by rdh61 on 2010-11-05
@ B.Blackbird:-

Not sure if this is the same issue (I too have intel chipset), and i915.modeset=1 (not 0) worked for me when I originally installed Lucid and until this afternoon, but this was to resolve a different kind of behaviour (i.e. no boot, and crashes) in my case. However, the latest does seem likely to be part of the same intel related problem.

---

### Post by drs305 on 2010-11-05
> **rdh61 said:**
> @ drs305:-

Thanks. Booting into recovery mode (failsafe graphic mode) worked. Should I now try to uninstall my updates of this morning?

Have you checked your drivers? If you know what you had before, you may need to reinstall them again via System, Admin, Additional Drivers/Hardware Drivers.

I'm not a video expert. *B.Blackbird* may come back and tell you which drivers you need to install or how to modify your system now that you have it back up. 

I think now that you know how to get back into your system I would tend to try to install any *new* updates before trying to remove older ones. A fix may already have been introduced if there were widespread problems with it. Of course, if you can't fix it you may have to roll back the update.

---

### Post by B.Blackbird on 2010-11-05
Initially I followed [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes") using an updated driver because otherwise my Intel GM855 didn't show anything or was terrible unstable and kept crashing. But there seems to be a wide variety of behaviors with this bug. 

After using the workaround with the alternate driver everything worked fine - since the last driver update from that Glasen-repository for *xserver-xorg-video-intel* that happened yesterday or so.

I now restored the original *xserver-xorg-video-intel* from the Ubuntu repository and it it works out of the box again.

Not sure if this highly specific solution helps anyone else. ;)

---

### Post by rdh61 on 2010-11-06
> **B.Blackbird said:**
> Initially I followed [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) using an updated driver because otherwise my Intel GM855 didn't show anything or was terrible unstable and kept crashing. But there seems to be a wide variety of behaviors with this bug. 

After using the workaround with the alternate driver everything worked fine - since the last driver update from that Glasen-repository for *xserver-xorg-video-intel* that happened yesterday or so.

Yes, that is exactly my case history, too.

> **B.Blackbird said:**
> 
I now restored the original *xserver-xorg-video-intel* from the Ubuntu repository and it it works out of the box again.

Please could you, or somebody, tell me how to do that (easy steps, please)?

Many thanks. :P

---

### Post by rdh61 on 2010-11-06
OK, I got my brain back into gear and used the code available at:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Now back in working order.

Thanks B.Blackbird and drs305! :P

---

### Post by B.Blackbird on 2010-11-08
The package **xserver-xorg-video-intel** from ppa.launchpad.net/glasen has now appeared in a new version and this driver seems to be somewhat faster than the one in the Ubuntu repository. 

Of course my computer is quite old and only used as a secondary unit but it runs smoothly with the Glasen-driver, the one from Ubuntu which I used due to the bug felt sluggish and I could watch how windows appeared piece after piece. Also there was constant load on the CPU, thats gone now, too. 

So I would recommend to switch back to the alternative driver from Glasen since it runs much better and the bug seems to be removed. 

To the question how you switch package versions:

You can do this with Synaptic. Search for "xserver-xorg-video-intel", go to "package" in the menu on the top and if you have more than one version available you can select "force version" to choose the one you want to use - quite simple. :)

---

