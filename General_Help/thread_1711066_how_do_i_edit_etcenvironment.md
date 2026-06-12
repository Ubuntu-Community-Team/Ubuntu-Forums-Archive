---
title: "how do i edit /etc/environment?"
date: 2011-03-20
forum: General Help
---

### Post by ddmn on 2011-03-20
Hi,
I'm trying to add environment variable. i added the following line in /etc/environment:
```

ANT_HOME="/usr/local/ant"
``` and when i run the following i get nothing:
```
echo $ANT_HOME
```what may be wrong here?

---

### Post by abyrne on 2011-03-20
When you edited the file, you did so with root privileges, right? 
Also, did you reboot afterwards?

---

### Post by ddmn on 2011-03-20
> 
Also, did you reboot afterwards?Thanks. This solves my problem. i didn't reboot.:D

---

