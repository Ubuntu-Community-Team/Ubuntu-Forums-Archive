---
title: "Unrepairable Thunderbird installation"
date: 2010-04-28
forum: General Help
---

### Post by Lockheed on 2010-04-28
I've been using Thunderbird 3.0.x for some time and found in it a good replacement of TheBat. However, few days ago, ubuntu being ubuntu crashed and since then, Thunderbird freezes after 10 seconds every time I try to start it, sending CPU usage through the roof.

I have 8 imap accounts in it and my profile folder is ~2.8gb
I tried purging the installation.
I tried fsck on all partitions.
Windows Thunderbird using the same profile folder works just fine.

Any ideas welcome.

---

### Post by lidex on 2010-04-28
Where is your profile folder? Is it on a shared partition?

---

### Post by Lockheed on 2010-04-29
> **lidex said:**
> Where is your profile folder? Is it on a shared partition?
Shared ext2 partition.

---

### Post by lidex on 2010-04-29
Have you tried opening thunderbird with a new profile? That should work and I imagine the profile is the problem. Windows reads ext2? Something is probably corrupted. Try running fsck on that partition as well.

---

### Post by Lockheed on 2010-04-29
I already run fsck on all partitions.
There's no point on starting a new profile as all the data is in my old one. Besides, it works in Windows.
I had similar problem with FireFox before, but after purging it, rebooting and installing, it went away.

---

### Post by lidex on 2010-04-29
> **Lockheed said:**
> I already run fsck on all partitions.
There's no point on starting a new profile as all the data is in my old one. Besides, it works in Windows.
I had similar problem with FireFox before, but after purging it, rebooting and installing, it went away.

OK, missed the part where you mentioned fsck.
The whole point is to see if thunderbird will start with a clean profile. If it does, then it's the profile causing the problem and you can then rule out the thunderbird install and narrow down the issue. I understand all your data is in the old profile, but that doesn't help you if you can't use it. But, hey, you've got windows, right?

There is a recent bug with 3.0.4 that seems to apply to upgrades:
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/563893]("https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/563893")
Check in your profile for a lock. Check permissions for it as well.

You mentioned you had the same problem with firefox. Was that using a shared profile also?

---

### Post by Lockheed on 2010-04-30
I scrapped thunderbird and run pre-compiled 3.0.4 from thunderbird website. It works like a charm, so the fault must have been within the program itself, just like with the firefox.

---

