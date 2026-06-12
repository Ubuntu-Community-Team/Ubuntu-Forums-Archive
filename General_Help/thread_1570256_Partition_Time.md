---
title: "Partition Time"
date: 2010-09-07
forum: General Help
---

### Post by skraskey on 2010-09-07
So I selected to install windows side by side with Ubuntu, but it has now been twenty minutes since it said it was resizing the partition and it is still at 0%. Is this normal? Should I do something about this?

---

### Post by oldfred on 2010-09-07
How big is hard drive. How much space are you creating.

It can take hours. Let it run overnite if you have to.

---

### Post by srs5694 on 2010-09-07
Furthermore, it is *extremely dangerous* to interrupt a filesystem resize operation! If it's completely crashed, of course, you may have no choice but to power off; but if it's currently running, even if it's taking an excruciatingly long time to finish, interrupting it mid-operation will most likely cause data corruption in the partition, which will result in the loss of most or all of the files on the partition.

---

