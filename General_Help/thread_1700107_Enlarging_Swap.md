---
title: "Enlarging Swap"
date: 2011-03-04
forum: General Help
---

### Post by SuperFreak on 2011-03-04
I recently enlarged my Root and Home partitions and in the process was left with 1.69 GB of unallocated space next to Swap(see image). Not quite sure how it happened this way but for some reason I was unable to grab all the unallocated space available when enlarging either Home or Root. What I am wondering is there any reason why I couldn't enlarge Swap and thereby use up that unused 1.69 GB? Would there be any minor advantage to this? Also if I did this would it simply be a matter of booting from Live Disc and running GParted with Swap off and grabbing that space?

---

### Post by plucky on 2011-03-04
> What I am wondering is there any reason why I couldn't enlarge Swap and thereby use up that unused 1.69 GB?

Swap is already 4Gb and if you have 4Gb of memory on your system,the chances are that you are not using a lot of swap.

> Would there be any minor advantage to this? 

It is best to use as little swap a possible as it is slow compared with on board memory.Better to add the space to /home partition.

> Also if I did this would it simply be a matter of booting from Live Disc and running GParted with Swap off and grabbing that space?

Remember changing the size of any partition will change the UUID of the partition.You will then have to change the UUID in /etc/fstab and for the swap also in etc/initramfs-tools/conf.d/resume to allow hibernation.

Good Luck

---

### Post by lithopsian on 2011-03-04
As already said, many people won't see the benefit of increasing swap further.  If you like to hibernate, it can be useful to have swap larger than you memory, otherwise it isn't necessary on machines with gigs of memory.  By the time you need 4GB of swap your machine will be unusable.

You can safely unmount swap within a normal session.  Of course you'll have to swapoff first.  Don't do this while you're running 25 apps and 100 tabs in Firefox!  Or just use the Live CD if you're worried.

Carefully check that the swap is successfully mounting after you change it, so you can fix any configuration issues before you need the swap.

---

### Post by SuperFreak on 2011-03-04
Thanks for your advice plucky and lithopsian. I think I will probably leave things as they are as there doesn't seem to be any real advantage to expanding Swap any further.

---

