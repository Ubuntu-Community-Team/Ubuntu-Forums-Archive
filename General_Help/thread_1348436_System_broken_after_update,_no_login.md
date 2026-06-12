---
title: "System broken after update, no login?"
date: 2009-12-07
forum: General Help
---

### Post by MugOTea on 2009-12-07
Hi everyone,

I was on my laptop (running Kubuntu obviously) on Saturday night, everything was fine. I shut down and packed it away as normal, there were no errors. Sunday morning I boot the laptop back up, the Kubuntu logo appears (with animated progress bar). The progress animation goes through two stages, bouncing, then filling up. Once it reaches 100%, I just get a black screen with two small white lines a the top (center about 1/2 cm from the very top).

From GRUB I tried normal boot and recovery but both give the same result. The only way I have managed to get so I can input anything is to alter the GRUB and add "rw init=/bin/bash" (as suggested on other threads). I have checked the default gdm/kdm. When set to gdm the same boot procedure occurs but the logo is smaller.

The system is a HP/Compaq 6720s and everything was working perfectly before. I can only presume that something catastrophic has happened or an auto update has caused all this.

I installed from Ubuntu 8.10 disks and allowed the auto updates to do their thing pretty much unattended for the past few month.

(NB: I really hate this keyboard on this windoze system - please help!)

When I watch the boot sequence without the logo, I can see no errors right until the login window is due to be displayed then it says something about the console, I can't see if it is an error or not because then my screen goes blank as described.

I can get to a PROMPT but I am not logged in, how does this work, and is there a repair / recovery command from this point?

I'd love to be able to just restart again from my 8.10 disks but this system has so much on it, and from what I can see the filesystem has not been damaged.

Something I have noticed is that the system does not seem to have FROZEN when I get the blank screen / two white lines. The CAPs key still lights up/off when pushed, and when I press the power button on the system, I wait  few seconds and the laptop powers down after working briefly (the shut down procedure).

---

### Post by MugOTea on 2009-12-07
p.s. I've put KUBUNTU in the post title but that's only because that is the GUI that I use mostly, I still have the GNOME interface and would be happy to use either so long as I can login / get my files back.

---

### Post by MelDJ on 2009-12-07
try typing gnome-desktop or kubuntu-desktop to try to start gnome/kde

---

### Post by Vecho on 2009-12-07
I had similar problem. Try booting from live cd, then sudo gedit, open 
/your_ubuntu_disk/etc/X11/default-display-manager with it and change /usr/sbin/gdm
to /usr/sbin/kdm.

---

### Post by MugOTea on 2009-12-07
Hi,

I tried your suggestion MelDJ, but on the console that I have I am not logged in, even "sudo" does not work "Unable to resolve host: none". Typing either of the commands resulted in a "command not found". Thanks though.

I installed months ago, and I only have the install disk from 8.10 - I've searched everywhere for the live cd. So I am downloading the iso from ubuntu. Only thing is, there only appears to be one iso file available now, there used to be a live/install cd (two seperate iso), if my memory serves? Has ubuntu merged the live and install disk, or am i downloading the wrong thing??? lol

When I have a live CD I fully intend to try your suggestion Vecho.

---

### Post by MugOTea on 2009-12-07
> **Vecho said:**
> I had similar problem. Try booting from live cd, then sudo gedit, open 
/your_ubuntu_disk/etc/X11/default-display-manager with it and change /usr/sbin/gdm
to /usr/sbin/kdm.

The file only has one line and already ends with "kdm", however it is not "sbin" but "bin". Any idea on the difference, should mine read sbin also?

---

### Post by lidex on 2009-12-07
So your system was initially 8.10 upgraded to 9.04, correct? Have you tried ```
startx
``` command at prompt?

---

### Post by MugOTea on 2009-12-07
Hi lidex,

You managed to get my system showing me the Gnome desktop (briefly), then it went away and left some text in the console, most notibly:

xauth: (argv):1: bad display name "(none):0" in "list" command
xauth: (stdin):1: bad display name "(none):0" in "add" command
...
waiting for X server to shut down Dropping master
 ddxSigGiveUp: Closing log

xauth: (argv):1: bad display name "(none):0" in "remove" command

What could have possibly changed my settings over night to cause this?

---

### Post by MugOTea on 2009-12-07
Hurayy!

I got a desktop back, and it was all to do with a KDE update that is being discussed on the following thread, the link below takes you directly to page 3 where i found my solution...

[http://ubuntuforums.org/showthread.php?t=1343012&page=3](http://ubuntuforums.org/showthread.php?t=1343012&page=3)

Thanks for your help everyone!

---

### Post by lidex on 2009-12-07
If you could reconfigure xserver it might help. Try this command:
```
dpkg-reconfigure xserver-xorg
```
then
```
startx
```

---

### Post by ElliottCB on 2009-12-07
Hi, all. I have a similar problem with my Wubi dual-boot. I ran the installation off wubi-installer on-line and don't have a CD. None of the commands suggested work. I have the following:

GNU GRUB version 1.97~beta4
[ Minimal BASH-like editing is supported. (etc)

sh:grub>

No commands at all seem to work. I'm not a terminal expert. I tried ls and it spits out some text in a series of round brackets starting with (loop0) (hd0), etc.

My Linux installation is completely scrude. Can anyone tell me how to get it back up? I HATE having to boot into the-operating-system-that-shall-remain-nameless.

Cheers...
Elliott

---

### Post by lidex on 2009-12-07
This is becoming commonplace.
Read this thoroughly:
[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by lidex on 2009-12-07
> My Linux installation is completely scrude. Can anyone tell me how to get it back up? I HATE having to boot into the-operating-system-that-shall-remain-nameless.

Since wubi installs ubuntu in windows I would imagine windows is where you would fix it.

---

### Post by ElliottCB on 2009-12-08
I tried doing a chkdsk last night as per the guide, but it had no effect, as I suspected. I am fairly sure that Windows has not been shut down unexpectedly during the time-frame in which this happened and that it immediately followed a security update in Ubuntu. I'll try to find a solution again when I have more time, but basically it looks to me as though my Ubuntu installation has just unilaterally broken.

---

### Post by ElliottCB on 2009-12-17
I give in. It can't be fixed. Looks like I'm stuck with Windows.

---

### Post by lidex on 2009-12-17
You can always download and burn a LiveCD and do a regular install. Or even order the cd.

---

