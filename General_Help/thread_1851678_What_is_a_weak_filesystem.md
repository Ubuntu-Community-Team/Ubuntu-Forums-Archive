---
title: "What is a weak filesystem?"
date: 2011-09-28
forum: General Help
---

### Post by lobo_tuerto on 2011-09-28
When I shutdown my laptop I've seen this message:

```
Unmounting weak filesystem.
```

Wondered what does it mean, what is a weak filesystem guys? (no luck googling).

---

### Post by dino99 on 2011-09-28
never seen such message, but that mean you have to do some maintenance before being completly borked

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo dpkg-reconfigure -phigh -a

sudo shutdown -r now
(will force a fsck on next boot)

run smart to check your hdd(s)

---

### Post by Blasphemist on 2011-09-28
You both should remember about google. What is the line that follows that message? Is it that / is busy? If so it is a bug that looks like it has a fix in oneiric but not the other releases yet. [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/616287](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/616287)

---

### Post by haqking on 2011-09-28
> **Blasphemist said:**
> You both should remember about google. What is the line that follows that message? Is it that / is busy? If so it is a bug that looks like it has a fix in oneiric but not the other releases yet. [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/616287](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/616287)

+1

Was just about to post that same link but you beat me to it.

The same bug in various other versions exists too back to some 2009 posts.

from google seems to be *buntu specific

---

### Post by Dangertux on 2011-09-28
Also important to understand this is not always caused by failing hardware. The main reason it occurs is usually because umountfs fails to cleanly unmount /. It can also be caused by failure to cleanly unmount nfs shares.

---

### Post by haqking on 2011-09-28
> **Dangertux said:**
> Also important to understand this is not always caused by failing hardware. The main reason it occurs is usually because umountfs fails to cleanly unmount /. It can also be caused by failure to cleanly unmount nfs shares.

indeed, a recurring pain for cloning and back in the day ghosting of NTFS.

---

### Post by lobo_tuerto on 2011-09-29
Where can I read the log about the shutdown process? So I can copy paste the output here since it shuts down pretty quick.

The bit I could look at said something along the lines:

* Unmounting weak filesystems...     [OK]
* Will now halt

Is that normal?

---

### Post by lobo_tuerto on 2011-09-29
By the way, this is on a fresh install, just zeroed (with dd) HD.

No other filesystems (that I know of) are present.

---

