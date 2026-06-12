---
title: "hi"
date: 2010-11-15
forum: General Help
---

### Post by raviraj on 2010-11-15
hi
i am new to the linux, i installed linux o/s by using vm ware could any one plz  help me 
what to do to sort this problem
useradd:cannot lock /etc/passwd; try again later

---

### Post by x1a4 on 2010-11-16
Hi, welcome to the forums.

This is very similar to [bug 432964]("https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/432964"). Check that there's a file called /etc/gshadow.lock, and possibly /etc/shadow.lock, /etc/passwd.lock too; if that's the case, remove them (no risk), and retry.

P.S. In future please use a more descriptive subject.

---

