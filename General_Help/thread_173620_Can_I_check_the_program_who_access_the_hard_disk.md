---
title: "Can I check the program who access the hard disk?"
date: 2006-05-10
forum: General Help
---

### Post by piggyaugu on 2006-05-10
I always find my system is dragged by intense access to HD. But I cannot find out which program does that. Is there a tool like "top" where I can find out who's accessing the HD?:confused:

---

### Post by cyracks on 2006-05-10
to see which files are accessing /home directory:

$lsof -n|grep /home

---

