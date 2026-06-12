---
title: "umount busy device"
date: 2010-06-24
forum: General Help
---

### Post by Ratzian on 2010-06-24
Hello. I have a problem with an external USB HDD Samsung StoryStation 1TB. I try to umount it and I get the error "One or more partitions are busy on /dev/sdb".

I have closed all processes that may use the disk but I suspect it's soething in the background. Can someone help me with this?

Sorry if the answer is very obvious, but it eludes me. I'm using Ubuntu 10.04.

Later edit: I've solved it. Sorry about wasting some of your time. You can delete this thread. Thank you.

---

### Post by prshah on 2010-06-24
> **Ratzian said:**
> I try to umount it and I get the error "One or more partitions are busy on /dev/sdb".
I have closed all processes that may use the disk but I suspect it's soething in the background. Can someone help me with this?

For others encountering this problem, try this: open a terminal (Applications-Accessories-Terminal) then give the command ```
lsof|grep sdb
``` to find out the process id using your sdb device.

You can then either close that application or terminate the process using kill.

lsof = list open files. You can also use this with sudo, which will list key processes, but this is not recommended for a variety of reasons.

---

