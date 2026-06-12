---
title: "No audio coming from laptop speakers, can only be heard with headphones"
date: 2009-10-18
forum: General Help
---

### Post by taybrown90 on 2009-10-18
Hello everyone, I'm a first time poster on these forums, and I hope to continue posting in the future. Anyway, to get to the issue at hand...

I've only tried installing 64-bit Ubuntu 9.04 and now, 64-bit Ubuntu 9.10 beta on my main laptop, which is a Gateway 6800FX, if it matters. Anyway, the two problems that I've always had when running Ubuntu on this machine are: 1) My dedicated 8800M graphics card's drivers are non-existant whenever I install Ubuntu for the first time, so the screen is a fuzzy mess. But this is fixed once I get the wireless setup and working, and is no longer a problem.

The issue I still have is that the drivers for my onboard sound card are not supported by alsa. I searched on various forums for fixes. They included uninstalling alsa-base then reinstalling, altering the alsa-base.conf with root permissions to add the option for an intel mobile soundcard, and messing with Arch to manually set the sound up for my system. I've tried everything but the latter to no avail, and I haven't tried messing with Arch yet because I'm not exactly sure how to go about it. If you guys wouldn't mind telling me how to get my soundcard's specs via terminal, I can post the exact model and what type of audio it uses if that will help. Any advice to fix this problem is welcome. Thanks in advance!

---

### Post by P4man on 2009-10-19
open a terminal and type

```
lspci
```

that will give the hardware specs. also provide output of 

```
aplay -l
```

that will list any soundcards ubuntu found

---

### Post by Giblet5 on 2009-10-19
> **taybrown90 said:**
> Hello everyone, I'm a first time poster on these forums, and I hope to continue posting in the future. Anyway, to get to the issue at hand...

I've only tried installing 64-bit Ubuntu 9.04 and now, 64-bit Ubuntu 9.10 beta on my main laptop, which is a Gateway 6800FX, if it matters. Anyway, the two problems that I've always had when running Ubuntu on this machine are: 1) My dedicated 8800M graphics card's drivers are non-existant whenever I install Ubuntu for the first time, so the screen is a fuzzy mess. But this is fixed once I get the wireless setup and working, and is no longer a problem.

The issue I still have is that the drivers for my onboard sound card are not supported by alsa. I searched on various forums for fixes. They included uninstalling alsa-base then reinstalling, altering the alsa-base.conf with root permissions to add the option for an intel mobile soundcard, and messing with Arch to manually set the sound up for my system. I've tried everything but the latter to no avail, and I haven't tried messing with Arch yet because I'm not exactly sure how to go about it. If you guys wouldn't mind telling me how to get my soundcard's specs via terminal, I can post the exact model and what type of audio it uses if that will help. Any advice to fix this problem is welcome. Thanks in advance!

You may have to wait a month or two for audio support.

Or, I can trade you an old Omnibook that works great. I'll even throw in some pizza coupons to make it fair. ;)

---

