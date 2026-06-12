---
title: "Swap Not Used"
date: 2006-02-05
forum: General Help
---

### Post by Mau on 2006-02-05
I cannot get Kubuntu to use my swap memory.  I have 1 GB physical RAM, and so I set swap to 2 GB (or 1.86 GB I guess).  When I look at the memory usage, it's telling me that 100% of the swap space is free.  Of course, I'm only using 24% of the total memory, but shouldn't it be using the swap?

---

### Post by dickohead on 2006-02-05
No, the computer will use physical memory first, which of course is faster, it will then overflow into the swap file when your physical memory (RAM) has been used.

---

### Post by Ocxic on 2006-02-05
the swap space is virtual memory, that means when you run out of avalable ram linux will start using the swap space as ram. have your memory at 100% is normal, linux will mostly always allocate all of the ram to itself and then give out the required amount to whatever program/application may need it. I too have 1GB of ram, and i don't even have a swap partition, and everything still runs smooth. I got rid of it, scince i was tired of always seeing nothing being used, and scince i don't think I'll ever use all of my 1BG of ram, i decided to just get rid of it and use the space for meself

---

