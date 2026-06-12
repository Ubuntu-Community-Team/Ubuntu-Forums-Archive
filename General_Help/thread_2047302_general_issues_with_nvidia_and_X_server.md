---
title: "general issues with nvidia and X server"
date: 2012-08-24
forum: General Help
---

### Post by kryrinn on 2012-08-24
I recently set up an older box, meaning to use it as a mythtv/media central, but I've been fighting with the graphics.  At first, I was only getting a black screen, then I was able to get to unity using nomodeset, then installed nvidia drivers and it booted up right into unity (yay! albeit it taking 20 minutes to boot), and now something broke.  

Yesterday I installed handbrake, and libdvdcss and ripped some dvds, and this morning my mouse was gone so I restarted.  I can't bypass anything into the menu where I enter the nomodeset, and it's going straight to a command line.  I tried purge/reinstall/reconfig of the nvidia drivers, each fails to bring back unity.  'startx' gives a fatal error of "no screens found".  I tried backing up xorg.conf, and using the failsafe file, which also fails to get X to start.  I did get one funny error:

"Error: API mismatch: the NVIDIA kernel module has version 304.37, but this NVIDIA driver component has version 295.49."

I used both nvidia-current, and nvidia 173.  I was able to purge nvidia-current, but 'apt-get purge nvidia*' didn't get any files.

I need to fix this so it routinely boots into gui, and maybe make it boot faster?

---

### Post by alan21276 on 2012-08-24
I had a similar issue with a recent update breaking my nvidia driver and causing a near identical problem to your's, all the usual fixes didn't work for me either....

I downloaded the latest driver from the nvidia website and installed using the nvidia installer from a tty console.

So far my system has been more stable than ever.

Maybe worth a try.......unless you've already tried this.

---

### Post by alan21276 on 2012-08-24
sudo apt-get purge nvidia*

should remove all the nvidia packages.

perhaps something is broken somewhere.

sorry in advance if this isn't much help.

---

### Post by kryrinn on 2012-08-24
I tried the purge while sudo and it said "coudn't find package named nvidia". So I hope it's gotten them all out of it's system, I'll try with the newer drivers again.

---

### Post by SeijiSensei on 2012-08-25
Are you also running Hardy on this box?  If so, the desktop version reached end of life in [May of 2011]("https://wiki.ubuntu.com/Releases") which may be the cause of version mismatches.

I'd consider upgrading to 12.04.

---

### Post by ullix on 2012-08-25
I am using two older computers with older nvidia GPU as frontends for mythtv. Both replayed videos and tv well when using the nvidia drivers 295.?? and earlier. The computers are running Ubuntu 10.04 and 12.04.

But now I upgraded the nvidia driver to 304.37, and both show the same behaviour: at fully 100% CPU load video replay is stuttering; impossible to watch anything any more.

Did someone else noticed a regression in this latest driver?

---

### Post by SeijiSensei on 2012-08-25
If your player is using hardware acceleration via VDPAU, you shouldn't see CPU usage figures anywhere near 100%.  That's the whole point of using hardware acceleration.  If the cards have 8xxx or later NVIDIA chips, make sure your player is set to use VDPAU as the output driver.

---

### Post by ullix on 2012-08-27
my cards are GeForce 6 series, i.e. well before any vdpau. But as I said, they were playing video just fine at about 30-40% CPU.

The computer on 12.04 with nvidia driver shows 100% cpu load and badly stuttering video. This occurs with nvidia drivers 173.14.35, 295.40, 295.49, and 304.37. When this computer was on 10.04, the driver 302.17 was the one working well (and some older ones too).

Now video performance under nvidia driver is just as bad as with nouveau, unacceptable for viewing.

---

