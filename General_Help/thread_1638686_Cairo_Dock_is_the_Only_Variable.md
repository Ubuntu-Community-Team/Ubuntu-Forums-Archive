---
title: "Cairo Dock is the Only Variable"
date: 2010-12-05
forum: General Help
---

### Post by MrJLBrown on 2010-12-05
I just don't get it. I used to have terrible problems of "input/output error failed to initiate child process," random reboots, locks, booting in initramfs, and inevitably a complete format and reinstallation of Ubuntu 10.04.

I've been running the same installation of Ubuntu 10.04 for almost two months, now, and I'm constantly on edge expecting crashes. But I've actually had the best Ubuntu experience I've had since I discovered it in July. There is really only one variable I can point at--I have not installed Cairo Dock at all.

I'm really just curious if maybe I've just had flubbed installations that mysteriously didn't work for some reason or another, or maybe because this time I partitioned my drive for storage, or if because I'm dockless this time. Heck, I never even used the OpenGL version so it should have been more stable.

My question is if anybody has ever had complete system-wide crashes and instability caused by Cairo Dock. It just seems really far-fetched to me a dock program of all things could force you to reinstall an entire system.

---

### Post by asmoore82 on 2010-12-05
Your hard drive almost certainly has failing sectors or "bad blocks".

The drive will attempt to conceal these errors and reallocate storage
to some spare sectors on the drive. A clean re-install is the perfect
clean slate that such a drive needs to work great again ~ for a little while.

If a drive like that is under warranty you would be entitled to a complete replacement.

To test, you need to boot a LiveCD and
```
sudo badblocks -sv /dev/sda
```
^you may need to adjust sda but make sure not to include a number at the
end, you need to test the entire drive and not just a partition.

Google has done extensive studies on drive failure data across all their operations;
they found absolutely no correlation between failures and brand/temperature/usage
with the exception of one product that needed to be recalled.

There is, however, a "survival of the fittest" effect where good older drives are
statistically less likely to fail because they have survived the "infant mortality" rate.

---

