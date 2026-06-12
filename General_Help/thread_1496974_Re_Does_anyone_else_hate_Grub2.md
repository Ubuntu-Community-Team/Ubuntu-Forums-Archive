---
title: "Re: Does anyone else hate Grub2?"
date: 2010-05-29
forum: General Help
---

### Post by optimus2861 on 2010-05-29
I'm not actually running Ubuntu but I am running the latest Linux Mint. Has anyone else run into this problem? 

I installed grub2 into the root partition of Mint, rather than the MBR. Every stinking time I reboot Mint, that partition turns unbootable! I have to pull out the live DVD, reinsert it, run a "sudo grub-install ...", then reboot. Then the partition is bootable again. Until the next reboot!

What the hell is going on here?!

---

### Post by cariboo on 2010-05-29
This is a support question, it doesn't belong in the Cafe. Moved

---

### Post by wojox on 2010-05-29
Why don't you install Grub2 to the Master Boot Record?

---

### Post by Spr0k3t on 2010-05-29
When you go to do the grub-install and you choose a partition instead of the MBR you are given a warning message about the stability of using a regular partition.  What you have described is one example they give for some northbridge chipsets.

Solution: sudo grub-install, select the MBR instead.

---

### Post by dcstar on 2010-05-30
I use **burg** now, a nicer, graphical version of Grub2 that actually works better.

---

### Post by optimus2861 on 2010-06-12
> **wojox said:**
> Why don't you install Grub2 to the Master Boot  Record?
Because I was using BootItNG as my boot loader. Note the word "was". I  was finally forced to throw in the towel and  install grub to the MBR in order to get my system to boot.

> **Spr0k3t said:**
> When you go to do the grub-install and you choose a partition instead of the MBR you are given a warning message about the stability of using a regular partition.
I read that warning message. It's pure technobabble. I had to google it to find out what it meant (fortunately I have a laptop). The programmer who wrote it needs to be whacked with a cluebat about writing better error messages.

The old grub never had a problem being installed into a partition instead of the MBR and being chain-loaded. I ran my system that way for years. I completely fail to understand why an "upgraded" grub no longer likes to do this without technobabble and silent failures.

---

