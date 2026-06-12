---
title: "Moving Home from Main Drive to 2nd Drive."
date: 2012-04-19
forum: General Help
---

### Post by Cyberpawz on 2012-04-19
I have an old C640 Dell Latitude that I have given a second life to . 10 years old and the computer runs Ubuntu 11.10 flawlessly... well for what I need that is. Which is Email, Web Browsing, and writing books.  

So needless to say I am not trying to re-even the wheel, or even a new way of doing things.

Although the hacker in me (hardware hacking) has introduced a new piece of technology into this 10 year old laptop. A SATA drive as it's secondary drive. 

This means my CD drive is no longer being used for it's original purpose, and the USB is USB 1.1 so no booting from it recognized from the computer unless there is a firmware update I don't know about? 

Now you know my setup, don't ask if the SATA drive works yet, I haven't gotten to that point in the build. 

I am gutting an old floppy encasing to hold the HD, but at the same time hold a floppy as well, so that to the outside user the laptop will look like it is using a floppy drive and not a 2nd HD bay, when in reality it is.

What I am attempting to do if the SATA drive works the way I play is to make the SATA drive my Home instead of the primary drive having it on another partition. 

I would normally do what has been told on this forum, but with the CD out of commission, and the USB boot-ability not feasible as far as I know, is what I am asking possible? 

I can't imagine it's not, I just haven't found the answer. 

If anyone can help me at least with this aspect the rest of what I am doing will be a breeze I hope.

---

### Post by Cheesemill on 2012-04-19
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Cyberpawz on 2012-04-19
> **Cheesemill said:**
> [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I thought that required the need to boot from a CD to make this work?

---

### Post by Cheesemill on 2012-04-19
> **Cyberpawz said:**
> I thought that required the need to boot from a CD to make this work?
It doesn't mention that anywhere in the instructions.

I've just read them carefully and the process it describes will work without needing to boot from anything but your installed system.

---

### Post by oldfred on 2012-04-19
My concern might be it it works, is timing. When system boots it wants to find all the system mount points including /home. If external does not come up quickly then you may have boot issue.

I like to keep each drive as a fully bootable system including /home. But I have data on several drives that I mount & link back into /home. Even that may not work if external does not mount quickly enough but data partitions could be remounted or separately mounted if need be.

---

### Post by Cyberpawz on 2012-04-19
> **oldfred said:**
> My concern might be it it works, is timing. When system boots it wants to find all the system mount points including /home. If external does not come up quickly then you may have boot issue.

I like to keep each drive as a fully bootable system including /home. But I have data on several drives that I mount & link back into /home. Even that may not work if external does not mount quickly enough but data partitions could be remounted or separately mounted if need be.

I know what you mean, but as it stands I get that sometimes with the Hard Drive, I am replacing it soon anyway. The drive is an original, so needless to say it needs replacing anyway.

---

### Post by Cyberpawz on 2012-04-19
Well the SATA drive is recognized, 40GB SATA, more than enough space for what I need, now to make it my home drive and see how it takes. I'll tell you tomorrow since my work day is over.

---

