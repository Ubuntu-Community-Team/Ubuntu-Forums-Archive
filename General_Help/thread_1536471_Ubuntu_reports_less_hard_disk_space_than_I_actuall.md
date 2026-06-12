---
title: "Ubuntu reports less hard disk space than I actually have"
date: 2010-07-22
forum: General Help
---

### Post by ignotus666 on 2010-07-22
Hi 

I recently bought a new pc and installed Ubuntu on it. It came with a 500gb hard drive and during installation I manually partitioned it as follows:

10 gb (ntfs) for a windows partition
15 gb (ext4) mounted on /
4 gb for swap
the rest (470gb - ext4) mounted on /home

I've just installed a few apps from the repository, nothing big (about 500 mb in all), but in the 'file system' tab in 'system monitor' it says that for /home I have a total of only 432 gb, of which just 408 gb are available, with 500mb used. According to this, around 60gb of space have just vanished into thin air.

My question is:
Where did all this missing disk space go? The disk is brand new and there are no bad sectors in it.

Thanks in advance.

---

### Post by linux18 on 2010-07-22
It's the way disk space is calculated, the manufacturer counts size in base-10 and the OS counts in base-2. All of the space is there, just counted differently.

---

### Post by ignotus666 on 2010-07-22
Thanks for the quick reply

Ok, I (kind of) get it - I'll make a point of looking that up to get a better grasp. I just needed reassurance that there was nothing wrong with the hardware or software.

Cheers again!

---

### Post by CannibalZerg on 2010-07-22
Run in terminal
```

df -h

```It shows disk usage. I think that "wanished" space is the difference between GibiBytes (GiB = 1073741824 bytes) and GigaBytes (GB = 1 000 000 000 bytes). HDD manufacturers specify the size with GB, while Ubuntu shows used space in GiB.

---

### Post by Vaphell on 2010-07-22
on a sidenote: the difference between free and available space is because system reserves 5% for root, so there is no risk of running out of space and leaving the OS in an unusable state. In times of huge few hundred gigabyte partitions 5% is too much, you can set it to 1% with no problem.

[http://ubuntuforums.org/showthread.php?t=1487515](http://ubuntuforums.org/showthread.php?t=1487515)

---

### Post by amauk on 2010-07-22
> **CannibalZerg said:**
> HDD manufacturers specify the size with GiB, while Ubuntu shows used space in GB.
Just to clarify
that should be the other way around

1GB = 1,000MB = 1,000,000KB = 1,000,000,000B
1GiB = 1024MiB = 1,048,576KB = ....

Also here
[http://ubuntuforums.org/showthread.php?t=1355626](http://ubuntuforums.org/showthread.php?t=1355626)

---

### Post by ignotus666 on 2010-07-22
Thanks people, I'd never heard of these differences and you've definitely saved me time trying to figure all that out myself.

Take care!

---

