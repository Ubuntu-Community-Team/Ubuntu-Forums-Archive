---
title: "zip issue"
date: 2012-10-04
forum: General Help
---

### Post by winzip on 2012-10-04
I want to **exclude **a specific  file  **abc.xml**   during   zipping . How to do it ?

I tried  this ...but this  does not work

zip -r /home/user/app.zip ./*  -exclude abc.xml

---

### Post by drmrgd on 2012-10-04
The exclude option needs two hyphens.  Also, you could just use -x:

```
zip -r /home/user/app.zip ./* -x abc.xml
```

---

