---
title: "Open Files question"
date: 2009-09-02
forum: General Help
---

### Post by philcms1 on 2009-09-02
Hi all,

I am trying to understand the "lsof" command. I have a Java process (Weblogic server), that has a normal number of open files:

lsof -p 674 | wc -l
1200

Now a number of those files are opened and closed by the application:

java    674 foo  DEL    REG        8,1            562212 /tmp/_axis2/axis2930597630889754512rampart-1.4.mar

and they appear again as deleted:

java    674 foo  463r   REG        8,1     2796   562212 /tmp/_axis2/axis2930597630889754512rampart-1.4.mar (deleted)

My question is: why do they appear in the count of open files if they are deleted? Why do they still consume file handlers?

Thanks!

Phil

---

