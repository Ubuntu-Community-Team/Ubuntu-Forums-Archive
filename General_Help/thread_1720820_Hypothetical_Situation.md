---
title: "Hypothetical Situation"
date: 2011-04-03
forum: General Help
---

### Post by Habeouscorpus on 2011-04-03
Say I wanted to dual boot Crunchbang, Ubuntu and Debian on one machine. I have a separate /home partition for Ubuntu. Could I reuse this partition for the home partitions of Debian and Crunchbang, since they're all based on Debian? If so, how?

I'm contemplating a distro move.

---

### Post by TeoBigusGeekus on 2011-04-03
I think it would just be as simple as a change to the fstab file.
...Though I've read (somewhere) that it is not recommended - too error prone.

---

### Post by techunit on 2011-04-03
If you want a headache go right a head!

Really bad idea. You could but you going to need to create an extended partition before it will work. And manually partition every OS.

I would create a Fat32 partition that you can use to share files between them with.

---

### Post by Habeouscorpus on 2011-04-03
Hmm. That stinks. How could I create an extended partition on Ubuntu? 

And I'm not afraid of manual partitioning - I knew I'd have to do that when I asked!

---

### Post by snowpine on 2011-04-03
> **Habeouscorpus said:**
> Say I wanted to dual boot Crunchbang, Ubuntu and Debian on one machine. I have a separate /home partition for Ubuntu. Could I reuse this partition for the home partitions of Debian and Crunchbang, since they're all based on Debian? If so, how?

I'm contemplating a distro move.

This should work just fine. Make sure you use a different username and UUID for each distro so there are no conflicts.

---

### Post by techunit on 2011-04-03
> **snowpine said:**
> This should work just fine. Make sure you use a different username and UUID for each distro so there are no conflicts.
That would actually defeat the purpose and add to the confusion.

@Habeouscorpus boot into a live cd with gparted on it (Ubuntu one will work) and create a partition as extened. simple.

---

### Post by Habeouscorpus on 2011-04-03
> **techunit said:**
> That would actually defeat the purpose and add to the confusion.

@Habeouscorpus boot into a live cd with gparted on it (Ubuntu one will work) and create a partition as extened. simple.


Yay, simple! I'm actually playing with VMs right now. Thanks for the suggestion. 

(And I thought UUIDs were assigned by the OS?)

---

### Post by lithopsian on 2011-04-03
I'm lost with some of the comments on here.  FAT32 partition?  Why on earth would you want to do that to share data between three different Linux distros?  A shared data partition is certainly a good idea and I would recommended you make it separate from the /home partition(s).  Make it ext4, or your preferred Linux file system, just like every other partition.  Use FAT32, or NTFS, only for compatibility with other OS types.

Major headaches because you need an extended partition?  It is pretty straightforward to create dozens of partitions even on a single drive and anyone who can't do it probably wouldn't be asking this question.

Also think about sharing a swap partition.  One reason *not* to do this is if you want to hibernate into one distro and then boot into a different one, but on the whole it might be best to avoid doing things like that.

The only real question is compatibility of your /home partition between three distros.  This is certainly possible but prepare yourself for some glitches.  Think carefully about not just things like your DM/WM configurations, file system caches and trashes, but also things like browser cache and email folders.  They can all be shared but you'd better be careful about keeping application versions consistent or you can end up with a right mess.  As for using different user IDs that is pretty pointless.  Use the same one and aim for an exact clone of the user in each distro.  Otherwise just have three separate /home partitions and the shared data partition.

---

### Post by techunit on 2011-04-03
> **lithopsian said:**
> I'm lost with some of the comments on here.  FAT32 partition?  Why on earth would you want to do that to share data between three different Linux distros?  A shared data partition is certainly a good idea and I would recommended you make it separate from the /home partition(s).  Make it ext4, or your preferred Linux file system, just like every other partition.  Use FAT32, or NTFS, only for compatibility with other OS types.

Major headaches because you need an extended partition?  It is pretty straightforward to create dozens of partitions even on a single drive and anyone who can't do it probably wouldn't be asking this question.

Also think about sharing a swap partition.  One reason *not* to do this is if you want to hibernate into one distro and then boot into a different one, but on the whole it might be best to avoid doing things like that.

The only real question is compatibility of your /home partition between three distros.  This is certainly possible but prepare yourself for some glitches.  Think carefully about not just things like your DM/WM configurations, file system caches and trashes, but also things like browser cache and email folders.  They can all be shared but you'd better be careful about keeping application versions consistent or you can end up with a right mess.  As for using different user IDs that is pretty pointless.  Use the same one and aim for an exact clone of the user in each distro.  Otherwise just have three separate /home partitions and the shared data partition.
@lithopsian
You can only have 4 partitions on a drive! An Extended partition is required to have any more than 4. So effectively you have to have tree partitions and an extented partition containing the rest.

Fat32 is only because it is easily read by any os and if he were to add windows later (not the greatest idea)he could access it as well.

The swap partition would be used by default for all the operating systems

Creating a shared partition will be less glitchy and far less problematic in the long run. Storing his files there would be better. And when reinstalling they would stay on the computer!

I hope this clears up why the things I say are said.

---

### Post by darkstaar on 2011-04-03
Just wanted to add that I ran Linux Mint 5 using my old Ubuntu 8.04 home partition. Had all of the added benefits of Mint with my original Ubuntu look. It actually worked so well that I skipped the 8.10 release entirely, only to come back to a straight Ubuntu install with 9.04.

Not that I'm suggesting that you rush headlong into something like this (as I did). Just that I luckily wound up with a system that happened to work flawlessly. So, yes, it's possible. And if you end up experimenting, make sure that you can recover from any screw-ups that might come up.

---

### Post by techunit on 2011-04-03
That might happen but Ubuntu has changed alot since then. and because mint and Ubuntu both are based on gnome it would work.

I am surprised I haven't asked this earlier, but why haven't you looked into VM?

---

