---
title: "Unable to use Gparted"
date: 2010-03-29
forum: General Help
---

### Post by Arch Linux on 2010-03-29
Whatever I do, I get this:
```
WARNING: the kernel failed to re-read the partition table on /dev/sda (Device or resource busy).  As a result, it may not reflect all of your changes until after reboot.

```
Help? A reboot doesn't change anything.

---

### Post by n0dix on 2010-03-29
Are you try with a Live CD?

---

### Post by Arch Linux on 2010-03-30
It works with Live-CD but I wouldn't want to do any minor change from it :(.

---

### Post by n0dix on 2010-03-30
> **Arch Linux said:**
> It works with Live-CD but I wouldn't want to do any minor change from it :(.

What do you want to do with Gparted?
What is the problem you get?

---

### Post by Arch Linux on 2010-03-30
I mean when trying to create or modify partitions in any way.

---

### Post by n0dix on 2010-03-30
If you run the Gparted from console you get the same error?
```
$ sudo gparted
```

---

### Post by Mark Phelps on 2010-03-30
The message indicates that the partition you're trying to modify is in use, that is, is "mounted".

You would do better going to distrowatch.com, downloading and burning the GParted LiveCD, booting from it, and then doing the partition work.

---

### Post by srs5694 on 2010-03-30
> **Arch Linux said:**
> It works with Live-CD but I wouldn't want to do any minor change from it :(.

Are you saying you don't want to deal with the hassle or are you saying you don't trust it when booted in this way?

If it's the hassle, consider that most people don't need to run partitioning software very often. The need to boot a live CD to use the partitioner is not absolute for all modifications, but when it is required, it's a fundamental kernel issue, so you'll just have to deal with it. If you really need to make changes very often, please elaborate on why; perhaps somebody can suggest ways to work around the problem.

If it's a trust issue, then why don't you trust it? This seems like an irrational mistrust to me. If you've got a specific reason, then please elaborate. If not, then don't worry; in my experience it's no more (or less) dangerous to run partitioning software from an emergency disc than from a hard disk, all other things being equal. (There are known bugs in certain versions of all partitioning tools, so that can certainly be an issue, but it's not one that favors either method in a uniform way.)

---

### Post by Arch Linux on 2010-03-30
@n0dix, yes.

@Mark Phelps, I already told that - in my last post :).

@srs5694, I didn't quite understand your "trust" thingy. The thing just is that some time ago I didn't need to boot up to the Live CD when resizing or creating partitions.

And, well, if you really *want* to know why *I* want to so often modify *my* partitions then I guess I can tell *you* :D.
My Windows partition is like 100gb. I want my brother to move from away Windows so every time he is about to use my Win partition, I resize it so that it has like 2GBs left (so that it's slightly slower and he can't save much stuff into it). When I want to use it, I change it back. 

If you also want to know the whole story, I guess I can tell you that too :D.

---

### Post by psusi on 2010-03-30
The kernel can not update its in memory partition table while any partition on the disk is in use, which is why you should run gparted from the livecd.  In Karmic, a new method is used that allows you to modify unmounted partitions and create new ones on the same disk that has other partitions in use.  This was broken in lucid until yesterday or so.

---

### Post by Intrepid Ibex on 2010-03-30
psusi is correct, there is no way to "fix" this but there is a workaround that has already been implemented.

---

### Post by Arch Linux on 2010-03-30
@psusi, but of course - this was the answer I was looking for :).

I don't yet mark this as solved, if someone wants to add something.

---

### Post by srs5694 on 2010-03-30
> **Arch Linux said:**
> @srs5694, I didn't quite understand your "trust" thingy. The thing just is that some time ago I didn't need to boot up to the Live CD when resizing or creating partitions.

And, well, if you really *want* to know why *I* want to so often modify *my* partitions then I guess I can tell *you* :D.
My Windows partition is like 100gb. I want my brother to move from away Windows so every time he is about to use my Win partition, I resize it so that it has like 2GBs left (so that it's slightly slower and he can't save much stuff into it). When I want to use it, I change it back. 

Prior to the post to which I was replying, your answers were short and cryptic. It was unclear what you were trying to accomplish, why you wanted to do what you want to do, or why you were objecting to the advice to use a live CD.

IMHO, what you're doing is dangerous. Messing with filesystem data structures should not be done casually. A power outage or system crash during such an operation can hopelessly corrupt the partition. Ditto for a bug in the resizing software. If you're messing with a logical partition, such problems can render all the subsequent logical partitions inaccessible. Windows can be rendered unbootable by changes to its boot partition.

As an alternative, Windows may support some sort of disk quota system that would accomplish the same goal, but I'm not an expert on this topic. (Try Googling "Windows disk quota".) Another option is to create a big file with a command like this:

```

dd if=/dev/zero of=deleteme.img bs=1048576 count={size in megabytes}

```

Replace "{size in megabytes}" with a value ("2048" to create a 2GB file, for instance). Store the file in a directory to which your brother has no access and he won't be able to delete it. I'm not sure how long this type of operation would take on an NTFS partition, though; it could be prohibitively time-consuming.

---

### Post by Arch Linux on 2010-03-31
Hey, why didn't I think of dd.

---

### Post by pwn on 2010-06-14
I have the same error and it doesn't work from the LiveCD either.

---

