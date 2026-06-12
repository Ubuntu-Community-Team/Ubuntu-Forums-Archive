---
title: "need to get write permission on this drive"
date: 2010-01-01
forum: General Help
---

### Post by itachis.eyes on 2010-01-01
first off let me start by saying i'm trying out linux from scratch and maybe i'm going about this the wrong way...

ok if you look at the attachment that is the map of my hard drive, the /dev/sda1 partition is what i'm trying to build my install on but i can't figure out how to get write permission on it. right now its read only.

also..i wasn't quite sure (i know this is probably the wrong place to ask) but the partition i'll be building on, is it fine like that or does it need to be inside my extended partition, and if so i honestly have never done that before so i don't know how to do it.

thanks

---

### Post by northrup on 2010-01-01
Maybe this would work? (I don't know what GParted's terminal command really is...)

```
sudo gparted
```

Sometimes Ubuntu automatically puts original partitions and hard drives under root's ownership, I assume to prevent accidental data corruption.

Also, make sure the partition isn't mounted for some reason.

---

### Post by northrup on 2010-01-01
Oh, and that should be fine the way you have it in regards to extended partitions.  I personally don't see why you'd need an extended partition in the first place, since there's only four total, unless you're planning on splitting the one you're trying to get write access for.

---

