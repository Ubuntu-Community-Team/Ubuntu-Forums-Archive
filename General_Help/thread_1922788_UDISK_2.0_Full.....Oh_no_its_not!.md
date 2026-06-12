---
title: "UDISK 2.0 Full.....Oh no its not!"
date: 2012-02-09
forum: General Help
---

### Post by old_dog on 2012-02-09
I know I am going to feel foolish when someone tells me the answer...... My USB Stick has nothing, zero zilch on it, deleted everything. But I cannot copy to it. 128mb stick 2.6 Mb file.......Error message "No space on device". Basically how do I stop this foolish device believing it is full????? 

Go on tell me the command...........

Cheers

---

### Post by TeoBigusGeekus on 2012-02-09
Can you plug in the drive and post us the output of
```
df -Th
```
?

---

### Post by jerrrys on 2012-02-09
You could also fire up gparted and see whats going on.

Also did you select "show hidden files" and look for trash?

---

### Post by TeoBigusGeekus on 2012-02-09
> **jerrrys said:**
> You could also fire up gparted and see whats going on.

Also did you select "show hidden files" and look for trash?

+1
The .Trash folder could also be full.

---

### Post by old_dog on 2012-02-22
Just got back to it....Trash was the problem
Thanks guys
old_dog

---

