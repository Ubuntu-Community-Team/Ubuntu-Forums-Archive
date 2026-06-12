---
title: "Force console video mode with Grub2 - no monitor"
date: 2010-03-25
forum: General Help
---

### Post by BillRebey on 2010-03-25
[Posted a couple days ago in 'Multimedia and Video'...no bites.  Trying again here]

I have a very annoying problem, and I'd appreciate any help I can get.

Background: I run a number of Ubuntu 9.10 boxes attached to multiple daisy-chained KVMs. None of the PCs are using any GUIs - they all run in console mode. I often reboot them remotely via an SSH session, etc.

Problem: If a monitor isn't actually active on the PC when it reboots, Grub2 uses a low-res video mode, despite having a higher-res video mode set correctly in Grub2's configuration.

If I reboot WHILE THE MONITOR is attached to the Ubuntu PC via the KVM, the video mode is set correctly as configured in Grub2's config files.

If I reboot WITH NO MONITOR attached, the video mode is ignored and I'm stuck in a low-res mode next time I attach to the PC via the KVM.

How can I force Grub2 to honor the configured graphics setting, despite not having a monitor present at the time it boots?

Thanks for any help - this is a very aggravating problem.

(If there is a better forum on which to post this, please advise!)

---

### Post by dcstar on 2010-03-26
> **BillRebey said:**
> 
..........
How can I force Grub2 to honor the configured graphics setting, despite not having a monitor present at the time it boots?

Thanks for any help - this is a very aggravating problem.

(If there is a better forum on which to post this, please advise!)

This might give you some hints on what to experiment with:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/512245](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/512245)
and
[http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html](http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html)

---

