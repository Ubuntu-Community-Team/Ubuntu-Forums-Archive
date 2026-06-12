---
title: "USB stick with CD partition in 11.04: how to stop repeated notifications"
date: 2011-05-07
forum: General Help
---

### Post by keithpeter on 2011-05-07
Hello All

I have one of those USB sticks that has a partition that mounts as if it was a read only CD and another that is a 1Gb storage area.

When I pop this into a USB socket under Xubuntu, I get repeated notifications that the CD has mounted (and, with default settings, a lot of Thunar windows!).

Real optical CDs mount normally with a single notification.

Ordinary USB sticks mount normally with a single notification.

This happens on two different computers with Xubuntu installed

When booting the laptop from a live Ubuntu 11.04 CD, the storage device opens normally with a single window for the CD partition and another for the storage partition.

How do I find out what is going on? Any command line magic?

Have I actually found a bug, be it ever so obscure?

The nearest thing I can find to this is at

[http://ubuntuforums.org/showthread.php?p=10777593#post10777593](http://ubuntuforums.org/showthread.php?p=10777593#post10777593)

---

### Post by Not unique on 2011-05-07
Have you already tried the basic stuff? like changing the settings in file manager for auto read on inserted media and settings for the notifications?

---

### Post by keithpeter on 2011-05-07
> **Not unique said:**
> Have you already tried the basic stuff? like changing the settings in file manager for auto read on inserted media and settings for the notifications?

Yes, and thanks for the reply.

I changed the file manager settings so that the contents of removable storage devices are not displayed automatically, so Thunar does not open 300 windows in a minute! I also changed the notification settings so that the notifications only stay on the screen for a second.

What I'm interested in is why this particular drive is confusing Xubuntu's device loading system, and other drives are not. I was thinking its to do with the speed with which the solid state 'CD' responds in some way, a 'race' condition. Anyone got any ideas?

Cheers

---

### Post by Not unique on 2011-05-07
I have a USB T-mobile internet sick and Ubuntu has always recognised that as a CD too so it must be a little bug maybe therefore too complicated for me SORRY you will have to bump it and wait, Mind you this reply will bump it up the list.

Maybe it's something to do with the way Ubuntu recognises chips/firmware chips in dongles (USB sticks) because of chips structure but just a guess.

---

### Post by keithpeter on 2011-05-08
Thanks for replying, 

I've logged a bug at

[https://bugs.launchpad.net/ubuntu/+bug/779438](https://bugs.launchpad.net/ubuntu/+bug/779438)

with all the information that I can find. This is definitely 'unexpected behaviour'.

Cheers

---

### Post by eev2 on 2011-09-27
Hi **keithpeter**. I was wondering whether you found a solution to this as I am also experiencing the same problem. Please let me know. Thanks.

---

### Post by keithpeter on 2011-09-27
Hello Eev

Suggest you add your report to the bug thread on Launchpad. They seem to have logged it as an actual bug. I just use that stick for music on my mp3 amplifier now!

cheers

---

