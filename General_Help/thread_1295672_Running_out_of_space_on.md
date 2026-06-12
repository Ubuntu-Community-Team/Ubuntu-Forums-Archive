---
title: "Running out of space on /"
date: 2009-10-19
forum: General Help
---

### Post by ExpressTrain on 2009-10-19
I'm running out of space on my root partition (/).  I have another partition after it with some space, but before I go resizing things and losing a bunch of data, I wanted to see if there was a better solution.  Here is the output of fdisk (edited for relevance)

```
%fdisk -l
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       12512    39062047+  83  Linux
/dev/sda3           12513       91201   632069392+   5  Extended
/dev/sda5           90716       91201     3903795   82  Linux swap / Solaris
/dev/sda6           12513       90714   628157502   83  Linux
```

There is lots of space in the sda6 partition, and it is immediately adjacent to the partition that is running out of space (sda2).  So I thought maybe I could reduce the size of sda6, and enlarge sda2.  But my guess is that shrinking the size of sda6 would mean shrinking it from the end (so it would still start at address 12513).  Can anyone confirm?:confused:

---

### Post by mechro on 2009-10-19
3 is extended containing 5 so ...

Shrink & move 6
Shrink & move 5
Shrink & move 3
Enlarge 2

What is in 6?

---

### Post by mechro on 2009-10-19
> **mechro said:**
> 3 is extended containing 5 so ...

Shrink & move 6
Shrink & move 5
Shrink & move 3
Enlarge 2

What is in 6?

Maybe not quite correct, but do you get the idea?

---

### Post by ExpressTrain on 2009-10-19
Thanks Mechro,

6 contains my user account areas, but only one contains a significant amount of data, and that's the mythtv account.  There's about 400GB of TV recordings in there.  I didn't realize that moving a partition was possible.  I'll have to go do my self-education, and post back on this thread my plans when I have a better understanding.

---

### Post by mechro on 2009-10-19
I'm not much of a command liner so anything I recommend will usually be GUI based.

Have you checked out Gparted? In Ubuntu it's in System > Administration > Partition Editor.

---

