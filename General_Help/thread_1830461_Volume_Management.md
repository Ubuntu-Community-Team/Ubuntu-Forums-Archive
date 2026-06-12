---
title: "Volume Management"
date: 2011-08-21
forum: General Help
---

### Post by ClientAlive on 2011-08-21
Hi,

So I have this desktop I've been building up and have finally gotten all the hardware I need to show up and the thing to function. Now I've set my focus on volume management. I got to reading about RAID, LVM, and something called MDADM today and thinking about a good scheme to use with hardware I have available on the machine. I attached a hand drawn diagram to this post and was hoping to get some feedback on my ideas. Does it seem like something that is possible? Perhaps there is a better way to get what I"m after? Can anyone fill in some of the blanks on terminology for me? I'd sure appreciate any help I can get. Lord knows, I need it.

By the way, 'what I'm after' is:

I read somewhere that RAID 1, with it's mirroring, can increase read speeds for me. That was the first thing that perked my ears up, but the whole redundancy/ data protection thing is important too. At the moment I was reading that, I had only 2 drives in the box (1 X 100 GB + 1 X 75.9 GB). Then I got to thinking about this third drive I had sitting there and how I might use it somehow too. That one is the 80 GB drive. With all this thinking about RAID, I didn't want to just have some third drive hanging out there like an extra thumb, so I got to thinking about how I could maybe use it for data storage and somehow build a little redundancy/ data protection into it's involvement too. That's how I came up with the ideas expressed in the attached file.

Really though, I'm not set on functions/ uses of the different drives yet - I'm still kicking that part around a bit. Can anyone offer some input on this scheme I hatched? I'd sure appreciate it. Thanks in advance for your help.
----------------------------

Edit:

I noticed that I forgot to account for 4.1 GB of space on the drive I'd labeled "C" in the diagram. I just forgot to write it in but my intention for that 4.1 GB of space was for it to be the swap file and not involved with RAID or anything going on with the rest of the scheme. Just like it was hanging out there on it's own, no redundancy, no involvement with the rest of the scheme, and used as the swap file for everything that would need one (just point everything that uses a swap file to it).

That raises another, different, question - but I'll save it for now.

---

### Post by ClientAlive on 2011-08-23
bump

:D

Anybody?

---

### Post by ClientAlive on 2011-08-28
I thought of a much simpler scheme - if it can be done.

Diagram attached to this post.

---

