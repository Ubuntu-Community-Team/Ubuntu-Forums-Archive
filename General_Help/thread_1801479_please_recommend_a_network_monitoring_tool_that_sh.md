---
title: "please recommend a network monitoring tool that show what App is connecting"
date: 2011-07-10
forum: General Help
---

### Post by nrundy on 2011-07-10
Every network monitoring tool I install only displays IP addresses and port numbers but not what application is using the IPaddress or port.

Are there any network monitoring tools that show what Application on my computer is initiating the outbound internet connection?

---

### Post by Gyokuro on 2011-07-11
Try

**netstat -npl**

or **lsof** can be used too.

---

### Post by Habitual on 2011-07-11
```
sudo netstat -plant
``` 
last column.

---

