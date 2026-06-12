---
title: "How to grep from Nth line of the file"
date: 2009-07-29
forum: General Help
---

### Post by kodalisrikanth on 2009-07-29
Hi,

I want to grep from the nth line of the file. I read the manual, but grep can search the nth line not from nth line to the end.


Any help will be appreciated. 



Thanks,
Srikanth

---

### Post by kodalisrikanth on 2009-07-29
Any idea?

---

### Post by beren.olvar on 2009-07-29
you can use awk for that:

cat file | awk '{if(NR>=3) print}'

Of course, where 3 is the line number from where you want to print your file

cheers

---

### Post by dlmarti on 2009-07-29
tail -n +37 assm.txt | grep hello

Will start at the 37th line and grep for hello

do a "man tail" to get more info

---

### Post by kodalisrikanth on 2009-07-29
> **beren.olvar said:**
> you can use awk for that:

cat file | awk '{if(NR>=3) print}'

Of course, where 3 is the line number from where you want to print your file

cheers
Thank you very much .. it is working ...  :)

---

