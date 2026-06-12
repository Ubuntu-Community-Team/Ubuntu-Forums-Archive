---
title: "Ubuntu Crashed and Cannot Re-install"
date: 2012-01-06
forum: General Help
---

### Post by PsyclonJohn on 2012-01-06
Just the other day, one of my laptops wouldn't start up, it was duel booting with Windows Vista, and I kept getting the grub bash line screen. I've gotten this before, and always resulted in uninstalling Ubuntu and re-installing. Well, when attempting to uninstall, I received an error about a missing file, and it wouldn't finish. 

When booting up, it boots straight into Windows, which is a sign that Ubuntu is no longer there. So, I tried to install it again, but there is no option to install with Windows. I've tried both WUBI and LiveCD, and I don't want to wipe the hard drive at all.

I've looked into partitioning, and when attempting to partition the HD, it said something like "Creating a new partition will wipe the hard drive", so I didn't go for that option. I've tried some other linux OS's, such as Linux Mint 11, CentOS, and Debian 6, and they all only had "Wipe and install" features available.

Can someone please help? I'd like to have Ubuntu running on this machine, but at the same time keep Windows (I hate Windows, but I use it for audio production and PC games).

Thanks, 

John

---

### Post by PsyclonJohn on 2012-01-06
I would also like to mention that nothing will install on Windows, so would you say it was a Windows issue or a hard drive issue?

---

### Post by x C0MMAND0 x on 2012-01-06
Hmm...Just thinking "out loud" here, if nothing will install within Windows, I would think there would be a problem with your Windows Installation.

As far as not being able to install Ubuntu (or another Distro), that is very odd.  Most of them have a "side by side" install option and will install allowing you to dual boot your system.  Are you saying you don't see an option for this?  If you are booted through a Live-CD, does it detect that you have Windows installed already?

If you can somehow get a screenshot of what the live installer options are, that would be very helpful.

Lastly, if you think you might have a hard drive physical problem, does your system have a built in diagnostics option boot that you can run?

Just some thoughts/ideas to try and help

---

### Post by PsyclonJohn on 2012-01-06
Thanks for the reply!

That's exactly what's happening, the 'side by side' feature isn't displaying at all. I just tried an Ubuntu 11.10 disk, and that even didn't have the feature available. I tried it because I do remember how the 11.10 CD was setup (update, side-by-side, and wipe hard drive), but all it had was 'wipe hard drive'.

Also, it does say I have Windows installed when running the LiveCD (some OS's had the option to manually partition, but ended in wipe HD).

-
John

---

### Post by x C0MMAND0 x on 2012-01-06
If you look at [this link]("http://www.psychocats.net/ubuntu/installing"), One of the pictures shows an option for "Install Ubuntu 11.10 Along Side Windows".  You don't see that, correct?

You also said that the installer detects Windows still?  I guess one thought would be to shrink your Windows partition (if possible) from within Windows, and then install Ubuntu to the unallocated space which would then show up on the installer.

EDIT - Check out [this link]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/") for partition shrinking in Vista.  As always, make sure you have a verified backup before messing with anything.

---

### Post by PsyclonJohn on 2012-02-13
I know this is about a month old now, but I wanted to respond back on how I fixed this issue. 

I went into windows and renamed the broken installation as broken_ubuntu in the programs, and instantly I was able to use wubi again and successfully install Ubuntu.

Why did this happen? Still unknown!

---

