---
title: "Install Grub2 inside boot partition?"
date: 2010-03-10
forum: General Help
---

### Post by neu5eeCh on 2010-03-10
Hi folks, I need a little guidance. 

I have Ubuntu 9.10 installed in the second of two primary partitions. I just installed PCLinuxOS in the first partition. When PCLos wanted to install grub, I stopped it. As it is, I can't seem to edit Grub2 so that it will boot PClos.

So, here's my plan (based on googling).

Install Grub2 into 9.10's Boot partition.

Then reinstall PCLos and let it install legacy grub into the MBR. Once that's done, I'll try editing legacy grub so that it chainloads.

That's the plan. I have a vague idea how to do it. And I could use some guidance. First, how do I re-install 9.10's Grub2 into the Boot Partition?

Let me just start with that, then I'll ask questions as needed.

---

### Post by neu5eeCh on 2010-03-10
OK. Here's what I did.

I downgraded Ubuntu's Grub2 to Grub. I hoped that PCLinuxOS would recognize Ubuntu's Grub.

But it doesn't.

I no longer have the option to boot into Ubuntu - probably because PCLinuxOS doesn't recognize EXT4. 

How do I boot back into Ubuntu, and fix this problem?

---

### Post by neu5eeCh on 2010-03-10
Wow.

One can learn **a lot** when one is, like, *you know*,  completely ignored.

I downloaded Super Grub Disk and was able to boot back into Ubuntu. At  that point, I chose to upgrade from GRUB, back to GRUB2. This was, in  effect, like installing UBUNTU **after** installing PCLinuxOS. To a pro, this  has got to be an ugly, ugly way to do it. But it worked. I think, at  this point, I can add the corrected boot script for PCLinuxOS via the  40_Custom file.

---

### Post by Mark Phelps on 2010-03-11
Well ... one thing that you apparently did NOT learn was to have some patience.  Looks like your whole time here didn't exceed 5 hours.

Impatience like this will only get you ignored in the future.

---

### Post by neu5eeCh on 2010-03-11
> **Mark Phelps said:**
> Well ... one thing that you apparently did NOT learn was to have some patience.  Looks like your whole time here didn't exceed 5 hours.

Impatience like this will only get you ignored in the future.

Well Mark, glad you had enough time to posture. Just think, you could have been helping somebody else.

---

### Post by leorolla on 2010-03-11
> **Mark Phelps said:**
> Well ... one thing that you apparently did NOT learn was to have some patience.  Looks like your whole time here didn't exceed 5 hours.

Impatience like this will only get you ignored in the future.

Yesterday I had my partition table corrupted, I couldn't access anything on my hard disk.

Today, after opening a topic and waiting for a while, I got it fixed in security.

By the way, to fix these grub problems you only need this:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

