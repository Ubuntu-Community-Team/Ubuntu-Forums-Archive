---
title: "Disk Usage Inaccuracies"
date: 2011-02-15
forum: General Help
---

### Post by Gibby82 on 2011-02-15
First, let me say I would search if I knew what to search for. Unfortunately, I haven't the slightest of where to begin. 

The issue may or may not be related to MediaTomb. I installed it, added my dir for music (at the time it was /storage) and let it run. It stopped working with my PS3, I came to troubleshoot, was greeted with low disk space alerts, restarted, and now am here. I've changed fstab, moving my RAID from /storage to /media/storage. That didn't seem to do anything. 

The image shows what my current situation is. No clue where to go from here.

---

### Post by Gibby82 on 2011-02-15
Did a fsck on both drives at the advice of friend. Both seemed to run rather quickly and were clean. Going to try to force a check possibly, later tonight.

---

### Post by hawkmage on 2011-02-15
Can you unmount the volume /media/storage and see what is in the directory?  It should be empty.  I have see weird things happen if you mount a volume over a directory with something already in it.

---

### Post by tgm4883 on 2011-02-15
Possibly attach your info to this bug [https://bugs.launchpad.net/ubuntu/+bug/370487](https://bugs.launchpad.net/ubuntu/+bug/370487)

---

### Post by Gibby82 on 2011-02-17
> **hawkmage said:**
> Can you unmount the volume /media/storage and see what is in the directory?  It should be empty.  I have see weird things happen if you mount a volume over a directory with something already in it.

I just created the /media/storage directory, and the previous dir, /storage, was created specifically for this drive. So in both cases they didn't exist before I made them. So it's actually been unmounted and moved to another dir, and the result was the same.

---

### Post by Gibby82 on 2011-02-17
> **tgm4883 said:**
> Possibly attach your info to this bug [https://bugs.launchpad.net/ubuntu/+bug/370487](https://bugs.launchpad.net/ubuntu/+bug/370487)

Thanks, I went ahead and attached my info.

---

