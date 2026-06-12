---
title: "So what should I trust?"
date: 2009-12-25
forum: General Help
---

### Post by zigNzag on 2009-12-25
Terminal 

total       used       free     shared    buffers     cached
Mem:       1016892     739356     277536          0      12608     489372

system monitor 

tells me my memory usage is only at 16%

---

### Post by chewearn on 2009-12-25
Technically both information are correct.  It's a matter of context.

The System Monitor is probably reporting the actual memory being used at the moment by processes, open applications, etc.  This would be somewhat the "traditional reporting" of free available memory.

The terminal "free" reports the memory allocation being performed in the Linux kernel.

Now, why is most of the memory being reported as used?  Think about it.  Any unused memory is wasted memory.  What the kernel does is to retain a substantial cache of previously accessed data; even though it might have already been freed by the processes or applications.

Therefore, future accesses to the same data do not have to go back to the harddisk, which is significantly slower.

You can see this effect thus: any application that you open the first time usually takes much longer to come up than subsequent times.

---

### Post by zigNzag on 2009-12-25
I thank you

---

