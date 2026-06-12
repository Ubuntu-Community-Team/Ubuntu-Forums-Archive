---
title: "DB2 Express-C edition on 9.04?"
date: 2009-09-09
forum: General Help
---

### Post by echo9 on 2009-09-09
hi!

i want  to install ibm's DB2 express-C edition on my ubuntu 9.04

anybody knows how should i go for it??

should i install it from its *.deb package or through a tar ?

---

### Post by zenandruby on 2009-09-09
Hi echo9,

you can download DB2 Express-C 9.7, a free version of DB2, from [here]("http://www.ibm.com/software/data/db2/express/download.html?S_CMP=ECDDWW01&S_TACT=ACDB201").

Once you've downloaded the file, you can install it as follows:

```
$ tar xvfz db2exc_970_LNX_x86.tar.gz
$ cd expc/
$ sudo ./db2setup
```

Please do not hesitate to ask if you encounter any issues.

Cheers,
Antonio

DB2 Technical Evangelist
IBM Toronto Lab

---

### Post by guneet25 on 2009-09-26
ubuntu rocks...
i am a newbie...and i hv installed db2 using the above coomands and also created users..
but i am not able to run the control center..
plz help me with it....
cheers..!!:KS

---

### Post by echo9 on 2009-10-04
> **guneet25 said:**
> ubuntu rocks...
i am a newbie...and i hv installed db2 using the above coomands and also created users..
but i am not able to run the control center..
plz help me with it....
cheers..!!:KS
try running db2cc from console.
go to console and type this command:  db2cc

see if that works..

---

