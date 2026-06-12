---
title: "Network bandwidth."
date: 2006-06-07
forum: General Help
---

### Post by denisesballs on 2006-06-07
Ever since upgrading to Dapper stable and NetworkManager I've noticed everytime I download something, it COMPLETELY hogs all my bandwidth. Any streaming radio I'm listening to dies until the download is finished and other ocmputers on my network are dog slow too. Is there a way to put a cap on how fast a process can download? Also, is anyone else noticing this, or should I check my router and switch?

---

### Post by Ivan Matveich on 2006-06-08
"wget" has a rate limiting feature. You could set up per-user (or by port, whatever) aggregate rate limiting with "iptables" and "tc" if you are feeling masochistic.

---

