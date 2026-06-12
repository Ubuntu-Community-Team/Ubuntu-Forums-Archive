---
title: "Any issues linking sh back to bash?"
date: 2011-01-04
forum: General Help
---

### Post by wds on 2011-01-04
What issues will I create for myself if I link /bin/sh back to bash?

---

### Post by bodhi.zazen on 2011-01-04
In general it should work. linking to bash is, IMO, a bit less secure and you may break a few scripts that are not written for bash.

---

### Post by wds on 2011-01-04
great, thank you

---

### Post by lithopsian on 2011-01-04
Yup, give it a try.  Most likely everything will work until you find some subtle thing you didn't even realise was using a shell commend ;)

---

