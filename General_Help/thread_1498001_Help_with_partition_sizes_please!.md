---
title: "Help with partition sizes please!"
date: 2010-05-31
forum: General Help
---

### Post by MikeSz on 2010-05-31
Hi All,

Ive just ditched Sabayon Linux and replaced it with 10.04, which I have to say is very nice indeed.  My system was initially a dual boot between Sabayon 3.5 and Windows XP on a split 160Gb hard disc.  Now, ive added an extra 160GB hard disc, which looked pretty much empty, and ive replaced sabayon with ubuntu.  When I went through the installation process however, what's ended up happening is the sabayon partition is now just free space (no idea how i did that) and Ubuntu has plonked itself on a little 20GB partition.  I would like to get rid of any unnecessary partitions and expand the 20gb partition so that Ubuntu can use it.  Ive tried using gparted but for some reason it wont let me re-size the partition.  Ive attached a screenshot of my drive which might help make a little more sense - can someone help please?

---

### Post by cusinndzl on 2010-05-31
I've had a similar issue, but with a different version. I just reinstalled Ubuntu. I'm wondering if there is a way to resize the operating system installation. I think the problem you are having might relate to /dev/sda5 having some smaller partitions between it and the unallocated space.

---

### Post by MikeSz on 2010-05-31
I have no idea what those are.  I think its something that Ubuntu put there when it was setting itself up, I went through the automatic process anyway, not the advanced bit so no idea what they are.  It seems a little daft that you cant just 'use' that unallocated space and extend the ubuntu partition

---

### Post by jerome1232 on 2010-05-31
You can't resize a partition while it's mounted.

You will need to boot the live cd to play with your partitions. You should be able to drag and drop the partitions around to where you want them.

I am uncertain as to whether changing the partition order will mess with grub, so you should probably run 'sudo update-grub' when your done with it all to make sure grub is updated.

---

### Post by HereInOz on 2010-05-31
I am guessing that the old Sabayon partition is /dev/sda2.  What you could do is to leave Ubuntu installed on the 20GB partition but then move your /home folder to /dev/sda2.  This has many benefits and will allow you to use this disk space for your data, leaving Ubuntu happily where it is.

You will find instructions on how to do this here:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by jeremyswalker on 2010-05-31
What's on /dev/sda2? If it's not anything important, your best bet would be to delete that and the swap partition. Then you should create a new swap partition at the end, and expand the root partition to fill the empty space. You should use the live CD, as you can't modify mounted partitions. You will also have to turn swap off in order to move it. Just right-click on it in Gparted and there should be an option to turn it off. Don't forget to backup.

---

### Post by oldfred on 2010-05-31
You have 'trapped' the extended partition. You can expand sda2 or create one more primary, but cannot expand the extended partition. I would reorganize before going too far and plan what partitions you may want now or in the future. It is usually best to have the extended partition last so you can expand it into the unallocated and create additional partitions.

If you have /home or a separate /data for all you data you only need about 10-20GB for root anyway, do it depends on what your needs are.

---

### Post by srs5694 on 2010-05-31
> **HereInOz said:**
> I am guessing that the old Sabayon partition is /dev/sda2.  What you could do is to leave Ubuntu installed on the 20GB partition but then move your /home folder to /dev/sda2.  This has many benefits and will allow you to use this disk space for your data, leaving Ubuntu happily where it is.

You will find instructions on how to do this here:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

This is what I recommend, too. Having a separate /home partition has many advantages over keeping /home on the system root (/) partition, as Ubuntu does by default. In fact, if /dev/sda2 has no user data you want to preserve, I'd delete it and create a new partition to take its place and to fill the unallocated space on the disk -- or did you mean that what had been the Sabayon partition is now the unallocated space?

---

