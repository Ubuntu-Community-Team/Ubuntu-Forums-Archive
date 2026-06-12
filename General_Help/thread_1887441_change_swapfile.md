---
title: "change swapfile"
date: 2011-11-27
forum: General Help
---

### Post by eddski on 2011-11-27
i just added an additional drive to my desktop and wanted to put the swapfile on it in hopes of getting better performance, but i don't know how to do that or if its possible. can it be done and will it increase performance?

---

### Post by oldos2er on 2011-11-27
No, hard disk access is many orders of magnitude slower than RAM access, so swapping will degrade performance, not enhance it. Max out your RAM first.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by gdonwallace on 2011-11-27
Its more of a swap partition as opposed to a swap file.

The swap partition is going to be slower than memory anyway.  But if you wanted to do it, you would have to format the drive as a swap partition, then disable and reformat the existing swap partition into usable space.

---

### Post by andrew.46 on 2011-11-28
> **oldos2er said:**
> [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Nice page. My own situation is this one:

> 
High RAM and high disk space With 2 GB RAM and 100 GB hard disk, use 2 GB for swap since hard disk space is plentiful. 


although the disk is actually 300 GB. I have attempted to max out the ram + swap file several times, with conky watching, and it is very difficult to even make the swap file kick up to anywhere near the 1 gig mark :). But of course the golden rule is max out the physical ram....

---

### Post by eddski on 2011-12-04
thanks for your comments, will max out ram

---

