---
title: "Samba path through windows....."
date: 2011-01-10
forum: General Help
---

### Post by abhilashm86 on 2011-01-10
I've installed samba in ubuntu 10.04, then i'm able to access through windows7 by 'map network drive' and my workgroup name is WORKGROUP.

How to access files from windows7 without mentioning ip address from map network drive??

Now i'm doing the following,
\\192.XXX.X.X\foldername . 

I don't want to use ip address of the machine, but the workgroup name.

---

### Post by pricetech on 2011-01-10
Workgroup name won't work.  You'll need to use a machine name instead.

---

### Post by taseedorf on 2011-01-10
And you will need a WINS server running to map domain names to IP addresses

---

