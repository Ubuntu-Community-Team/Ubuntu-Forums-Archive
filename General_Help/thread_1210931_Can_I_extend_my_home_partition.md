---
title: "Can I extend my /home partition?"
date: 2009-07-12
forum: General Help
---

### Post by b@sh_n3rd on 2009-07-12
Hey there, I'm using Jaunty and I added a second 3GiB HDD I had and set it up to mount automatically at boot. I use it to store files in an additional space and to keep backups. I was just wondering, is there a way I could extend my /home partition at sdb6 to my second HDD (sdb1)? just a Q... Thanks!

---

### Post by Chronon on 2009-07-12
As far as I know, you need to be using LVM to do that.  Logical volumes can be extended across two physical drives; physical volumes cannot.

---

### Post by andrewc6l on 2009-07-12
You could always migrate your /home partition from its current partition on your first drive to a new partition on the second drive. This wouldn't be extending, just replacing the existing partition with a larger one somewhere else.

You'd have to update /etc/fstab to mount /home on the new drive after copying the files / permissions over. Use cpio to do the copy... I used to know how to update fstab, but don't quite understand the UUID stuff in the new /etc/fstab I'm afraid :-)

---

### Post by b@sh_n3rd on 2009-07-12
Hi guys, thanks for your replies...
**Chronon,** what's LVM? It sounds promising :D
**andrewc6l, **Yes I *have* heard that I can migrate my /home folder to a different partition, but it seemed to be quite complicated :D. Anyways, my current /home folder is a 6GiB partition, so I was just wondering if I could extend that to the 3GiB drive. If it's possible it'd be really cool...Thanks once again...

---

### Post by Frugoo Scape on 2009-07-12
Just mount another drive to a folder in your home directory, other then that I believe you would have to be using LVM, like everyone else has been saying.

---

### Post by b@sh_n3rd on 2009-07-12
> **Frugoo Scape said:**
> Just mount another drive to a folder in your home directory, other then that I believe you would have to be using LVM, like everyone else has been saying.

uhh...what's LVM? And yes I've mounted it in a separate directory for now. I did think of mounting it in a different dir within /home though. Well, I suppose it really isn't possible to actually extend it then huh? Thanks for your replies though...but btw, what in the world is LVM?? :D

---

### Post by Frugoo Scape on 2009-07-12
> **b@sh_n3rd said:**
> uhh...what's LVM? And yes I've mounted it in a separate directory for now. I did think of mounting it in a different dir within /home though. Well, I suppose it really isn't possible to actually extend it then huh? Thanks for your replies though...but btw, what in the world is LVM?? :D

Unless your installed ubuntu with LVM, then your going to have to do what I said. You could create a LVM disk, remount your stuff using that disk and transferring the stuff onto it.

**LVM:**
[http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))

---

### Post by TeamJ on 2009-07-12
I really am a n00b but couldn't you use RAID?

---

### Post by b@sh_n3rd on 2009-07-12
> **TeamJ said:**
> I really am a n00b but couldn't you use RAID?

Well, read the green bit in my signature. I'll give you a clue. My PC was manufactured on the 6th of June 1998! :D still running strong. I got it second-hand anyways not brand new so I'd be like, the second owner...Anyways, My Q did remind *me* of RAID too...

---

