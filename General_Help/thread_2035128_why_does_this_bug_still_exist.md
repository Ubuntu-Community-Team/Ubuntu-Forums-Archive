---
title: "why does this bug still exist?"
date: 2012-07-29
forum: General Help
---

### Post by ant2ne on 2012-07-29
[http://blog.computerant.com/2010/03/22/grub-2-bug/]("http://blog.computerant.com/2010/03/22/grub-2-bug/")

As I ranted back in 2010...

> This bug is very Windows’ish in its annoyance. If for some reason the computer crashes or is improperly shutdown then the computer will hang at its grub menu selection
```

    GNU GRUB version 1.97~beta4
    Ubuntu, Linux 2.6.31-14-generic
    ubuntu, Linux 2.6.31-14-generic (recovery mode)
    Memory test (memtest86+)
    Memory test (memtest86+, serial console 115200)
```

etc

But there is no countdown for a default boot. It just hangs here… Indefinitely… Until someone at the console makes a choice by pressing the enter key with “Ubuntu, Linux 2.6.31-14-generic” highlighted (default).

This is unacceptable!! I need these systems to continue to boot and get back on line regardless of the reason they were powered off. If the server is rebootable, then by all means, let it boot! I see no reason to physically access it and manually boot it. Perhaps once network is restored, an admin can then ssh into the device and repair whatever brought the server down in the first place. Or maybe it was just a simple power failure, and once the power is restored the server should boot right back up so customers can access the server and the commerce can continue. Maybe the server goes down at midnight and it takes several hours to get the IT guy out of bed and into work and to the data closet, where he has to scrounge up a keyboard and monitor and plug it all up so he can hit the enter key. Of course, this will all be overtime for the IT guy, and possibly after hours charges would apply. Forcing someone to physically access the device just to hit the enter key is ridiculous, and the grub2 developers should be ashamed. Have I expressed, sufficiently, how dumb this feature is?Unfortunatly it appears that my previous fix isn't working and now I need to find a new one.

---

### Post by 3rdalbum on 2012-07-30
> **ant2ne said:**
> [http://blog.computerant.com/2010/03/22/grub-2-bug/]("http://blog.computerant.com/2010/03/22/grub-2-bug/")

As I ranted back in 2010...

Unfortunatly it appears that my previous fix isn't working and now I need to find a new one.

a. I've never observed that, and yes I run a home server that's not on a UPS and definitely uses GRUB 2. I also have a desktop running GRUB 2 that has been suspended and then unplugged by accident. So I'd imagine it can't be a common problem, one that would be noticed by GRUB developers, which leads me to the second point...

b. Did you just rant, or did you file a bug report?

If I were you I'd check to see if the GRUB developers are aware of this behaviour; and if they're not, then please file a bug report, giving as much information as possible.

If you filed a bug report back in 2010 and are now using a later version of GRUB 2 (or the version you were using is still the absolute latest), then I'd post a comment onto the bug report just saying "This problem still exists", to keep the bug report alive. Sometimes, developers see a bug report for an older version and they think "Well, this might have been fixed in the latest version" and ignore it. I'm not saying that's the best thing for them to do, but I'm sure it happens...

---

### Post by dcstar on 2012-07-30
Grub 2 autoboot will be interrupted by a Shift Key character being input before the menu times out.

If some hardware fills the keyboard FIFO with random rubbish on reboot that happens to interrupt Grub then it is not the fault of the software, it is a problem with the hardware.

Fix/upgrade the BIOS so it doesn't throw rubbish at Grub or get some hardware that doesn't behave like this.

---

### Post by ant2ne on 2012-07-30
I have seen this issue with all of my grub2 systems. In fact, I see at at least once and then make the changes in the work around and then I don't think about it again until I install a new system. It is most often when the system shuts down unexpectedly, or thinks it was shut down unexpectedly. But it has happened sometimes on normal reboot.

It appears that this bug has already been reported several times.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/797544]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/797544")

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/512593]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/512593")

[http://ubuntuforums.org/showthread.php?t=1364220]("http://ubuntuforums.org/showthread.php?t=1364220")

On the bright side, during the research of those links I figured out why my recent attempt failed. I think I forgot to run the  sudo update-grub command after making the changes in the work around. 

I still maintain that this should not be the default behavior. Particularly in a server install. If the system will boot, by all means let it. A server need not just hang waiting for a technician to bring a monitor and keyboard just to push the damn enter key!

This is not a BIOS issue. This is a "feature" by design.

---

### Post by Frogs Hair on 2012-07-30
That kernel goes back to Karmic 9.10 (unsupported/EOL). does  the problem still apply to newer versions ?

---

### Post by ant2ne on 2012-07-30
Yes. I asked why this bug still exists. But I wasn't specific. My latest complaint is on a 12.04 system.

---

### Post by pbpersson on 2012-07-30
Does this bug in grub affect all Linux distros or just Ubuntu?

Is there any news on whether it is being worked on or when it will be fixed?  Are these bugs given a priority or a place in the overall bug queue?

---

### Post by ant2ne on 2012-07-30
I'm thinkin I recall seeing it in a debian install. I'm pretty much always  mint/ubuntu. And the ubuntu mint. I will need to review those bug links (above) but if it has been nearly 2 years I don't think grub devels care too much.

---

### Post by ant2ne on 2012-10-31
Just installed 12.04 on a new server. Upgraded. Bug still exists.

I also happened to notice that a VirtualBox VM hung at this screen causing the physical CPU to hang at 100% until I could get past the screen. Probably not good to run the CPU at 100% for a long time.

---

