---
title: "How to obtain cache hit ratio?"
date: 2010-12-06
forum: General Help
---

### Post by yshoaib on 2010-12-06
Any ideas how we can obtain cache hit ratio?
I have tried using "sar -b" but couldn't find the info there.

Thanks.

---

### Post by bodhi.zazen on 2010-12-07
> **yshoaib said:**
> Any ideas how we can obtain cache hit ratio?
I have tried using "sar -b" but couldn't find the info there.

Thanks.

streamrecorder ?

---

### Post by yshoaib on 2010-12-07
Thanks. However, doesn't that relate to audio recording?

This is concerning CPU Cache.

---

### Post by bodhi.zazen on 2010-12-07
Oh, I guess I am not understanding what you want.

---

### Post by soldier1st on 2010-12-07
> **bodhi.zazen said:**
> Oh, I guess I am not understanding what you want.
i believe i understand what the op wants to know but i do not know the command but what he wants to know is the radio or % when ubuntu goes to use the cached data vs the non cached data.

---

### Post by owiknowi on 2010-12-07
Is this of any help to you?
[www.cse.iitk.ac.in/users/moona/students/Y3101.pdf/](www.cse.iitk.ac.in/users/moona/students/Y3101.pdf/)

It was of interest to me when working with CPU and memory consuming GIS applications.

---

### Post by yshoaib on 2010-12-07
Thanks. soldier1st is right.
owiknowi, yes the data is quite useful. They mention about using meminfo and vmstat. Although I couldn't find the exact info about the parameters to these commands and how the output can be utilized for this specific use. Will have to look into the 'man' of these commands.

---

### Post by bodhi.zazen on 2010-12-07
This may be of interest, sorry if it is not:

[http://distilledb.com/blog/archives/date/2009/02/22/swap-files-in-linux.page](http://distilledb.com/blog/archives/date/2009/02/22/swap-files-in-linux.page)

---

