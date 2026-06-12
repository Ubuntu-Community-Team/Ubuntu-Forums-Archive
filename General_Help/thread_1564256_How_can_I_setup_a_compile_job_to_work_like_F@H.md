---
title: "How can I setup a compile job to work like F@H?"
date: 2010-08-30
forum: General Help
---

### Post by dragos240 on 2010-08-30
Hi,

I sometimes do heavy compile jobs, which may take a while. Now I don't like leaving my computer idle just because I'm compiling something. Folding@Home adjusts it's CPU usage if your using another application, so I can run firefox and do whatever I want while running F@H. How can I do this with compile jobs? Is it possible?

---

### Post by lloyd_b on 2010-08-30
> **dragos240 said:**
> Hi,

I sometimes do heavy compile jobs, which may take a while. Now I don't like leaving my computer idle just because I'm compiling something. Folding@Home adjusts it's CPU usage if your using another application, so I can run firefox and do whatever I want while running F@H. How can I do this with compile jobs? Is it possible?

The simplest way is to use the 'nice' command along with 'make':```
nice -n 19 make 
``` will run the make with a 'nice' value of 19, which means it will only get CPU time if there is nothing else asking for it.  This will keep all other programs responsive (but the compile will, or course, take much longer than running it with standard priority).

Lloyd B.

---

### Post by dragos240 on 2010-08-30
Thank you very much. I will need to remember this.

---

