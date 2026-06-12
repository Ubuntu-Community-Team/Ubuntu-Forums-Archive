---
title: "USB 3.0 speed incorrectly reported - or is it?"
date: 2012-05-08
forum: General Help
---

### Post by Fraoch on 2012-05-08
Just playing around with my new USB 3.0 flash drive and I noticed something odd.

Take a look at the screenshot - the speed in Disk Utility is reported as "705 Mb/s".  That's a very odd number.  USB 3.0 is rated to 5 Gb/s although of course no device is going to get there right now.

What's even more odd is that my drive benchmarked at almost *exactly* 705 Mb/s.  Take a look at the second attachment.  705 Mb/s = 88.125 MB/s...my drive is eerily close.

So what's going on here?  Where did that 705 Mb/s come from?  Does it somehow know how fast the drive will be? :-s It couldn't possibly be limiting it to that speed, could it?  On one hand it should report 5 Gb/s and on the other hand the odd "705 Mb/s" is much more realistic, yet it seems that number was chosen at random.

---

### Post by SB21487 on 2012-07-27
Just attached my Seagate Expansion 500GB USB 3.0 drive and I see the same 705 Mbps reported as the theoretical ( I believe the benchmark data is the actual). For my USB 2.0 devices it reports 480 Mbps which is the correct theoretical. Not sure whats going on, maybe its motherboard on my Dell Vostro v131.

---

### Post by dcstar on 2012-07-27
> **Fraoch said:**
> Just playing around with my new USB 3.0 flash drive and I noticed something odd.

Take a look at the screenshot - the speed in Disk Utility is reported as "705 Mb/s".  That's a very odd number.  USB 3.0 is rated to 5 Gb/s although of course no device is going to get there right now.

What's even more odd is that my drive benchmarked at almost *exactly* 705 Mb/s.  Take a look at the second attachment.  705 Mb/s = 88.125 MB/s...my drive is eerily close.

So what's going on here?  Where did that 705 Mb/s come from?  Does it somehow know how fast the drive will be? :-s It couldn't possibly be limiting it to that speed, could it?  On one hand it should report 5 Gb/s and on the other hand the odd "705 Mb/s" is much more realistic, yet it seems that number was chosen at random.

People should realise that a WIRE speed of the connection to a hard drive has little or no relevance to the data speed the drive is capable of.

The bottleneck is the hard drive, no matter if it is connected to a 5GB link or a 500GB link.

---

