---
title: "Restarting X or GDM vs. full system reboot - what's the difference?"
date: 2010-11-27
forum: General Help
---

### Post by raptx on 2010-11-27
Here is my problem, that applies to all kinds of video playback: flash in firefox, individual files in vlc, totem, etc. After a fresh boot, all video is fine and good. But when I suspend and then come back, all video becomes choppy. I reboot, and everything is fine all over again. I assume then that this means some settings somewhere, perhaps related to x, display driver, etc. are being screwed up after resuming from suspend, but get set to the correct defaults after a fresh reboot. My question is, what kind of settings these might be, and how can I implement a fix without having to reboot the system. I've tried restarting x and gdm, changed settings to some files, etc. re logged on...and so on, but nothing works. A full restart is the only thing that seems fix this. So, what is restarting the system doing that x restart is not doing?

I'm running 10.10 maverick 32-bit on a 64-bit thinkpad t410. It has nvidia 3100m optimus, and I'm using the nvidia drivers. A similar problem occurs when I don't use the nvidia drivers (although in that case, the standalone video files are fine even after suspend, but the videos in browsers gets choppy and that requires a reboot).

Hope someone can help me out here.

---

### Post by Ocxic on 2010-11-27
Restarting X will restart/reset the Graphic display system. where as restarting the system will reset all running services, and applications. If you want, you can definitely try restarting X before rebooting, you issue may be reserved to the graphic system, and a reboot may not be required.

---

### Post by raptx on 2010-11-27
But the problem is that restarting X alone doesn't work. only a full reboot does. Since the problem only starts when I resume from a suspend action, I'm assuming it is related to the display settings (are there other things that could be screwed up when coming back from suspend?). So that's why this is confusing...

One of the things I've tried is doing a diff on some of the config files (e..g. xorg.conf) before and after suspend, but there's no difference. The settings in the video players seem to be the same before and after also. I'm trying to figure out what it is that a full reboot is fixing here.

---

