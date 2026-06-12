---
title: "Question about how paging works"
date: 2010-11-24
forum: General Help
---

### Post by nolag on 2010-11-24
I am wondering (in linux and I guess for other os if it is the same), if I x number of pages and the ammount of total memory they take is less than the amount of RAM that I have will the OS keep those pages in memory, until there is a need for something else to be there or when a program is idle will it kick it out to the hard drive (swap if there is any)?
 
I think it would make sence to keep the pages in RAM until there is a usage more than the RAM you have since it would significantly speed it up, but I want to be sure if that is true, or why it is not true.

I think my error was the on at

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/677748](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/677748)

---

### Post by dcstar on 2010-11-25
> **nolag said:**
> I am wondering (in linux and I guess for other os if it is the same), if I x number of pages and the ammount of total memory they take is less than the amount of RAM that I have will the OS keep those pages in memory, until there is a need for something else to be there or when a program is idle will it kick it out to the hard drive (swap if there is any)?
.........

There are many explanations of how paging works available from a simple web search.

---

### Post by asmoore82 on 2010-11-25
In my experience, Linux will not use swap until is absolutely has to.
Some other OS's seem to use massive amounts of pagefile space for the fun of it.

---

