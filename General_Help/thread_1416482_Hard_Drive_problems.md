---
title: "Hard Drive problems"
date: 2010-02-26
forum: General Help
---

### Post by Sentience on 2010-02-26
I am very surprised that the community does not seem up to date or to be acknowledging compatibility issues leading to damaged hard drives. Has anyone figured out what is going on with this yet? Has it been fixed?

Every computer that I had Karmic Koala on has had hard drive failures or other problems.My laptop hard drives have completely failed, and I do not believe this is a coincidence.


Now I cant connect to the internet on windows on my desktop. It says there are 4 disks but there is only 1. 

This was looking like the most user friendly version of Linux so far, but nobody seems to be addressing the hard drive failures.

---

### Post by johngreth on 2010-02-26
I've never heard of anything like this. Did you check the integrity of the disk (md5 or sha sum and check integrity option on live cd)? I can't think of any reason all the hard drives failed unless you have a bad disk or have installed something nonstandard on all the computers.

---

### Post by Mark Phelps on 2010-02-27
> **Sentience said:**
> I am very surprised that the community does not seem up to date or to be acknowledging compatibility issues leading to damaged hard drives. Has anyone figured out what is going on with this yet? Has it been fixed?

Every computer that I had Karmic Koala on has had hard drive failures or other problems.My laptop hard drives have completely failed, and I do not believe this is a coincidence.


Now I cant connect to the internet on windows on my desktop. It says there are 4 disks but there is only 1. 

This was looking like the most user friendly version of Linux so far, but nobody seems to be addressing the hard drive failures.

I've heard of this a LOT -- and it has me worried, too!

At first, it seemed like a lot of false positives -- Palimpset reporting drive problems where there were none.  But over time, there have been followon posts of more and more folks saying their drives DID subsequently fail .

And, this was only AFTER installing 9.10!

What makes 9.10 unique from the earlier versions is it's the first one to use Ext4 filesystem as the default (and yeah, it uses the new GRUB2, but that's very unlikely to be the problem).

So, I'm beginning to think maybe there is something to this Karmic-is-killing-my-hardrive thing!

---

