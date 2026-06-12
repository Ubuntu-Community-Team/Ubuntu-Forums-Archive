---
title: "Hard Drive Behavioral Question -- Simultaneousness writing to multiple directories"
date: 2011-01-16
forum: General Help
---

### Post by cdaringe on 2011-01-16
Hi all:

This is fundamental question which I'd guess is handled differently between OS's and partition types?

Suppose on partition A I have directories A, B, C, ...N.

I would assume that as pencil is to paper, my disk can only write to **one** location at a time.  When using Ubuntu, when I command 'writes' to many directories simultaneously, how is that processed?  I'm particularly curious with higher volume writes.

For example, I was copying some old ISOs from one drive to my theoretic partition "A", downloading a big file @ 3mbs+, and moving my music library (~10gb) to this partition all @ the same time.

How does it query the transfers?  How does that impact disk health?

Thanks!

---

### Post by tredegar on 2011-01-16
> This is fundamental question which I'd guess is handled differently between OS's and partition types?
It'll be different between different OSs and filesystem types.

Your disk can probably only write to one location at a time, but if it has several heads and platters (as most do) some locations are better accessed at different times, and depending on the hardware, multiple writes _could_ take place across multiple platters at the same time, provided the HDD has sufficient buffer space, and this has been filled in advance. This can all become extremely complicated, but the kernel buffers file writes (in RAM, if you have enough) and tries to minimise head-movement (for speed). There is potential for conflict here, as the disk firmware might have one idea about what is "best" and the kernel another.

Also, disks may report themselves as having an entirely different hardware architecture from what they really have, and then use their own (proprietary) optimisation algorithms to minimise head movement and maximise transfer rates.

Meanwhile, the kernel will try to optimise disk reads and writes for minimal head movement (because head movement is relatively s-l-o-w). This is good for the disk hardware too, as it minimises wear in the head transport bearings.

There are people who find optimising disk transfers interesting (I did once: *many* years ago I wrote a program that formatted FDs so data transfer was 2X what the commercial sector was offering. 
It was "just" a matter of staggering the sectors, so that by the time the head move had completed, settled and synced with the track, the next sector was *just about* to pass under the head, rather than having to wait for another (almost) complete revolution.

Nowadays, you can relax and leave it to the kernel and the HDDs manufacturer to make the right decisions for you. If one disk seems slow, try another by a different manufacturer, perhaps the different optimisation algorithms will work together.

Of you *really* want to know how this all works, you should take a take a look at the kernel source code. It is well commented.

The HDD manufacturers are unlikely to reveal their optimisation strategies, which really doesn't help anybody who isn't running you-know-what, but that's life.

The bottom line is "Don't _you_ worry about it, that is what the kernel is _for_".

---

### Post by tredegar on 2011-01-16
> This is fundamental question which I'd guess is handled differently between OS's and partition types?
It'll be different between different OSs and filesystem types.

Your disk can probably only write to one location at a time, but if it has several heads and platters (as most do) some locations are better accessed at different times, and depending on the hardware, multiple writes _could_ take place across multiple platters at the same time, provided the HDD has sufficient buffer space, and this has been filled in advance. This can all become extremely complicated, but the kernel buffers file writes (in RAM, if you have enough) and tries to minimise head-movement (for speed). There is potential for conflict here, as the disk firmware might have one idea about what is "best" and the kernel another.

Also, disks may report themselves as having an entirely different hardware architecture from what they really have, and then use their own (proprietary) optimisation algorithms to minimise head movement and maximise transfer rates.

Meanwhile, the kernel will try to optimise disk reads and writes for minimal head movement (because head movement is relatively s-l-o-w). This is good for the disk hardware too, as it minimises wear in the head transport bearings.

There are people who find optimising disk transfers interesting (I did once: *many* years ago I wrote a program that formatted FDs so data transfer was 2X what the commercial sector was offering. 
It was "just" a matter of staggering the sectors, so that by the time the head move had completed, settled and synced with the track, the next sector was *just about* to pass under the head, rather than having to wait for another (almost) complete revolution.

Nowadays, you can relax and leave it to the kernel and the HDDs manufacturer to make the right decisions for you. If one disk seems slow, try another by a different manufacturer, perhaps the different optimisation algorithms will work together.

Of you *really* want to know how this all works, you should take a take a look at the kernel source code. It is well commented.

The HDD manufacturers are unlikely to reveal their optimisation strategies, which really doesn't help anybody who isn't running you-know-what, but that's life.

The bottom line is "Don't _you_ worry about it, that is what the kernel is _for_".

---

### Post by cdaringe on 2011-01-18
that was fantastic!  thank you so much!

---

