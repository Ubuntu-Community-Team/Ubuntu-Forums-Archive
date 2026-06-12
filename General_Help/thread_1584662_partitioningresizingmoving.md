---
title: "partitioning/resizing/moving"
date: 2010-09-29
forum: General Help
---

### Post by dunno on 2010-09-29
Okay, so I have an 80GB drive partitioned like this (assume ext3):
```
|-Swap 4GB-|------------filesys 64GB------------|--home 7GB--|-root 5GB-|
```
Usage looks like this:
```
|-Swap 4GB-|---filesys 14GB---|--home 6.5GB--|-root 4GB-|
```
I'd like it to look like this:
```
|-Swap 4GB-|---------filesys 46GB----------|----home 20GB----|--root 10GB--|
```

My understanding is that a partition can only be expanded into empty space after it, is that correct?

Is what I want to do possible using gparted running from the live cd without losing data?

What would the process be?
My guess is:
1. resize filesys to create unpartitioned space
```
|-Swap 4GB-|---------filesys 46GB---------|----empty 18GB----|--home 7GB--|-root 5GB-|
```
2. move/copy home into that unpartitioned space
```
|-Swap 4GB-|---------filesys 46GB---------|----home 18GB----|--empty 7GB--|-root 5GB-|
```
3. resize home
```
|-Swap 4GB-|---------filesys 46GB---------|----home 20GB----|--empty 5GB--|-root 5GB-|
```
4. move/copy root into the unpartitioned space where home used to be
```
|-Swap 4GB-|---------filesys 46GB---------|----home 20GB----|-root 5GB-|-empty 5GB-|
```
5. resize root
```
|-Swap 4GB-|----------filesys 46GB----------|----home 20GB----|--root 10GB--|
```

Any tips or pointers regarding partitioning/moving/resizing disks or using gparted are appreciated.

Thanks in advance,
Chris

---

### Post by hhh on 2010-09-29
My experience has been that you stand a good chance of getting a corrupt partition when trying to shrink partitions and/or move partitions so back up important data. Then try shrinking the "filesys" (/) partition, then expand /home. If everything is still cool, shrink /home and expand /root. BTW, I haven't seen too many schemes with a separate /root, but maybe I'm just misunderstanding your description (usually / is the "root" filesystem and then under that is a folder named root). I wouldn't bother with creating a blank partition and moving everything twice, but maybe someone else will disagree.

I think you'll end up having to back up /home and then reinstall your OS with a better partitioning scheme (I prefer the default Ubuntu way of everything under /, but I understand the need for other schemes). Here are a couple of useful links...
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://www.linuxplanet.com/linuxplanet/tutorials/4269/1/](http://www.linuxplanet.com/linuxplanet/tutorials/4269/1/)

---

### Post by dFlyer on 2010-09-29
If your running just linux, your waisting an awful lot of disc space with a 48 Gig file system and a 5 gig root. Why not combine root and file system to about 15 gig and apply the rest to your home folder which will hold all your files.

---

### Post by hhh on 2010-09-29
I agree with dFlyer, but I'd make "/" 20G since you have 15 almost used already.

---

### Post by dunno on 2010-09-29
Thanks to all for the info.

One of the links hhh gave suggested having a separate partition for /var and /tmp on server machines to isolate the r/w wear and prevent them from growing uncontrollably.  This is a server machine, all be it my personal server so prolly not all that important.

I want a separate /root for the same reason I want a separate /home, but it doesn't need to be nearly as large.

I reckon that '/' won't grow too much more, so dFlyer's suggestion to make it much smaller and /home much bigger makes sense.  However, making '/' too small will lead to a similar problem in the future.

If the consensus is that I'll have to reinstall the OS, then I'll just throw down $50 for a new 500GB drive or something.  Any comments/experience on the success of shrinking a partition?

Thanks again
Chris

---

### Post by hhh on 2010-09-29
I've moved a partition successfully, and I've shrunken a partition unsuccessfully. Back up what you need and give it a shot, be prepared for the consequences.

---

### Post by oleink on 2010-09-29
> **hhh said:**
> I've moved a partition successfully, and I've shrunken a partition unsuccessfully. Back up what you need and give it a shot, be prepared for the consequences.

Cannot stress backup enough! Although usually your stuff will be successful so give it a shot but as he said back up your stuff

---

### Post by srs5694 on 2010-09-30
> **dunno said:**
> I want a separate /root for the same reason I want a separate /home, but it doesn't need to be nearly as large.

Although /root *can* (I think) be placed on a separate partition, doing so is generally a bad idea. Consider an emergency situation: The computer can boot to a certain point, but some critical libraries, binaries, or configuration files are damaged, thus preventing a full boot. In such a situation, the system will enable a text-mode root login to enable you to fix the problem; however, there's no guarantee that any filesystem but the root (/) filesystem will be mounted. Thus, if you split /root off on its own partition, the root user's configuration settings will be missing, which could limit the usability of the account. Likewise for any files you might have stored in /root, like notes on how the system is configured, local backups of configuration files, etc.

In practice, /root should generally hold very few files, aside from root's configuration files (.bashrc and the like). This greatly reduces the benefits to be had from putting it on a separate partition; and as I just noted, splitting it off that way is likely to cause problems sooner or later. I recommend you not do it.

---

### Post by dino99 on 2010-09-30
i guess you have a real need for /root because its not how ubuntu is designed by default. For average user:

- / 10~15 Go
- swap: 2 Go
- /home: unlimited

**************
/var, /root usually are set on server(s) only and not always.

---

### Post by srs5694 on 2010-09-30
> **dino99 said:**
> /var, /root usually are set on server(s) only and not always.

Although /var is often split off on servers, I've never heard of this being done with /root, at least not by experienced administrators; see my previous post.

---

### Post by dino99 on 2010-09-30
was true mostly ages ago

---

### Post by srs5694 on 2010-09-30
> **dino99 said:**
> was true mostly ages ago

I think you may be thinking of /boot, which was often split off to work around BIOS access limitations. (/boot holds the kernel, and making it a separate partition gives you control over where on the disk the kernel resides.) Even today, it's often split off on systems that use RAID or LVM configurations, since not all boot loaders make it easy to access files in a RAID or LVM setup.

AFAIK, it's *never* been common practice to split /root (the superuser's home directory) into its own partition. That said, my knowledge of Linux and Unix system administration only goes back to 1995 or thereabouts. If this split was used in the 1970s, 1980s, or early 1990s I might not know about it.

---

### Post by dunno on 2010-10-05
GPartEd worked like a charm.  Shrunk my / partition, grew and moved my /home partition and grew and moved my /root partition without problem.

---

