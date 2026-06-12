---
title: "Disk Checks and Power Failures - ext4/Lucid issues?"
date: 2010-07-25
forum: General Help
---

### Post by R3M3 on 2010-07-25
After upgrading to 10.04 Lucid Lynx, I've noticed a somewhat annoying behavior. Whenever there is a power failure, reboot inevitably produces a "Filesystem Errors Detected" message. A further annoyance is that the check then stalls, waiting for human intervention. And pressing the "yes, I'd like to fix my disks" key, results in a rather lengthy wait as the disks are checked.

I don't recall having similar sorts of issues with previous versions of Ubuntu - power failures may have prompted a check, but I don't recall there being a consistent failure notification. Is it just my perception, or is there something about Lucid which makes these sorts of "failures" more frequent? I thought that the journaling system of ext4 was supposed to make the filesystem *less* prone to errors. (Although I was running ext4 with Karmic, and don't recall having similar issues, though.)

It's not a hardware issue - the disks are relatively new, and both of the (different model number) disks are being flagged as having errors, though the main filesystem moreso than the others. They're both larger than I was running previously, so perhaps that's contributing to the long check times.

Anyone know if something changed w/r/t disk check behavior in Lucid? Is there anything I can change to make the "Filesystem Errors detected" less likely on power failures? Any way to avoid the "press F to fix" stall on disk check? Any way to make disk checks speedier on large disks?

Thanks.

---

### Post by prodigy_ on 2010-07-25
A good UPS will certainly help...
> **R3M3 said:**
> ...to make the "Filesystem Errors detected" less likely on power failures

---

### Post by ajgreeny on 2010-07-25
I have had one or two power failures which send my desktop into a useless lump until the power comes back, and of course, causes a bad hard shutdown, but it has never even bothered to do a fsck check after that.  It only seems to do the fsck at the interval set by myself with tune2fs, not the default 30(?) boots set by the system.

I assumed that was the standard way that lucid did things, and have certainly not noticed any differences from previous ubuntu versions.

---

### Post by R3M3 on 2010-07-29
Anyone have any tips/suggestions which don't involve buying new hardware?

For example:

Is there some setting which will auto-answer "yes" to the "Do you want to fix the errors?" prompt?

Is there some setting in a configuration file (e.g. /etc/fstab) which will make it less likely that the filesystem will have errors in the event of a power cut? (And what do I give up for turning it on?)

Is there something about ext4 itself which makes errors on power failure more likely? Is there another filesystem format which does better in this regard?

---

### Post by dino99 on 2010-07-29
into a console (need to boot with a cd or usb)

to let you know about issue(s):
- fsck -n /dev/sdxx , where xx is your real partition

to repair it:
 fsck -y /dev/sdxx

*** if you dont know the partition name, use partedmagic to boot on or gparted inside the live cd/usb ***

---

### Post by bumanie on 2010-07-29
From a live cd or usb, i would run this command - according to Herman's illustrated Dual Boot site ([http://members.iinet.net.au/~herman546/p10.html](http://members.iinet.net.au/~herman546/p10.html)) this will correct 99% of ext* filesystem errors. > sudo e2fsck -C0 -p -f -v /dev/sdxxSubstituting xx for your partition designation.

---

