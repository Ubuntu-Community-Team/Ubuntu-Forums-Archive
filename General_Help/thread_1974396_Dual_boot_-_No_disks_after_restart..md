---
title: "Dual boot - No disks after restart."
date: 2012-05-06
forum: General Help
---

### Post by wselwood on 2012-05-06
I've been running kubuntu for a couple of weeks, setup to duel boot with windows 7. Every thing has been fine while I've been using kubuntu. However every time I boot into windows when I next restart my computer there is no grub menu. The bios sits there like it has no boot-able disks. 

Booting off the kubuntu install disk and using boot repair seems to resolve the problem until I next have to boot into windows again. (Though the kubuntu boot splash screen was garbled after the first time round this loop) The next time I boot into windows it happens again.

Here is the paste bin of the last boot-repair run: [http://paste.ubuntu.com/970758/](http://paste.ubuntu.com/970758/)
And the first time it happened: [http://paste.ubuntu.com/955304/](http://paste.ubuntu.com/955304/)
Unfortunately I didn't write down the URL for the second time I had to do this.

I've had a search around the forum and googled the only similar problem seemed to be when windows update runs and causes the boot flag to be set. However the last two times I am pretty sure that windows update wasn't showing any updates. Can't remember on the first time, I wasn't paying close attention as I wasn't expecting any problems.

Unfortunately due to my work not using windows is not an option.

My disk set up:
sda : windows 7
sdb : windows 7 (software raided with sdd in windows 
sdc : kubuntu and all its partitions (/, /boot, /home, swap)
sdd : windows 7 (other half of the software raid)

Any one got any idea's for things I can change in system to get rid of this problem?

---

### Post by wselwood on 2012-05-07
I think I've managed to resolve my problem.

Using boot repair from the live cd I changed the options to force grub to install to only sdc1 (The linux disk). Then in the bios I changed the boot order of the disks so sdc is now first, rather than the disk with windows on it.

So far it seems to be keeping windows' hands of my boot loader.

---

