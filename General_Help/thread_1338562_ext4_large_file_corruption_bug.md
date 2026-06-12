---
title: "ext4 large file corruption bug"
date: 2009-11-26
forum: General Help
---

### Post by crash_90 on 2009-11-26
I heard a little bit about the large file corruption bug with ext4 in 9.10.  I was wondering if this is still an issue or not.

Thanks in advance,

Crash_90

---

### Post by soni1770 on 2009-11-26
i heard about it to, was a bit worried but...

so far no corruption at all, and i've got 100's of gb of large files.

only issue i can see is sometimes when moving files around the filesystem then closing the folder and reopen the folder they where moved to, they don't show up in the gui,

however by use of the terminal i can see they are still there and after a shut down or restart
there is no more problem,

so just a small issue, not really a deal breaker..

---

### Post by The Cog on 2009-11-26
Oh, yes! Wait until you get a system crash. Like as not, you will have to reinstall. Of four crashes I've had while on ext4, I've had one with no noticeable loss, one with a couple of GB disappeared, one that would only boot into busybox, and one where GRUB complained "invalid extent". 

Oddly, after reverting these machines to jfs or ext3 I haven't had another crash, so I suspect that ext4 is not only making an unholy mess when the system crashes, but might also be the cause of the crashes.

---

### Post by StuartN on 2009-11-26
> **crash_90 said:**
> I heard a little bit about the large file corruption bug with ext4 in 9.10.  I was wondering if this is still an issue or not.

You can select ext3 during installation if you want.

---

