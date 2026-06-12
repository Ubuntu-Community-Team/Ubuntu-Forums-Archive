---
title: "Reasons for compiling a custom kernel?"
date: 2010-08-02
forum: General Help
---

### Post by Buffy635 on 2010-08-02
An excerpt from the Ubuntu Kernel/Compile help wiki:

> 
**Reasons for compiling a custom kernel**
You are a kernel developer.
You need the kernel compiled in a special way, that the official kernel is not compiled in (for example, with some experimental feature enabled).
You are attempting to debug a problem in the stock Ubuntu kernel for which you have filed or will file a bug report.
You have hardware the stock Ubuntu kernel does not support.


I am not a kernel developer, I don't need the kernel compiled in a special way, I'm not debugging anything and I haven't had any problems running Ubuntu on my hardware. But, I'm curious about compiling the kernel with experimental features or potentially running it on odd hardware.

Unfortunately, I haven't found any really relevant documentation.

Can I streamline display drivers into the source so when I install they are already there? Could I incorporate a beta desktop environment(gnome shell) into the source and have them installed automatically?

If I knew more specifically what I wanted to do I would likely have move luck finding documentation. What modifications have you all done? Where can I go to learn more? What constitutes compiling the kernel in a special way?!

I'd appreciate any insight or thoughts the forum has.

Thanks.

**Update 8/8/2010**

bump

I've settled upon tailoring my kernel to my hardware. Curiosity I guess. While searching for methods I've come across this:

[http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/index.html](http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/index.html)

It's an online version of *Linux Kernel in a Nutshell*. I've read through the whole thing and found it very helpful, save for customization. Chapter 8, Customizing a Kernel, contains the method for discovering the modules used by a kernel. I also has a short script that lists the modules loaded for a running kernel. I'm confused because the two methods don't seem to correlate. 

The manual method works well for hardware and services I'm aware of. I, unfortunately, am not aware of all the hardware my machine uses. The script seems to show all modules used, but the results aren't easily found in *menuconfig*.

Is there an easier way of discovering all loaded modules? Or how can I find those listed by the find_all_modules.sh in *menuconfig*?

Any pointers the gurus may have I'd appreciate.

---

### Post by Linuxforall on 2010-08-02
WOW! Crapbuntu and you are at an Ubuntu forum.

---

### Post by dcstar on 2010-08-03
> **Buffy635 said:**
> 
..........
If I knew more specifically what I wanted to do I would likely have move luck finding documentation. What modifications have you all done? Where can I go to learn more? What constitutes compiling the kernel in a special way?!

I'd appreciate any insight or thoughts the forum has.


The only value I have ever had of compiling a custom kernel is switching off all the various hardware and software features that I know do not apply to my setup so the resultant kernel is massively smaller than the "standard" that has to support many things that are out there. A custom kernel will also load quicker because there is no need to probe for hardware that it knows does not exist.

After a few of these compilation cycles I quickly came the conclusion that is just wasn't worth the bother as disk space was hardly a concern and a slight decrease in booting time wasn't a big enough pay-off for having a non-standard kernel that caused problems with proprietary video drivers.

---

### Post by MCVenom on 2010-08-03
> **Linuxforall said:**
> WOW! Crapbuntu and you are at an Ubuntu forum.
Well, he is quite entitled to his opinion (within the CoC, of course) :D

---

### Post by worksofcraft on 2010-08-03
Ubuntu Studio is a derivative of Ubuntu that has a special real time kernel giving improved performance for multi media applications.

---

