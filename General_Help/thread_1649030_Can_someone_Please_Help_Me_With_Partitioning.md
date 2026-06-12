---
title: "Can someone Please Help Me With Partitioning"
date: 2010-12-19
forum: General Help
---

### Post by Mindswap1 on 2010-12-19
Hi guys! I've looked at every guide possible even the idiot proof ones, but I couldn't manage to learn how to partition. I was getting sick of having to backup my data every time I had to reinstall Ubuntu, so someone recommend that I partition my hard drive so that I could store all my personal files ( documents, music, and vidoes ) onto the seperate partition. However I don't know how to do this. Furthermore when a new version of Ubuntu is release I always pick the install on the entire hard drive so the partition i installed would end up being deleted. So How do you install Ubuntu by manually specifying the partitions. Thank You So Much In advance!

---

### Post by nothingspecial on 2010-12-19
Try this

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I couldn`t explain it in simpler terms. :D

---

### Post by Verbeck on 2010-12-19
select manually partition from the installer and make
1. 15 gb, mount point /, type ext4
2. ram size, type = swap
3. the rest , mount point /home, type ext4

and the next time you need to install, manually partition again, but only check the box for 'format partition' for the 15 gb /

hope you get the concept

---

### Post by nothingspecial on 2010-12-19
> **Verbeck said:**
> select manually partition from the installer and make
1. 15 gb, mount point /, type ext4
2. ram size, type = swap
3. the rest , mount point /home, type ext4

and the next time you need to install, manually partition again, but only check the box for 'format partition' for the 15 gb /

hope you get the concept


 ```
15 gb, mount point /
``` ???????????????? That`s crazy, what do you have installed?

---

### Post by Verbeck on 2010-12-19
> **nothingspecial said:**
> ```
15 gb, mount point /
``` ???????????????? That`s crazy, what do you have installed?
:)
need a big /tmp for dvd burning i guess
~think positive~

---

### Post by nothingspecial on 2010-12-19
hmm :-k

To the op, you need less than 3gigs for a full ubuntu install.

To be safe, I`d do twice that, 6 gigs.

---

### Post by srs5694 on 2010-12-20
IMHO, 6 GiB is close to the minimum I'd recommend unless you've got very little in the way of resources. Most of my Linux installations (I've got many of them) use at least that much space in root (or the equivalent; some of mine split off other partitions). Packages like OpenOffice.org, desktop environments (KDE, GNOME, Xfce), and programming tools can suck up disk space pretty quickly. I generally recommend 5-20 GiB for root (/), depending on available disk space and planned use of the system. Given that modern hard disks are typically hundreds of gigabytes in size, guessing too big by 5 or 10 GiB isn't a big deal. Guessing too small, OTOH, is likely to result in a need to resize the partitions, which is both a pain and risky. Repartitioning operations often go smoothly, but when they don't you can end up losing a lot of data, so it's best to avoid them whenever possible.

---

