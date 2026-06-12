---
title: "GRUB error 22-- HELP!"
date: 2010-02-12
forum: General Help
---

### Post by linmalex on 2010-02-12
Hi. So here's my problem. I deleted the partition Ubuntu was on (I know, I know, stupid. Spare me, I need pity), and now I'm getting GRUB error 22. All the advice I read online says I should get myself a copy of a live CD (done) and put it in and make sure the boot order is such that it will boot from the CD drive (done) but it is still giving me the error. 

I'm running Vista right now, and I've been using that mostly because of another, separate issue I've been having with Ubuntu (no sound whatsoever)

Any advice? Anything?

---

### Post by ironclaw on 2010-02-12
I assume that you did not have a separate /boot/ partition? If that's the case, then when you deleted the Ubuntu partition, GRUB can not longer read the files that it needs in /boot/grub/.

You can just reinstall Ubuntu into the unallocated space and it should automatically reconfigure GRUB with entries for both Ubuntu and Windows. Or if you're not planning to reinstall Ubuntu, boot from a Windows recovery disk and overwrite the master boot record.

---

### Post by linmalex on 2010-02-13
Well, I was planning on reinstalling ubuntu, but I can't get that far. I put in the liveCD, but it gives me the error message before it can boot from the cd. That's my problem right now.

---

### Post by mechro on 2010-02-13
Is your computer's BIOS set so that it will boot from a CD?

If the LiveCD is faulty then it won't boot and your computer will try and boot from the Hard Drive which is giving you a Grub Error 22.

---

