---
title: "External Drive Problems"
date: 2010-06-03
forum: General Help
---

### Post by ThanosIsKing on 2010-06-03
This is getting annoying. I have been using a memory stick to transfer character creations for 3D Dot Game Heroes from my computer to my PS3. It has been working fine up until now. Today I tried to clean up my stick, but it has decided that the entire system is "read-only file system". I found [this fix]("http://ubuntuforums.org/showpost.php?p=6714597&postcount=3"), but I can only get to step 2. I am completely baffled. First point of confusion: when I use the mount command, the console tells me that the stick is in fact re-writable, as all the files have (rw) next to them. Also, when I try to implement step 2 there, I get a message that /dev/sda1 is still busy, and thus can't be unmounted. The console does note that "useful processes that use the device [are] found by lsof(8) or fuser(1)." I have no idea what those two things are, or how to run them. Then moving to step 3 gives me a warning that "Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage."

What is going on with my memory stick, and how can I fix it?

---

