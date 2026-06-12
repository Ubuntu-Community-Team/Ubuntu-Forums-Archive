---
title: "ram allocation question"
date: 2011-08-08
forum: General Help
---

### Post by dan0804smith on 2011-08-08
i want to allocate some of my ram as video memory.  if my max ram allowed in my computer is lets say...2GB, then could i put 3GB of ram in there if i allocate 1GB?  because that way the computer would still be useing its max of 2gb and i would have some sick video memory

will this work?

---

### Post by jerrrys on 2011-08-08
on my box the video ram is controlled by BIOS.  where the min to max video ram to allocate is preset in steps.  check BIOS for options.

---

### Post by psusi on 2011-08-08
max means max, no more will be recognized.

---

### Post by dan0804smith on 2011-08-08
i understand that it will no longer be recognized as ram but is there any way the excess could be recognized as video memory?

---

### Post by psusi on 2011-08-09
video memory is ram, so no.

---

### Post by blind2314 on 2011-08-09
> **dan0804smith said:**
> i want to allocate some of my ram as video memory.  if my max ram allowed in my computer is lets say...2GB, then could i put 3GB of ram in there if i allocate 1GB?  because that way the computer would still be useing its max of 2gb and i would have some sick video memory

will this work?

Your "sick video memory" would also be held back by the number of stream processors your card has, as well as its core/shader clocks.

---

### Post by psusi on 2011-08-09
> **blind2314 said:**
> Your "sick video memory" would also be held back by the number of stream processors your card has, as well as its core/shader clocks.

Not to mention that system ram is not as fast as dedicated ( on card ) video ram, and access to it has to be shared with the cpu, making it even slower.

---

### Post by 3rdalbum on 2011-08-09
Your extra video memory would be so slow as to be useless. The graphics memory has to be close to the GPU because the GPU needs to fetch things from memory as each frame is being rendered. Graphics memory needs to be super-fast and always-ready. Having to go back to the motherboard controller and regular memory would be too slow. The point of graphics memory is so that the GPU doesn't have to suffer the slowdown of system RAM!

Besides, if your BIOS/chipset can only recognise 2 GiB of RAM, that's all it can actually address and work with. If it could deal with the extra 1 GiB there would be no reason not to pool it with the rest of the system memory.

---

