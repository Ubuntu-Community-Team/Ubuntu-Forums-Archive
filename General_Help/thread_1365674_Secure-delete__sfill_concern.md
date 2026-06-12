---
title: "Secure-delete / sfill concern"
date: 2009-12-27
forum: General Help
---

### Post by tgeer43 on 2009-12-27
Last night I installed secure-delete from the repos. Ran "sfill /" to wipe the freespace on my main partition (approx 76GB). Well, it's been limping along for 12+ hours now and I'm afraid to interrupt it with Ctrl-C because it's currently showing the partition as 100% used (it's actually less than half full).

Is this normal? What, if anything should I do? I'd like to have my computer back sometime today. :(

tgeer

---

### Post by dcstar on 2009-12-27
> **tgeer43 said:**
> Last night I installed secure-delete from the repos. Ran "sfill /" to wipe the freespace on my main partition (approx 76GB). Well, it's been limping along for 12+ hours now and I'm afraid to interrupt it with Ctrl-C because it's currently showing the partition as 100% used (it's actually less than half full).

Is this normal? What, if anything should I do? I'd like to have my computer back sometime today. :(

tgeer

Filling the root partition cripples any Linux system.

---

### Post by tgeer43 on 2009-12-27
> **dcstar said:**
> Filling the root partition cripples any Linux system.
Not sure what you're saying here, dcstar. I'm just trying to wipe the freespace on the root partition. I think that sfill does this by creating one large file of all the freespace which it overwrites repeatedly before marking it again as free space.

Since it's available in the repos and mentions nothing about _not_ using it on the root partition, it seemed like a fairly safe thing to do. And the system is not crippled in any way. It's still responding relatively well. I'd just like it to finish so it will mark my free space as free again and I can finally shut down the box.

BTW: In system monitor the sfill process shows a status of 'Uninterruptible'.

tgeer

---

### Post by tgeer43 on 2009-12-29
For those wanting to know:
Yes, you can safely interrupt sfill by hitting Ctrl-C. The program will exit cleanly and will mark the free space as unallocated once again.

Sfill defaults to overwriting the free space 38 times which is pretty ridiculous even if you're trying to wipe plans for building a clandestine biological warfare production facility, much less that gay midget porn you downloaded last week. :wink:

A more practical approach would be to use some combination of the -f, -l, and -z parameters to limit the number of passes to say, 5 or less.
By using: ```
sfill -lv /
``` I was able to securely wipe about 60GB of free space in just under an hour.

tgeer

---

