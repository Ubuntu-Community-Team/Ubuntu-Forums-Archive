---
title: "ext3 saved a 'corrupt' hard drive - how?"
date: 2010-09-27
forum: General Help
---

### Post by mendhak on 2010-09-27
I have an EEE netbook (16GB SSD) which had eeebuntu installed on it.  Recently, the OS kept failing to boot up, it would throw various errors which I don't remember, but which had to do with the hard drive.  It would force me to do a manual fsck, it would find a lot of corrupt blocks and at the end of this exercise, the OS would still not boot up, it was an endless cycle.  I just **happened** to have a USB stick with Linux Mint on it so I tried installing that, but still the same problems - fsck, corrupt sectors, can't start the OS.  I did this several times.

Then on a complete hunch, I went through the Mint installation again and this time, I looked at the file format - it was FAT.  So I changed it to EXT3 and did the install again.  This time, everything worked perfectly. No fsck, no corruptions reported, I tried rebooting about 30 times (really), but no problems were reported.  I can only deduce that ext3 has done something.

But what has it done? 

Bear in mind - at the time I did this, I was on a small island on vacation with no Internet access.  This 'problem' has been bugging me since then.

---

