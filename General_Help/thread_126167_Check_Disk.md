---
title: "Check Disk?"
date: 2006-02-05
forum: General Help
---

### Post by Mau on 2006-02-05
Hi everyone,
So I was playing around with KLaptop.  I had enabled hibernate, suspend, and standby. I tried out each of them, and they each failed at different places.  Hibernate failed to restore my screen correctly; suspend messed up my BIOS temporarily; and standby failed to turn off.  Anyways, after having to manually reset my computer, Kubuntu came up and told me it was doing a forced disk check. I let it do its thing, and it said 1.1% something-here for my root partition.  It then told me that it failed on my /home partition, with 3.4%.  

It booted up fine, and I believe that most of my files are there.  What does this fail mean?  Should I run some disk repair utility?

---

### Post by stuporglue on 2006-02-05
It means "double check if everything is ok". Since your crashed were probably software induced rather than hardware induced, your disks are probalby alright.  If it were happening seemingly at random, then you could suspect the disks and think about getting your info off them quickly. 

To check the disks, boot from a live CD, open a terminal and run:

# sudo fsck.FILESYSTEMTYPE /dev/DEVICELOCATION

For example, if my main partition (root, /) were at /dev/hda1 and it's in ext3 format, I'd run:
sudo fsck.ext3 /dev/hda1

Anything it finds out of place it throws in lost+found at the top level of the partition (ie. not in a sub-folder).  You can check in there for files and see if it recovered anything to there.

---

### Post by Mau on 2006-02-05
Everything seems fine - I just a little worried that it told me that it "failed."

---

### Post by 5-HT on 2006-02-06
Hi, I've had a few crashes here and there related to what seems to be my video card.

When Ubuntu does its forced disk check every 30 mounts, I've noticed that one partition always comes up with "FAILED" instead of the usual "OK".

Originally I was worried, so I booted a live CD and did a whole slew of tests from fsck as well as for bad sectors, etc...

Well everything checked up ok.

I even reformatted that partition and put everything back on, and sure enough at the next forced check it failed again.

So, while I'm not sure why it was saying "FAILED"...it seems to be a false-positive I assume (seems like the default forced check only checks the journal, not the complete filesystem).

I have read posts where people encountered messages on boot saying something like "Disc errors were found, please run fsck manually...", so I'm guessing that is something to be concerned about and verify with fsck.

Overall, it seems wise to always double-check manually yourself to make sure as data integrity is a great concern.

Always becareful not to run fsck on a mounted filesystem though (well, read-only is ok... but unmounted would be better).

---

