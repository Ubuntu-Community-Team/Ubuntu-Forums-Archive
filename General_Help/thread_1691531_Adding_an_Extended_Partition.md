---
title: "Adding an Extended Partition?"
date: 2011-02-20
forum: General Help
---

### Post by emoguitarist06 on 2011-02-20
Here is my hard drive setup
sda1 = Swap
sda2 = ext4 / 
sda3 = ext4 /home
sda4 = ntfs Windows 7 

They're all primary partitions. I want to triple boot with another linux distro (KXStudio to be exact) but obviously I can't add another primary parition so I need an extended partition.

Is there anyway I can create an extended partition and place my current primary's under it?

p.s.
The only solution I can think of us using clonezilla to make an image of my partitions and than format my drive and then create the extended and use clonezilla to put back my previous partitions. (Now that's just a hunch... I'm not even sure if that'll work)

---

### Post by plucky on 2011-02-20
The easiest thing to do is delete the swap partition,resize one of the primary partitions so that there is some un-allocated space, then create the extended partition on the un-allocated space.
Once the extended partition is there,you can re-create the swap partition in it.

I am surprised the swap partition wasn't put into an extended partition during the installation.(Unless you set it up this way)

Can you post a Gparted screenshot?

---

### Post by emoguitarist06 on 2011-02-22
> **plucky said:**
> The easiest thing to do is delete the swap partition,resize one of the primary partitions so that there is some un-allocated space, then create the extended partition on the un-allocated space.
Once the extended partition is there,you can re-create the swap partition in it.

I am surprised the swap partition wasn't put into an extended partition during the installation.(Unless you set it up this way)

Can you post a Gparted screenshot?

Man sometimes the obvious just escapes you huh? Thanks and this is exactly what I'm doing! I deleted the swap and moved sda2 and sda3 and Installed an extended and logical ext4 and logical swap

Yeah when I installed Ubuntu I did manually partitions to have the separate /home but I just totally forgot about using an extended partition

anyways THANKS!

---

