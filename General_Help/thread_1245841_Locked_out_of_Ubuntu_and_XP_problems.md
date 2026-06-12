---
title: "Locked out of Ubuntu and XP problems"
date: 2009-08-21
forum: General Help
---

### Post by SirSigma on 2009-08-21
Earlier today I had a setup of the Windows 7 RC and Ubuntu 9.04. Everything was working, but knowing the RC would end up expiring sometime around June next year (with the annoying messages prompting me to purchase it coming around as early as March), I decided to remove Windows 7 and install XP.

My friend gave me a disk with XP Professional with SP3. He told me it would work. So I went into Ubuntu 9.04 and, after backing up all my media on an external hard drive, deleted the Windows 7 partition. It was then unallocated space.

So I tried running the XP disk from boot. But no matter what happens, the setup will stop dead at "Human Interface Parser" and it will just sit there pretending to continue loading. I waited as long as 20 minutes looking at the message, but to no avail. I tried booting the disk again, but the same thing happened.

I was a bit concerned and wanted to learn more about this problem, so I tried to boot into Ubuntu 9.04, but that's when things took a turn for the worse. It seems my GRUB installation was on that partition, since I got a screen telling me the media test failed and to check a cable (which I can't do on my laptop).

Since then, I booted into my live CD of Ubuntu 8.10 (I lent 9.04 to somebody else) and tried to find a way to recover GRUB, but for each scenario, it only pertains to deleting Linux, not deleting Windows.

I have factory disks with Vista on them, but I do NOT want to go back to Vista.

So what I'm trying to say here is that I have 2 problems I need to get help on.

1) How do I get the XP installation past "Human Interface Parser"? Is it supposed to take forever to start that?
2) How can I restore GRUB on a scenario where I deleted Windows instead of Linux?

Please respond as soon as possible. I'm here on my Live CD and I really miss my 9.04 installation. It feels like I locked myself out of my car.

---

### Post by vinnywright on 2009-08-21
make a partition on the unallocated space and do XP agin........then use this guide [http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

I think #3 is what you want to reinstall grub.

VINNY

---

### Post by bchurchill on 2009-08-21
Yeah, Windows likes to rewrite your Master Boot Record every time you install it, so you need to replace it afterward.

Here are instructions on that:
[https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows](https://help.ubuntu.com/community/WindowsDualBoot#Recovering%20GRUB%20after%20reinstalling%20Windows)

As to the Windows XP problem, I don't know how to help you.

---

### Post by SirSigma on 2009-08-22
Thanks guys. I was able to recover my Ubuntu installation and I was able to install XP with my friend's help. As it turns out, installing it from CD worked better than installing from DVD (I haven't a clue why).

---

