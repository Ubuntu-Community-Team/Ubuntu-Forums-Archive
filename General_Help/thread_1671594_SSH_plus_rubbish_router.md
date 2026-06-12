---
title: "SSH plus rubbish router?"
date: 2011-01-20
forum: General Help
---

### Post by andyzammy on 2011-01-20
Hi all,

I'm currently moving a lot (200G) from an external hard drive on one pc to an external hard drive on a laptop and I'm using scp to do it. I have a bt home hub 2.0 and as luck would have it my laptop keeps getting disconnected from the network.I'm worried that this will result in data loss or corruption as this has happened about 5 or 6t times just that I was aware of.

Could someone tell me what to expect? Should I compare, should I retry with ethernet or am I in the clear?

---

### Post by muteXe on 2011-01-20
So it's all copied over but you're not sure if stuff has gone missing?
You could, for starters, do a right-click properties on the overarching folder and see if it's the same size as the source folder on your other machine.

---

### Post by andyzammy on 2011-01-20
It's actually still copying over so no point in checking anything until it's finished. I was just wondering if it was worth carrying on or starting again. I guess I wanna know if ssh is_that_ good?

---

### Post by muteXe on 2011-01-20
Can you plug the external drive into the destination laptop, and bypass the router?

I had a bt homehub while a while. It was pretty terrible.

---

### Post by andyzammy on 2011-01-20
> **muteXe said:**
> Can you plug the external drive into the destination laptop, and bypass the router?

I had a bt homehub while a while. It was pretty terrible.

I cannot because one of the hard drives is in some fat format ([http://ubuntuforums.org/showthread.php?t=1621657](http://ubuntuforums.org/showthread.php?t=1621657))

I guess it's not just a bt problem, it's a whole wireless thing.no matter what hw or os I've used, I've always experienced some drops from whatever router I've used. For years.what the hell. but one thing that confuses me about the bt router is why you're only allowed to you've ONE device and ONLY ONE device access to a port. Again, what the hell. But I digress.. I'm only concerned for my data for now

---

### Post by andyzammy on 2011-01-20
> **muteXe said:**
> Can you plug the external drive into the destination laptop, and bypass the router?

I had a bt homehub while a while. It was pretty terrible.

I cannot because one of the hard drives is in some fat format ([http://ubuntuforums.org/showthread.php?t=1621657](http://ubuntuforums.org/showthread.php?t=1621657))

I guess it's not just a bt problem, it's a whole wireless thing.no matter what hw or os I've used, I've always experienced some drops from whatever router I've used. For years.what the hell. but one thing that confuses me about the bt router is why you're only allowed to you've ONE device and ONLY ONE device access to a port. Again, what the hell. But I digress.. I'm only concerned for my data for now

---

### Post by andyzammy on 2011-01-20
> **muteXe said:**
> Can you plug the external drive into the destination laptop, and bypass the router?

I had a bt homehub while a while. It was pretty terrible.

I cannot because one of the hard drives is in some fat format ([http://ubuntuforums.org/showthread.php?t=1621657](http://ubuntuforums.org/showthread.php?t=1621657))

I guess it's not just a bt problem, it's a whole wireless thing.no matter what hw or os I've used, I've always experienced some drops from whatever router I've used. For years.what the hell. but one thing that confuses me about the bt router is why you're only allowed to give ONE device and ONLY ONE device access to a port. Again, what the hell. But I digress.. I'm only concerned for my data for now

---

### Post by andyzammy on 2011-01-20
> **muteXe said:**
> You could, for starters, do a right-click properties on the overarching folder and see if it's the same size as the source folder on your other machine.

> **muteXe said:**
> You could, for starters, do a right-click properties on the overarching folder and see if it's the same size as the source folder on your other machine.

okay transfer has finished, this is the best i can do to compare size + files:

Transferred from:
2872 items (2651 files + 221 folders), 272GB  <--- According to Windows
273GB                                         <--- According to Ubuntu Server

Transferred to:
2860 items (???), 272.3GB                     <--- According to Ubuntu

is there any way to diff directories separated over ssh?

---

