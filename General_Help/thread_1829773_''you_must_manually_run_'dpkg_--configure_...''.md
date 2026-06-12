---
title: "''you must manually run 'dpkg --configure ...''"
date: 2011-08-20
forum: General Help
---

### Post by dp7 on 2011-08-20
Hi Guys,

Need help.  While installing / uninstalling I get this message:

p, li { white-space: pre-wrap; }  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 



But the terminal does not recognise 'dpkg --configure -a' x


Am new to linux. 



Thanks in advance.


dp7

---

### Post by nothingspecial on 2011-08-20
Try it with sudo

```
sudo dpkg --configure -a
```

You will have to type your password which you will not see.

---

### Post by dp7 on 2011-08-22
thank you

---

