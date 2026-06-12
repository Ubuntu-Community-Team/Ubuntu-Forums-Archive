---
title: "reconfiguring partitions"
date: 2010-06-15
forum: General Help
---

### Post by punkbohemian on 2010-06-15
Currently, my partitions are set up as such:

83GB ext3 free space
~10GB ntfs HP/Vista Recovery Partition
~93GB Ubuntu (Hardy Heron)

Originally, I tried to just have two partitions (recovery and ubuntu), but because of the different file systems, and the placement of the hp recovery partition, it has to be right in the middle.

This is basically what I want to do:

1) Reinstall Hardy Heron on a new (smaller) partition from the free space partition.
2) Once it's working properly, format the rest of the hard drive (getting rid of the recovery partition) and create a single ext3 partition.
3) Install another distro on this new partition.

Does anyone foresee any complications with all this slicing and dicing of my hard drive for which I should/could prepare?

---

### Post by warfacegod on 2010-06-15
Create a separate partition for your Home folder.

---

### Post by john newbuntu on 2010-06-15
Create an extended partition so that you can stuff most of your others partitions as logical ones.  This way you could have more distros later on.
Is the Hp/vista recovery partition required in the interim since you plan to get rid of it anyway?
Do you plan to have the original Hardy in addition to the new one or is it just a relocation?
I was also not sure on whether you have Win on another drive.

---

### Post by punkbohemian on 2010-06-15
I'll have to consider the extended partition approach.

The hp/vista partition will no longer be required once I have a stable ubuntu working. I think I'm comfortable enough with linux that I can get rid of windows entirely.

The other ubuntu I will be installing will also be hardy. I'm not interested in lucid. It's sole purpose will be to have a "safety" os that I can get back into (and back on the net for tech support) if/when I have complications with the new distro that I'll be learning. I want to do a fresh install because my current ubuntu has too much extra stuff that I won't need for this new streamlined version. Rather than going through and doing some spring cleaning with my current version of ubuntu, it would be faster/easier just to install fresh to a new partition.

However, I can't just format everything and start from scratch because I remember having a few problems setting up wireless/internet when I first started using ubuntu, but I had a fully functional vista (oxymoron, I know) partition with which I could surf the net and get tech support.

So, in short, all I want is a skinny ubuntu hardy, and plenty of space to tinker with another distro (I'm leaning towards debian or slackware at this point).

---

### Post by warfacegod on 2010-06-15
It's a very good possibility that your wireless issues will have been ironed out in a newer version of Ubuntu. I suggest 9.04 or 9.10 or at least one that is still supported as I don't believe Hardy is anymore.

---

### Post by warfacegod on 2010-06-15
Actually i take that back. Hardy is still supported but it won't be in less than a year.

---

### Post by punkbohemian on 2010-06-15
Yeah, I believe Hardy's support ends in Oct 2011, but that's fine. By then I'll be more than comfortable with my next distro, using that as a safety if I wish to try another.

So, I haven't heard anyone mention any flaws with my current plan. I guess that means I'm (probably) good to go?

---

### Post by warfacegod on 2010-06-16
See post #2. Having one massive partition is fine if you like. There are advantages to having a separate Home partition, however. The most obvious is having your data safely tucked away if you break your system. Another is that, if you do break your system, your settings with be saved also. Upon installation, it will look and behave like your old one. That includes themes, F.F. bookmarks/add-ons, Compiz settings, etc. The only thing you'll need to do is install the apps you want and remove the ones you don't.

---

### Post by punkbohemian on 2010-06-19
> There are advantages to having a separate Home partition, however.

Is there some kind of guide online for setting something like this up?

Also, I'd be concerned about how I would size it. It probably doesn't need to be that large for FF bookmarks, settings, etc. but when I consider all my music and movies (which are also stored in home, one would think I'd need to dedicate a lot of hd to it.

In other words, I'd want the partition to be large enough to keep everything, but not so large it dominates my hard drive.

As for Hardy's support running out, I'm not worried about that. By the time that happens, I'm sure I'll be plenty comfortable with my next distro, and won't even need Hardy for a backup.

---

### Post by warfacegod on 2010-06-20
> **punkbohemian said:**
> Is there some kind of guide online for setting something like this up?

Also, I'd be concerned about how I would size it. It probably doesn't need to be that large for FF bookmarks, settings, etc. but when I consider all my music and movies (which are also stored in home, one would think I'd need to dedicate a lot of hd to it.

In other words, I'd want the partition to be large enough to keep everything, but not so large it dominates my hard drive.

As for Hardy's support running out, I'm not worried about that. By the time that happens, I'm sure I'll be plenty comfortable with my next distro, and won't even need Hardy for a backup.

Probably a guide somewhere but I don't know where considering that I don't need one.:p

What else would you do with the HDD if not use it for data storage? Home should be the biggest partition by far. Here's a screenshot of my partition scheme. Notice that /home is the biggest. sda3 is my experiment partition (it have Home in the partition). Where I install other Linux distros and play (read break) with them.

A good rule is 15 GB for each OS, I use 10 because I know mine won't ever grow too big. You can see in the shot that I still have almost 7 GB to go in sda1 (since the end of February). A partition for swap equal to the amount of RAM in your computer. I stopped using swap over a year ago and my laptop is somewhat faster because of it. I used to have a 30 GB HDD and I couldn't afford the extra 2 GB. The rest can be for /home or whatever else you like.

---

