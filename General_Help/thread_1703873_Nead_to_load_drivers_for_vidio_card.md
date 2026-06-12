---
title: "Nead to load drivers for vidio card"
date: 2011-03-09
forum: General Help
---

### Post by Jon Anderson on 2011-03-09
This is the problem I run" lspci -v" which checks all drivers on my system and more. It says kernel driver in use:  nouveau
then under that it says kernel modules: nvidia recent,nvidia-96,nouveau,nvidiafb
So what it looks like I have 3-4 drivers for my video card loaded and one, nouveau,  being used.  I think they conflict with each other. I'm trying to add drivers other then nouveau, because the mouse freezes with nouveau. At this point I can't seem to get rid of nouveau, I go to terminal and type"sudo apt-get --purge remove xserver-xorg-video-nouveau" and it says that it's not loaded so I can't dump it. "lspci-v" says nouveau is the driver being used and trying to dump it it says it isn't installed. ?????????confused. I want to dump nouveau, what should I do? I also go into Synaptic package manager and it isn't listed as being installed. All help exepted!

---

### Post by wojox on 2011-03-09
Did you try System > Admin > Hardware Drivers?

---

### Post by Jon Anderson on 2011-03-10
> **wojox said:**
> Did you try System > Admin > Hardware Drivers?
Ya, first thing, when I do that the Nouveau driver gets in the way(conflict) and now I can't dump them because when I do I get the message that they are not installed in the first place but when I"lspci -v" in terminal it says that nouveau are the drivers installed.

---

### Post by lithopsian on 2011-03-10
There is also a nouveau kernel module, a standard part of the Ubuntu kernel.  You must prevent this from loading or things get very confused.  The standard way is to blacklist it in the modules blacklist file.

---

