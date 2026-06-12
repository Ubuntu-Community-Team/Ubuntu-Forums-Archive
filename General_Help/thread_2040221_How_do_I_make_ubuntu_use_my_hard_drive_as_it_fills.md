---
title: "How do I make ubuntu use my hard drive as it fills up?"
date: 2012-08-10
forum: General Help
---

### Post by barefoot138 on 2012-08-10
I want to make ubuntu be like windows in the way that it uses the hard drive as it fills up instead of just using as much memory as was set during the installation. What I mean is that instead of me running out of memory when the hard drive still has memory left, that I only run out of memory when the hard drive does. So how can I do that?:confused::confused::confused:  I want to do this so that first, I can make ubuntu run better. Second, I want it to not run out of memory, at least until my large hard drive does. Please help!!! :):):) I believe I can do this through installing without using another OS to install it, so that it has it's own folder instead of one inside the windows installation partition.

---

### Post by Cheesemill on 2012-08-10
Ubuntu and Windows **are** exactly the same in this respect, they use whatever space is available in the partition(s) they were installed into.

How did you install Ubuntu? By itself, with Wubi or as a traditional dual boot?

---

### Post by Vaphell on 2012-08-10
systems live in hardcoded partitions. Windows doesn't run out of space because usually it has access to all disk space (because the space is contained in NTFS partitions spanning the whole disk)
When you create a partition for linux you carve some space for it and that's all it's allowed to use by default. If you want to have access to other partitions you need to mount them in linux so the system can see and access them.

as for mentioned Wubi installation. It can outgrow initial size because the system storage is just a big file in windows environment and partition rigidity doesn't apply here (of course the file can't outgrow the parent windows partition it lives in).

---

