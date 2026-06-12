---
title: "Ubuntu desktop won't load - only a flashing gray box"
date: 2012-09-11
forum: General Help
---

### Post by ksoth on 2012-09-11
Hello,

I am running Ubuntu 10.04 on a Lenovo W520 laptop with nVidia Quadro 2000M graphics.

Everything was working fine (mostly) for a while. I was having a problem, though, with the mouse not working after resuming from sleep/suspend. I did some research and saw some suggestions to install uswsusp. I did, but it didn't seem to work, so I removed it.

However, after this, the desktop won't load. I can't think of anything else I did besides uswsusp between it working and not. I can't say for sure that caused the problem, but it's all I can think of. Here is a video of what I am seeing

[http://www.youtube.com/watch?v=9TxSZTFBVHg&feature=youtu.be]("http://www.youtube.com/watch?v=9TxSZTFBVHg&feature=youtu.be")

This is all I see when the desktop loads. I can't log in or anything. No commands work, and I have to hold the power button down to do anything. I've tried searching for solutions but couldn't be sure what I found was referring to the same type of problem.

If I start in recovery mode, the 'start in failsafe X mode' doesn't work. It just goes back to the recovery menu, and a normal resume kicks me to the command line.

If I then do 'startx', X starts, I see the nVidia logo, the background shows up, but the mouse cursor just flashes between the pointer and the loading circle shape. Nothing happens.

I have removed and reinstalled xserver-xorg and all the dependencies, and the nVidia driver. Nothing works.

I can't re-install Ubuntu. I am dual booting with Windows 7 and have Symantec PGP whole disk encryption, and reinstalling Ubuntu will hose the boot loader and the encrypted partitions will be unreachable. I also have to be careful about what sort of repair type operations are done, as before that has hosed the system, too. I have to run version 10.04 because it is the only kernel that the PGP software supports.

The grub boot loader provides me with options to boot into 3 kernel versions. None of them work.

I am at an impasse on what else to do. Any ideas?

I also can't seem to get any internet working from the command line. eth0 doesn't show up in ifconfig and modprobe doesn't seem to do anything. The wirless card can see the wireless networks, but I can't seem to get the WPA2 protected one to work, and the open one displays a terms of use acceptance webpage that needs to be clicked before it will work, which I don't know what to do in command line to do this. But anyways the DHCP request for this just keeps listening but quits with it saying it couldn't get anything, maybe for the above reason. So, without network I can't do apt-get type commands to install stuff...

Any help would be appreciated.

---

### Post by ksoth on 2012-09-13
Sorry for the bump... Any thoughts would be appreciated.

---

