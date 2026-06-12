---
title: "EXT4 Warning"
date: 2010-01-30
forum: General Help
---

### Post by JohnnyJonJon on 2010-01-30
Ever since I installed 9.10 I have been experiencing "hic-ups", or cpu lag if you will, which I thought was due to ext4 bugs... turns out I was only partially correct.

My setup was system/home/swap all on one hard drive.  The problem is with the swapping functions and the ext4 functions conflicting which result in "hic-ups", wasted cpu cycles or disk i/o waits.  I went to a second hand computer store and bought a used 8 GB hard drive for about $5 and format/partition as a swap device, then removed the swap partition off my system drive.  Ubuntu is now running at peak performance and ext4 is the major upgrade from ext3 that it should be.

I don't know where to post this so I will hit the gen forum and hope word gets around.

---

### Post by howefield on 2010-01-30
> **JohnnyJonJon said:**
> ...and hope word gets around.

What word is that then ?

Are you saying ext4 and swap do not co-exist well on the same hard drive ?

---

### Post by Leppie on 2010-01-30
what do you use the swap for? it's usually only for hibernating and cpu intensive tasks like photo/video editing.

---

