---
title: "multi-core processors?"
date: 2011-10-23
forum: General Help
---

### Post by cybergalvez on 2011-10-23
Hi all, 

I just put together a new computer with an AMD 6 core processor. My question is do i need to do anything for ubuntu to take advantage of all the cores? So far all I've done is install 11.10 64 Desktop.

Thanks in advance for the help

---

### Post by Gawains Green Knight on 2011-10-23
My quad core was happy enough. Try running htop to see whats going on on your processes.

---

### Post by hwttdz on 2011-10-23
Nope, it'll use anything it can get.  

Take a look at top.  It reports % of a single cpu in the % column, so if you have an application which is multithreaded you'll see it with more than 100% cpu.

---

### Post by cybergalvez on 2011-10-23
Cool thanks, for the info. I took a look and it seems to at least report all the processors, so I guess that's all I have to do

---

### Post by Bobhuber on 2011-10-23
> **cybergalvez said:**
> Cool thanks, for the info. I took a look and it seems to at least report all the processors, so I guess that's all I have to do
Hint - Be sure and enable AMD Cool and Quiet in the BIOS

---

