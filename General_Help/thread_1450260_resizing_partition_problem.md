---
title: "resizing partition problem"
date: 2010-04-08
forum: General Help
---

### Post by brunoguerios on 2010-04-08
Hey guys...
I was resizing my windows partition with the liveCD and then I figured out that the size I chose was smaller than the size I wanted....
I have important files that I can't lose, so I tried to stop the resizing....
The only way I could stop was pushing the power button....  :(  but now when I try to boot the laptop, just appears:

"
error: no such partition
grub recover>
" 

did I lose all my partition??

please someone help me!!!!

---

### Post by adam22 on 2010-04-08
You NEVER want to touch anything while the partitioner is active. The only way now to see if you lost the partition is to boot into the LiveCD and use GParted to see if it is still there. If it is, mount it, and BACKUP YOUR DATA! Always backup everything you might need!

---

### Post by lovinglinux on 2010-04-08
Really bad move unplugging the machine. I hope you can recover your data.

---

### Post by Mark Phelps on 2010-04-09
> **brunoguerios said:**
>  did I lose all my partition??

Quite possibly, yes.  While you probably did not actually lose the data, what most likely happened is that the partition table(s) got trashed -- which is, to the OS, effectively the same thing.

Unless you made a record of your exact partition types, locations, and sizes, it's unlikely that you'll be able to recover them intact.

About all you can do at this point is boot from a LiveCD and use utilities to copy your data files onto an external drive.

---

