---
title: "Partitioning a drive without formatting?"
date: 2009-10-11
forum: General Help
---

### Post by CycloneJoker on 2009-10-11
I'm running Ubuntu Netbook Remix on my Acer Aspire One, and I'd like to be able to play around with some other distros without touching the main SSD in my Netbook, since it's only an 8 GB.  I happen to have a 250 GB external USB hard drive with a fair bit of open space still left on it (right now, about 120 GB) since I'm not a real heavy user.  What I'd like to do is partition the drive so that I can leave the media on there alone (about 23 GB of music, and the rest being video files), and then have maybe one or two partitions on it separately to install some Linux distros to, so that if I feel like trying out some others I can just plug it in and boot from the external.

Is it possible to do this, and what do I have to do in order to do this?  And on a somewhat related note, when the external is plugged in, will the GRUB loader be able to see the installed Linuxes or do I absolutely have to go in every time and point the BIOS to the drives?

---

### Post by ubun_two on 2009-10-11
Since you are trying to re-partition the external drive and not the internal one, you can use GParted from your Ubuntu installation.  If you don't already have it installed, you can install it using Synaptic.  Don't forget to unmount before changing the partition.

You can then install any Linux distribution in that opened partition on your external drive.

The USB device must be ahead of your internal drive in your netbook to boot from any distribution that's installed there.

---

