---
title: "Ubuntu freezes any time I go near a GUI, please help"
date: 2011-07-28
forum: General Help
---

### Post by nerocr on 2011-07-28
This was originally an installation problem of mine. I initially thought it was a problem with my disk(s) as the live cd install tended to freeze right around the partitioning screen. However, I later noticed that the live cd would freeze about a minute in, regardless of what I was doing. I managed to get a successful install of ubuntu by using the alternate install cd. Everything booted fine. However, about a minute in, ubuntu freezes and I have to do a hard reboot.

I figured it must have been something to do with my video card because the ubuntu logo on boot was just a bunch of visual artifacts. My ram passed the memory test fine, and seems to be fine on windows so I decided to rule that out. (I also ruled out my disk, because I eventually ended up trying to install ubuntu on 3 different hard disks, all with the same result.)

So I decided I needed to install my video drivers (nvidia geforce 8600 gts) by booting directly to bash and installing them from the command line.

So I booted, pressed ctrl + alt + f1 during boot to get to bash. As I suspected, nothing froze. I removed the default video drivers by doing "sudo apt-get --purge remove xserver-xorg-video-nouveau", (as I had read about online). I then tried installing the nvidia driver package with "sudo apt-get install nvidia-current", however it froze mid-installation, and I had to do a hard reboot. 

With the default video drivers gone, I could actually see the ubuntu loading logo on boot. When I got to the login screen things felt a bit better, but once again, it froze about 1 minute in. So I booted directly to bash once again. When I tried to install the nvidia drivers again, apt told me to run "sudo dpkg --configure -a" to compensate for the interruption of the last installation. It began installing the nvidia drivers once again, and froze...again.

I know my video card is solid. It's a little old, but my windows xp installation works great and I'm able to run high quality games without issue.

(I've also tried burning and installing multiple different cd's, including different versions and even different distros (lubuntu). All with the same result.)

Once again, I very much suspect that this has something to do with my video drivers not being installed. Is there anyway I could install them at a lower level to ensure they work?

specs:
DFI Infinity 975x/g motherboard
intel core 2 duo e6600
nvidia geforce 8600 gts
2gb of ram and multiple different disks used throughout this situation

Help would be **much** appreciated.

---

### Post by Wayne_V on 2011-07-28
I think nvidia-current is the binary driver from nvidia.   I would try first with just the opensource driver from Xorg.  It should be installed already (xserver-xorg-video-nv).  Just purge nvidia-current and try it.

---

### Post by nerocr on 2011-07-28
> **Wayne_V said:**
> I think nvidia-current is the binary driver from nvidia.   I would try first with just the opensource driver from Xorg.  It should be installed already (xserver-xorg-video-nv).  Just purge nvidia-current and try it.

Thanks. Sorry I probably should have been more concise when asking. My setup *was* such that it only included the "xserver-xorg-video-nouveau" driver without any nvidia drivers. I think that was the problem in the first place.

I'm really lost at this point. If this is a video problem, why would the installation of nvidia-current freeze on the command line? I don't even know that this is a driver problem, it seems like it would be though.

---

### Post by Wayne_V on 2011-07-28
ah - I see ubuntu switched to -nouveau as the default.   If you are having problems with nouveau, I would try removing that and installing -nv first, before trying any of the nvidia-xxx drivers.

Once you get X working with an Xorg driver, then use the Hardware Drivers utility to install the correct proprietary one.

---

### Post by nerocr on 2011-07-28
> **Wayne_V said:**
> ah - I see ubuntu switched to -nouveau as the default.   If you are having problems with nouveau, I would try removing that and installing -nv first, before trying any of the nvidia-xxx drivers.

Once you get X working with an Xorg driver, then use the Hardware Drivers utility to install the correct proprietary one.

Alright, I'll give it a try and report back. Thanks.

edit: I'm not sure it's specifically nouveau though, I think it might be a lack of nvidia drivers entirely. Even with nouveau uninstalled completely, things still froze. Also, why would the nvidia-current installation freeze on the command-line? I can't figure it out. :( (The command-line doesn't freeze otherwise by the way, I could leave it on all day. I can even install other packages. But as soon as I install nvidia-current, it freezes.)

---

### Post by Wayne_V on 2011-07-28
but with -nouveau removed you were using nvidia-current, right?   It's possible nvidia-current may not be the correct one for your card.  nvidia.com says the 8600 gts should use version 275.   If the Hardware Drivers utility doesn't recommend that one, try adding the Ubuntu X updates repo ([https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates)) and try it again.   If nothing else, remove all the nvidia-xxx packages and install version 275 from nvidia.com (using the command line installer).

---

### Post by nerocr on 2011-07-28
> **Wayne_V said:**
> but with -nouveau removed you were using nvidia-current, right?

I'm not sure, the install never completed.

> **Wayne_V said:**
> It's possible nvidia-current may not be the correct one for your card.  nvidia.com says the 8600 gts should use version 275.   If the Hardware Drivers utility doesn't recommend that one, try adding the Ubuntu X updates repo ([https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates)) and try it again.   If nothing else, remove all the nvidia-xxx packages and install version 275 from nvidia.com (using the command line installer).

I believe nvidia-current is 270, which should at the very least work with my card. I tried using the installer from nvidia.com, it started complaining about x not running.

---

### Post by nerocr on 2011-07-28
Okay, I think I may have fixed my problem to a degree (thanks to Wayne_V). I'm happy to report I'm typing this in a fresh ubuntu installation.

For anyone with a similar problem, this is what I did:
Install ubuntu, during first boot, press ctrl + alt + f1.
sudo apt-get --purge remove xserver-xorg-video-nouveau
sudo apt-get install xserver-xorg-video-nv
sudo reboot

The xserver-xorg-video-nv driver seems to allow me to use ubuntu without freezing every 30 seconds. However, I'm wondering what to do next. The driver itself seems sort of subpar (dsappearing mouse cursors etc). I'm debating whether to install official drivers lest the installation fail and I have reinstall the entire OS again.

edit: apparently I spoke too soon. Things have started freezing again. I'll try to avoid making assumptions in the future. I'm not sure what to do now.

---

### Post by Wayne_V on 2011-07-29
sounds like you are not the only one having issues with the 8600 series card:  [http://ubuntuforums.org/showthread.php?t=516552](http://ubuntuforums.org/showthread.php?t=516552)

I would say:

Stop X (sudo /etc/init.d/gdm stop)

download the latest 275 command line installer from nvidia.com and try that.

---

