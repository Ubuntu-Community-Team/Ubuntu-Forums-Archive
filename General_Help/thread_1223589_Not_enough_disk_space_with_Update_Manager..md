---
title: "Not enough disk space with Update Manager."
date: 2009-07-26
forum: General Help
---

### Post by shr1975 on 2009-07-26
I just installed Ubuntu 9.04 and when I restarted my PC I got an alert from the Update Manager about updates for some components.

However, when I clicked on 'Install Updates', I got an error message that read, "Not enough free disk space. The upgrade needs a total of 374M of free space on '/'. Please free an additional 308M of disk space on '/'...".

I did a 'df' and found that my '/' has only 67M free.

I cleared my trash and also ran sudo apt-get clean.

I am new to the Linux environment. How can I get rid of this problem?

Thanks.

---

### Post by philinux on 2009-07-26
Open a terminal. Apps>access>terminal
Use this code and post back the result.

```
df -h
```

---

### Post by shr1975 on 2009-07-26
> **philinux said:**
> Open a terminal. Apps>access>terminal
Use this code and post back the result.

```
df -h
```

Here's the result:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda9  2.3G  2.2G   26M  99%         /

I have truncated the rest of the output for the sake of brevity.

---

### Post by philinux on 2009-07-26
> **shr1975 said:**
> Here's the result:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda9  2.3G  2.2G   26M  99%         /

I have truncated the rest of the output for the sake of brevity.

Please post it all.

Ubuntu needs minimum 5 gig. When you installed you didn't give it enough space.

---

### Post by drs305 on 2009-07-26
It looks like you have the 'classic' 2.3-2.5GB new installation. When you selected 'side by side' setup with Windows, you have to move the tab in the bottom partition graphic or it defaults to 2.3 or 2.5GB, at least in Jaunty. I consider it a bug, but if not, it is at least not obvious how to correctly set it up.

Ubuntu can't operate on a partition that small. Your two options are to reinstall and correctly size the / partition, or expand it by taking space from another (windows probably) partition.

I've written guides to do both of these:
[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

[2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")

---

### Post by shr1975 on 2009-07-26
Thanks for your quick response guys.

I have attached the complete output.

Thanks drs305 for the links. I will go through them and hopefully, they resolve my problem :)

---

### Post by drs305 on 2009-07-26
Yes, it looks like that is what happened. The links I provided in my earlier post should help.

I have filed a 'bug' report here:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/404910]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/404910/+edit")

It may or may not be a bug, but having the default partition size set at 2.3 to 2.5 GB unless the user makes changes should be altered.

---

### Post by harmlessdrudge on 2009-08-13
I consider this a bug. An installation that can't be updated? Even if there are hundreds of Gb of free space!

Thanks to the instructions here I was able to fix quickly. I think the default partition size should be larger.

---

### Post by filifunk on 2009-08-19
is anyone else having trouble expanding your "ext" partition to take the unallocated space?  I can't drag it out.  How do I do it?  I can shrink the size of a partition but I can't expand it over the unallocated partition.

Thanks

---

### Post by drs305 on 2009-08-19
> **filifunk said:**
> is anyone else having trouble expanding your "ext" partition to take the unallocated space?  I can't drag it out.  How do I do it?  I can shrink the size of a partition but I can't expand it over the unallocated partition.

Thanks

If you are trying to expand your / system partition, this guide will walk you through it:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by filifunk on 2009-08-19
thanks I've looked at that.  I've found out that the reason why I can't expand it is because it is mounted.  How do I unmount it?

---

### Post by drs305 on 2009-08-19
> **filifunk said:**
> thanks I've looked at that.  I've found out that the reason why I can't expand it is because it is mounted.  How do I unmount it?

If this is your system partition, you will have to use the LiveCD or a rescue CD (SystemRescueCD, gparted, etc) since you can't unmount the / partition while your normal Ubuntu installation is mounted. Once you have booted to the LiveCD's desktop (or via one of the other 'rescue' cds), you can run gparted via System, Administration, Partition Editor.

For non-system partitions using gparted, you should be able to highlight the partition, right click and select Unmount.

---

### Post by filifunk on 2009-08-19
here's a pic

---

### Post by filifunk on 2009-08-19
I am using my LiveCD...and when I right click it won't unmount

---

### Post by drs305 on 2009-08-19
> **filifunk said:**
> I am using my LiveCD...and when I right click it won't unmount

You also must unmount the swap partition. Highlight the swap partition, right click, and select Swapoff.

---

### Post by filifunk on 2009-08-19
haha that did help, but I still can't get it to expand over the unallocated part.  Should I right click on the unallocated portion and click on "new" and then make it "ext3" will that work?  sorry this is taking so long

---

### Post by drs305 on 2009-08-19
> **filifunk said:**
> haha that did help, but I still can't get it to expand over the unallocated part.  Should I right click on the unallocated portion and click on "new" and then make it "ext3" will that work?  sorry this is taking so long

Did you follow the steps in the guide I linked in post #10. If it is incomplete I'd be happy to expand it.

You cannot expand it since the unallocated space and the ubuntu partition are not in the same area. They both must be in the primary partition area or both in the extended partition section. You can't span the "light blue" line in gparted.

You must first expand the extended partition to incorporate the free space, then can expand the ubuntu partition once the unallocated space is within the extended partition. It's explained in the guide.

---

### Post by filifunk on 2009-08-20
Thanks drs!  I didn't read closely enough.  It all worked out, thank you much!  I'm on my way to ubuntu land!!!

---

