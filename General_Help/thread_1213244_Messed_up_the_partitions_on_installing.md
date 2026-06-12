---
title: "Messed up the partitions on installing"
date: 2009-07-14
forum: General Help
---

### Post by fast_hands on 2009-07-14
Hi all,

I messed up my partitions on installing and now I don't have enough disk space. I've tried to create a new partition using Gparted, but I can't work out what I need to do. I've clicked on the free space then tried to create a new partition. It will only let me create a primary partition, which I then can't mount. I've posted a screen shot below of what my drives look like. I'm dual boting XP and Ubuntu.

Any advice anyone can give me on sorting this out would be greatly appreciated.

Also, as I'm a complete noob to this game, what's the difference between a primary, logical and extended partition?

[IMG]http://img354.imageshack.us/img354/9748/screenshotrma.png[/IMG]

---

### Post by michy99 on 2009-07-14
Here is one solution if you want to make sda6 bigger and use your free space.

1. Grow sda2 to use up the free space.

2. Move sda7 and sda5 to the end of sda2.

3. Grow sda6 to use up the space in sda2.

You have to do all this from a Live CD.

---

### Post by fast_hands on 2009-07-14
> **michy99 said:**
> Here is one solution if you want to make sda6 bigger and use your free space.

1. Grow sda2 to use up the free space.

2. Move sda7 and sda5 to the end of sda2.

3. Grow sda6 to use up the space in sda2.

You have to do all this from a Live CD.

Does this mean I have to reinstall essentially? Or will it just let me move stuff around at will?

Could anyone give me an explanation of what is actually going on on the drive? I'd like to get some understanding of what sda2 etc. actually means.

---

### Post by michy99 on 2009-07-14
You do not need to reinstall, but if you haven't done anything to the system yet, it might be quicker.

Sda2 in an extended partition. You can only have four primary partitions on a drive, but if you make one of them an extended partition, you can have as many logical partitions as you want. Sda5,6,and7 are logical partitions.

If you do the steps I outlined above, it will make sda2 bigger and allow you to move and expand logical partitions inside it.

---

