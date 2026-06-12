---
title: "Problem with boot on external HDD"
date: 2009-11-22
forum: General Help
---

### Post by MiniStephan on 2009-11-22
Hello, all!

I've been using Jaunty (and now Karmic) on my laptop, running it off of my external HDD.  I probably did this in a way that people wouldn't normally, treating my ExHDD as a normal HDD in my computer.  Anyway, the problem is, my laptop developed hardware issues, and I've had to start using my backup computer.

I got a SuperGrubDisk so that I could get it to work (I was getting GRUB Stage 1.5 Error 15 otherwise), but when it's nearly done booting, it starts flashing between two screens; one with more boot things on it and the other with some boot stuff and my login in tty1.

My description probably hasn't included enough information, but if you have _any_ idea of how to fix it, it would help.  I really hate using the Vista on this computer.

---

### Post by dcstar on 2009-11-22
> **MiniStephan said:**
> Hello, all!

I've been using Jaunty (and now Karmic) on my laptop, running it off of my external HDD.  I probably did this in a way that people wouldn't normally, treating my ExHDD as a normal HDD in my computer.  Anyway, the problem is, my laptop developed hardware issues, and I've had to start using my backup computer.

I got a SuperGrubDisk so that I could get it to work (I was getting GRUB Stage 1.5 Error 15 otherwise), but when it's nearly done booting, it starts flashing between two screens; one with more boot things on it and the other with some boot stuff and my login in tty1.

My description probably hasn't included enough information, but if you have _any_ idea of how to fix it, it would help.  I really hate using the Vista on this computer.

You just cannot take an install configured for one particular type of hardware and expect it to boot up on totally different hardware.

Many things are configured during the installation process and do not just automatically reconfigure themselves when booted in a different environment.

If you want a system that does reconfigure itself every time it is booted up, then that is a USB Startup Disk system.

---

### Post by MiniStephan on 2009-11-22
Yeah, that's what I thought.  Like I said, I treated it as a HDD, not a USB device.  Looks like I have a reason to wipe, now.  Thanks for the help!

---

