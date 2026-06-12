---
title: "Ubuntu sometimes doesn't boot"
date: 2011-12-14
forum: General Help
---

### Post by thacursedpie on 2011-12-14
Hey!

I am running Ubuntu 11.04 on my laptop, dual booted with Windows 7. About half a year ago I had re-installed Ubuntu after my laptop had been repaired (broken screen and they wiped the hdd, no surprise there though). It worked excellent.

A couple of months ago Ubuntu came up with a dialogbox prompting me to install some updates. Okay, no problemo. Being me I didn't really look into what these updates were, but I trusted Ubuntu to be nice :P.

After that update, I have been having some odd problems. Out of about every 3 times I try to boot into Ubuntu, only 1 is successfull. Sometimes the screen just stays black, and after a short moment Ubuntu boots up. Sometimes the Ubuntu logo appears and it boots up, sometimes the screen stays black and Ubuntu doesn't boot up.

I've got no clue what is causing this, nor have I found any correlations between then non-startups (similar circumstances, etc).

I've tried running the diagnostic mode (or whatever it's called) from Grub, it scanned the hdd and fixed some things. But after that I'm still having the issue that it just won't boot up most of the time.

Any ideas? Thanks in advance!

EDIT:
Opening Gparted it appears my Swap partition has become corrupt. ("Unable to detect filesystem!")
Can I just format this partition to "linux-swap"?

---

### Post by Mark Phelps on 2011-12-14
> **thacursedpie said:**
> Can I just format this partition to "linux-swap"?

Yes ... but when using GParted, you will probably have to select the partition and choose Swapoff before it will let you reformat it.

---

### Post by flyingfisch on 2011-12-14
I had a similar problem. You may want to check fstabs also to make sure it still recognizes it as swap.

---

### Post by thacursedpie on 2011-12-14
@Mark Phelps:
It's complaining that it's being used, so I'm going to give it a try with my live-cd (on usb). Will report back.

@flyingfisch:
How do I do that?

EDIT:
I just reformatted that partition to linux-swap. I restarted Ubuntu from my HDD, but it still isn't recognizing the partition, even though Gparted said the formatting was successful...

---

