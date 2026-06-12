---
title: "Nvidia drivers cause log out of session with web based video"
date: 2012-02-21
forum: General Help
---

### Post by Fenris_rising on 2012-02-21
Hi all

I've been using Ubuntu since 8.04 burst on the scene. Things have been great with a rock solid OS which has been brilliant to use.

Sadly about 3 - 4 months ago I began to suffer from random log out of sessions. I have been following all sorts of possible cures via the forum to no good effect.

In desperation, as the issue was becoming more regular in occurrence, I have done full re installs and have just changed to mint 12 from my faithful following of the Ubuntu Canonical lineage.

What has occurred now, with ubuntu 10.04, 11.04, mint 9, mint 12 is the ability to guarantee a log out of session when I have the nvidia drivers active. Specifically when watching iplayer, youtube or any web based video media.

If I don't use the restricted drivers I can watch web video no problem at all.

I've just been running mint 12 with the nouveau drivers for 24hrs and have had no issues at all with log out behaviour when viewing video. 30 minutes ago I bit the bullet and installed the recommended nvidia drivers and as soon as I tried to watch a web video the PC logged out!!!

As far as I am able to tell the hardware is all good. I my GPU is an 8400GS Nvidia card and I have dual monitors. I had also been running with Compiz doing it's thing flawlessly up to this point. This configuration has run superbly up until the 3 - 4 months ago and I am at a loss. I have even tried using older kernels and tried all the nvidia drivers both via the hardware drivers and manually installed and even though they used to be fine I am having the same issue across the boards. This even with effects turned off and no compiz.

I am going to try starting with 8.04 again and see if I get any joy I am that desperate!

So without Nvidia drivers all is well. With Nvidia it's guaranteed to fall over. Has anyone got a clue what else it could be because I think I'm running out of options. Only watching video causes the log out and I have even tried different browsers and environments, having read some possible cures on here, to no avail.

The only positive thing I have got from this PITA is trying KDE destop. It's rather nice!

Using Nouveau for 24Hrs was pretty good and I can't fault it as such but I do miss the 'little extras' that Nvidia drivers give to the effects.

Any help, hints, suggestions please!

BTW there are no error logs ever so no clues there.

regards

Fenris

---

### Post by lovinglinux on 2012-02-21
I don't know a solution, but I would recommend reporting this issue to the developers.

I didn't experience logouts, but I have been very disappointed with nVidia drivers performance on Oneiric, specially when flash video is involved. No matter what I do, performance is subpar, when compared to Lucid.

I am kind of glad that my new notebook doesn't have a nVidia card.

---

### Post by Perfect Storm on 2012-02-21
Could it be the card is starting to mal-function?

---

### Post by Fenris_rising on 2012-02-22
Hi there

I'm not sure I can report his as a bug. At this time I have no conclusive proof of the cause.

Today I ran one screen only and was able to watch a web video fully with no issues with the Nvidia driver in place.

Malfunction? Well is it a possibility? My thought is that using the Nvidia drivers with dual screens may stress the GPU due to the 'fuller' use of it.

Does the nouveau driver stress the GPU less thereby running under the critical point of failure?

I have run with the nouveau drivers all day, after the single screen Nvidia test, and frankly it is working rather well with both screens running.

I will continue with the nouveau drivers for now until I can afford a newer GPU to try again.

regards

Fenris

---

### Post by lovinglinux on 2012-02-22
> **Fenris_rising said:**
> Hi there

I'm not sure I can report his as a bug. At this time I have no conclusive proof of the cause.

Today I ran one screen only and was able to watch a web video fully with no issues with the Nvidia driver in place.

Malfunction? Well is it a possibility? My thought is that using the Nvidia drivers with dual screens may stress the GPU due to the 'fuller' use of it.

Does the nouveau driver stress the GPU less thereby running under the critical point of failure?

I have run with the nouveau drivers all day, after the single screen Nvidia test, and frankly it is working rather well with both screens running.

I will continue with the nouveau drivers for now until I can afford a newer GPU to try again.

regards

Fenris


Indeed it could be the dual screen setup.

Nouveau works better than nVidia for me, but with the expense of GPU temperature. It used to run a lot hotter than nVidia. I don't know if the developers improved that since the last time I tested.

---

### Post by efflandt on 2012-02-22
I don't know if this will help or not, but for 11.10 I have to use **nomodeset** kernel boot parameter, and for 10.10 I do not.  nvidia-current version from x-swat for both was identical, they are both 64-bit, the only difference is kernel version.

I did have problems with a failing GT 430 card, but I believe that was a physical problem with the card itself, because its symptom of screen freeze with mouse cursor still able to move in most cases, but no mouse click or keyboard response, happened in 64-bit Win7 as well.  Although, it rarely happened in 10.10.

No problems at all with my new video card once I realized that I had to use nomodeset for 11.10 (without that my screen would lose video signal after grub menu).

---

### Post by Fenris_rising on 2012-02-23
Hi chaps

Well I have settled for using mint12 at the moment. Dual screen under nouveau and the ability to watch video without issue I am pleased to report.

Though I did have a little problem with mint in that every now and again I would suddenly find myself with no control. I could highlight panel buttons but the menu was inaccessible and my open apps sort of locked up.

I could only get out using Ctrl/Alt/BkSpc. This seemed to be a glitch with the desktop rather than hardware. Installing KDE desktop has cured this and I have this set up with 4 virtual desktops and the rotating cube. All seems well at the moment and I will start looking for a new GPU card ready for 'total failure'.

I have the OS on a 120Gb drive at the moment and have a 500Gb installed which I will use to 'test' OS function when I have a new card. I can then just shift things over as and when.

regards

Fenris

---

