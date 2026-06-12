---
title: "X server / Vesa driver issue"
date: 2011-10-19
forum: General Help
---

### Post by jirradmg on 2011-10-19
Hello,

so i try to describe my problem : 

this ubuntu (8.10 intrepid) is a specific compiled installation , not a general overall release -

the problem we are having is that one of the applications running on X server (using Vesa driver) (it's not some kind of application that would really be complicated , i mean pretty simple app - just gui that shows some data in simple few colored windows)
-after some time this application seems to use majority of CPU , then it crashes - in process list the app shows using about 16% of CPU , and X server about 70% - yet , when i use top to show , top shows 1-5% for both apps - i am confused about this mismatch , any little idea about where could be the problem ?

Thanks in advance for any ideas

JirraDmG

---

### Post by duke.tim on 2011-10-24
The top command is likely inaccurate, don't trust it's output.

---

