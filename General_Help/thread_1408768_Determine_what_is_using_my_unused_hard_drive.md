---
title: "Determine what is using my unused hard drive?"
date: 2010-02-16
forum: General Help
---

### Post by KayakJim on 2010-02-16
I have Ubuntu 9.04 64-bit desktop running on my laptop, which has 2 drives - a 64GB solid state drive and a 320GB traditional hard drive.

I have everything on the SSD and in fact the 320GB drive is not even formatted or mounted.

However, starting about 10 minutes before this post I started hearing activity on the drive and the drive busy LED is flashing.

How can I determine what is using the drive and what it is doing?

---

### Post by akakingess on 2010-02-16
> **KayakJim said:**
> I have Ubuntu 9.04 64-bit desktop running on my laptop, which has 2 drives - a 64GB solid state drive and a 320GB traditional hard drive.

I have everything on the SSD and in fact the 320GB drive is not even formatted or mounted.

However, starting about 10 minutes before this post I started hearing activity on the drive and the drive busy LED is flashing.

How can I determine what is using the drive and what it is doing?

I guess the first thing to do is install the program 'Top', which will show every app or daemon that is currently running, and see if any of those that are running are something like a disk utility or an indexer. I know there used to be an app  (I can't remember the name, but thought it was something like 'weasle' or something like that) that would constantly scan the drives in order to keep everything 'indexed' for faster searching, etc. But I would definitely install "top" or it's colorful version 'htop' to see what is running on your system. That's all that I have for now, let us know what you find.

---

