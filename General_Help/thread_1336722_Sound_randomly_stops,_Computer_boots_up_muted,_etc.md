---
title: "Sound randomly stops, Computer boots up muted, etc (64-bit with RT Kernel)"
date: 2009-11-24
forum: General Help
---

### Post by Mike_IronFist on 2009-11-24
I'm a musician so I use Ubuntu Studio 64-bit. Why am I telling you this? Because as a pre-requisite to this problem, you need to know that:
-I NEED to use a realtime kernel
-Music and sound are among the most important things I can get out of my laptop
-I don't want to be suggested anything that might otherwise compromise my audio experience in Ubuntu.

So here's the problem: When I boot up my machine, the sound it set to 0%, or mute. Naturally, I turn up the volume. Problem solved? not even close.

When I watch long flash videos or have skype calls with my friend, the sound just suddenly cuts out for whatever particular app I'm using and doesn't come back until I restart that app.

So can anyone help me? This problem is EXTREMELY annoying!

---

### Post by Mike_IronFist on 2009-11-24
bump

---

### Post by Mike_IronFist on 2009-11-24
bump again.

---

### Post by Mike_IronFist on 2009-11-25
Bump. Again. Help.

---

### Post by Person98 on 2010-01-16
yeah i am having the same issue on the 32 bit version, just thought i would let you know you aren't alone. I have been looking and a fair number of post to similar situations but i have found no solution as of yet. just out curiousity did it start after the upgrade to karmic, and did you do a fresh install or an upgrade from a previous version.

Thanks, best of luck

---

### Post by danielkabrinski on 2010-01-16
I have 64 bit Xubuntu, and honestly, to fix the problem I removed everything ALSA and put on OSS (Open Sound System).  I went through the same crap you did.  No sound on boot, run a game and my sound shuts off, run audacity and I have to reinstall ALSA...  got sick of it.  It seemed that none of my sound cards were supported by ALSA, or, ALSA just isn't as great as it is cracked up to be, OR, I just didn't understand how to set it up right (this is probably why ;D).

I followed the instructions here: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

It takes some work/troubleshooting but when you finish you will not regret it.

---

