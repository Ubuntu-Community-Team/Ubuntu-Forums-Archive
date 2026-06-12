---
title: "Fake raid STILL can't partition in 10.04 installer"
date: 2010-07-16
forum: General Help
---

### Post by coryj on 2010-07-16
Been attempting to install ubuntu on my Intel fake raid on a new PC.
The installer sees the raid, but errors out:

> The ext4 file system creation in partition #1 of Serial ATA RAID isw_ehbgbddej_Volume0 (mirror) failed.This seem to be the EXACT issue described in this bug report:
[https://bugs.launchpad.net/ubuntu/+source/parted/+bug/568050](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/568050)

I read all the way down this bug report, and at the bottom it says:
> Launchpad Janitor  on 2010-06-25
Changed in parted (Ubuntu Lucid):
status:     Fix Committed &#8594; Fix Released A few weeks ago, a fix was "committed" and "released". I had been working with an earlier 10.04 ISO, so I downloaded 10.04 from the web site today. Still the same problem.
Maybe I'm just reading the bug report wrong? If it says the fix is committed and released, I would naively assume that it is fixed. Do I need to patch to apply the fix or something? Doesn't seem likely.

---

### Post by cj.surrusco on 2010-07-16
I would check out Linux Software RAID. I use it and it seems to have less problems than fakeraid. Plus, you don't have to worry about the RAID controller failing. Check it out [here]("https://help.ubuntu.com/community/Installation/SoftwareRAID").

---

### Post by ronparent on 2010-07-18
My experience matches yours relative to the bug report - any attempt to partition during the install fails. I had independently stumbled on one of the described workarounds and managed to install to a partition created with gparted in an earlier release (9.04 in my case). Also, with 10.04, I had to use an earlier install on a non-raid disk to boot to the raid install and install-grub to the raid to properly align grub to the raid install (step 8>advanced had failled). In Mint 9 step 8 did successfully install the grub boot loader to the raid. So you see, it is still a mixed bag but you can install to and boot from a raid with a bit of persistence.

Or, if your not dual booting with windows, you can follow cj's suggestion.

Good luck.

---

### Post by dino99 on 2010-07-18
before formatting, you need to remove it:

sudo dmraid -r -E /dev/sdx

---

