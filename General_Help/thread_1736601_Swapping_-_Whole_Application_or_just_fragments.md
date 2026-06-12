---
title: "Swapping - Whole Application or just fragments?"
date: 2011-04-22
forum: General Help
---

### Post by Wint3rmute on 2011-04-22
Hi All,

My question relates to the swapping mechanism in Ubuntu (more generally about it in Linux). Does it swap the entire application in and out of swap space, or just the parts that aren't being actively used?

The context that I'm asking this in is running a Minecraft server- I know they can tend to use intense amounts of RAM in a single application, but parts of it aren't (areas of the world) aren't touched often at all, and I feel it would be beneficial (by setting swapiness high) to swap it aggressively.

---

### Post by Wint3rmute on 2011-04-22
I did find 

"The main advantage of paging is that it allows the physical address space of a process to be noncontiguous. "

On Wiki, which would suggest that it does... although I'm not certain this is implemented.

---

### Post by 3Miro on 2011-04-22
Only pages are swapped in and out. Every application has several pages, thus only parts of the application are swapped. I think it would be a very rare thing for an entire app to get swapped.

---

