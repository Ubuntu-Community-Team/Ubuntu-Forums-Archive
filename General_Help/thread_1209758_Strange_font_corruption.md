---
title: "Strange font corruption"
date: 2009-07-10
forum: General Help
---

### Post by thezood on 2009-07-10
Weird thing is happening all of a sudden. Text are being displayed really corrupted and messed up (see attachments). First I thought it was only an encoding problem in Firefox but now it has showed up in the terminal as well. Have anyone seen anything like this? 

It could have something to do with me using a Linux kernel from edgers, 2.6.30-020630rc2-generic, and UXA graphics since this improves performance on my Asus EEE 904 netbook. However, I've been using that kernel for quite some time without problems.

---

### Post by Blancmange on 2009-08-06
I'm getting it on what lspci calls a "ATI Technologies Inc Radeon RV250 If [Radeon 9000] [1002:4966] (rev 01)". It makes no difference what font rendering options I use.

So are lots of people, it seems:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/293059](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/293059)

As you can see from the attached image, the bottom few pixel rows of some of the characters are corrupted.

---

### Post by Blancmange on 2009-08-07
It seems that when I followed a hunch and went into each user account I had and tried out all options presented in the Visual Effects tab of the Appearance preferences (and choose "None" for all of them, because I detested most of the effects), the problem went away.

The hunch was that the display preferences needed to be massaged because the effective preference data was not being consistently segregated between user accounts.

---

### Post by Blancmange on 2009-08-07
Please excuse the spurious Thumbs Down smiley. Ubuntu 9.04's handling of my Wacom Artz II tablet is diabolical. It's like my computer's overdosed on blue honey or something.

---

