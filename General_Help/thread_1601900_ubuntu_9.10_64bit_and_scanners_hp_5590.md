---
title: "ubuntu 9.10 64bit and scanners hp 5590"
date: 2010-10-20
forum: General Help
---

### Post by AgentZ86 on 2010-10-20
well I duplicated this post sort of

But wanted to put 5590 in the title so see post here please

[http://ubuntuforums.org/showthread.php?p=10003028#post10003028](http://ubuntuforums.org/showthread.php?p=10003028#post10003028)

---

### Post by AgentZ86 on 2010-11-19
Ahhh !!! this is bugging me.

Anyhow, I installed fresh 10.10 thinking something must have broke
After reading all over the net and forums it appears there is a bug.
I have no idea how to fix it, but I've tried just about everything there is to try all over the net and the forums etc. 

After fresh install no effect same symptoms.
Here is where I'm at now.

For no real reason I installed:
kibksane0
libksane-dev

Now the scanner and xsane will scan lineart and save to pdf and appears to work well in line art mode.
But if I scan gray or color - then it resorts back to it's same ole (error I/O ) message
And various freezes, and after restarting xsane NO device found.
So I can unplug the device and power up again and xsane will find it again

But all I can do is scan lineart.

I have no idea why libksane0 or libksane.dev appear to have allowed me to at least get to the point where I can scan line art, but anyhow FYI

I ran xsane from the terminal and when attempting to do multipage it give this:
[hp5590] hp5590_bulk_read: USB-in-USB: incomplete bulk read (requested 65536 bytes, got 20480 bytes)
[hp5590] hp5590_get_ack: USB-in-USB: error getting acknowledge

Basically anything but the default lineart settings will produce this same error I/O
and this error in the terminal:

[hp5590] hp5590_bulk_read: USB-in-USB: incomplete bulk read (requested 65536 bytes, got 59392 bytes)
[hp5590] hp5590_get_ack: USB-in-USB: error getting acknowledge





Thats all I can do so far.

And this problem appears to be all my scanners I've tried not just the HP 5590
And a fresh install of 10.10 won't fix it either same effect.

Anyone got a fix I would love to scan

---

