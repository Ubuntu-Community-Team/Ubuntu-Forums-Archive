---
title: "Samba - Ignore case"
date: 2009-11-03
forum: General Help
---

### Post by xzased on 2009-11-03
Hi guys. I need help with my samba setup. I was wondering if there is an option to make it case insensitive when reading files and directories. I tried looking it up but havent found anything yet. Any help is appreciated.

---

### Post by xzased on 2009-11-03
Just to describe the problem. We have a couple of windows machines writing to a samba share. Sometimes the users copy a directory named test as Test. I would like to know if its possible for samba to ignore the capital letter.

---

### Post by cesarbrod on 2010-01-04
I am having the same problem here and I wonder if you have found a solution...

Thanks!

---

### Post by bodhi.zazen on 2010-01-04
See : [http://oreilly.com/catalog/samba/chapter/book/ch05_04.html](http://oreilly.com/catalog/samba/chapter/book/ch05_04.html)

If this does not help, can you post the relevant section of your /etc/samba/smb.conf

---

