---
title: "Files mysteriously disappear"
date: 2010-08-22
forum: General Help
---

### Post by kazinnud on 2010-08-22
Hi all,
 
I've had a couple of occasions where files mysteriously disappear from my HD.  The first instance was with a whole season of some TV--poof, gone all of a sudden one day.  Couldn't locate it, didn't show up anywhere with grep even.  Just gone.  This was a few weeks ago.  Then, today, a whole folder of music disappeared.  Can't find any trace of it, not in the trash, not with locate or grep...
 
Using Ubuntu 10.04, ext3.  I am worried that perhaps my HD itself is going bad--is there any way to check the integrity of the drive?  In any case, if some sectors or something went corrupt, I would think there would be a way to tell?  Fsck doesn't return any errors, in any case.
 
I am not quite sure what to say about this.  I understand the importance of backing up, but I feel a little weird about having to back up everything because stuff randomly disappears.  
 
Thanks in advance!

---

### Post by sikander3786 on 2010-08-22
Hi.

[https://help.ubuntu.com/community/TestingStorageMedia](https://help.ubuntu.com/community/TestingStorageMedia)

Might be some bad sectors on your drive causing the loss of data.

---

### Post by ranch hand on 2010-08-22
Those fsck commands should be of some help.

Do NOT run them from the drive you are testing on.  The safest way to do that is boot to your Live CD and do it from there.

---

