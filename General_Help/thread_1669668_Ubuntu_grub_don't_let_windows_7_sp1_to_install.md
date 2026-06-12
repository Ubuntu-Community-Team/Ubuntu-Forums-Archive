---
title: "Ubuntu grub don't let windows 7 sp1 to install"
date: 2011-01-18
forum: General Help
---

### Post by aviramof on 2011-01-18
I have recently downloaded the leaked windows 7 sp1 RTM version and got an error
0x800f0a12 and now in this thread in the final reply i got the reason why.
 
[http://social.technet.microsoft.com/Forums/en/w7itproSP/thread/9083e953-f06c-4041-8977-115235359e23](http://social.technet.microsoft.com/Forums/en/w7itproSP/thread/9083e953-f06c-4041-8977-115235359e23)
 
i tried to find a way to file a bug report at launchpad but since i'm not in ubuntu now and for the time being i have removed grub so i can't find a way to do it properly 
so if any one eles can do it it would be great and thanks in advance.

---

### Post by s.fox on 2011-01-18
> **aviramof said:**
> I have recently downloaded the leaked windows 7 sp1

This forum does not support piracy.

Thread Closed.

**Edit**:

I have obtained second opinions from other staff.  The consensus is:

1 - It is a pre-release of a sp and is not piracy as the updates are free.

2 - The issue does appear to be with the pre-release version of the SP, not grub.

3 - It is advisable that  you seek help on windows support forums.

4-  The thread can be unlocked.

---

### Post by aviramof on 2011-01-19
I have seeked helped on microsoft forums and it said not to use grub for now but if you say it's a problem with the SP then i will wait a while for the official release and 
then try to reinstall grub again in the hope that it would work better.:)

---

### Post by julio_cortez on 2011-02-24
Unfortunately, it doesn't. I confirm that the same error happens with the RTM :(

By the way, I solved by manually booting from sda (the HD Windows 7 is on), which happens to be a different one from the one that hosts GRUB (sdb).

If you have both GRUB and Windows 7 on the same HD, try following this discussion (the correct workaround will likely appear in there soon, if it already hasn't):
[http://social.answers.microsoft.com/Forums/en-US/vistawu/thread/a584d276-a773-4917-b947-134d5330b825](http://social.answers.microsoft.com/Forums/en-US/vistawu/thread/a584d276-a773-4917-b947-134d5330b825)

---

