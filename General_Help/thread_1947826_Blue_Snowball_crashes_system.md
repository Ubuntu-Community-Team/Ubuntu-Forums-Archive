---
title: "Blue Snowball crashes system"
date: 2012-03-27
forum: General Help
---

### Post by antar on 2012-03-27
My system
[LIST]
[*]Ubuntu 10.04, 64-bit
[*]AMD Phenom II processor
[*]Nvidia GT 430 card, running proprietary drivers
[/LIST]

I installed some updates this morning, including the new linux kernel to (2.6.32-40), and rebooted. When I did, my computer locked up, refusing to boot, with the message:

```
BUG: soft lockup - CPU#5 stuck for 60s!
```

I'd seen that before (but not recently), and knew it had to do with my Blue Snowball USB mic, which was indeed connected, so I un-plugged it and rebooted successfully.

Problem is, whenever I plug it in, my system locks up (top shows modprobe at 100%).

I tried rolling back the kernel, but now it does this all the time. Is this a known issue? More importantly, is there a fix? I can live without my USB mic, but it's made my life so much better having it.

Edit: found [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/618155"). Am removing the various alsa backports now (I feel like I needed them for something...).

---

### Post by antar on 2012-03-27
Yeah, removing all alsa backport modules, as described [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/618155/comments/3"), fixed the issue.

---

