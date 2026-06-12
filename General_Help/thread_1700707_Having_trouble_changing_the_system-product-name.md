---
title: "Having trouble changing the system-product-name"
date: 2011-03-05
forum: General Help
---

### Post by budaslap on 2011-03-05
When I installed 10.10 I didn't put a value in the box that by default said System-Product-Name, and now I'm stuck seeing this every time I log on or elevate privileges. Is there any way to change this?

Thanks

---

### Post by budaslap on 2011-03-06
Is there no way to fix this?

---

### Post by leef on 2011-03-09
I know that this is grave digging but I stumbled upon this thread while trying to sort this problem on google search so people are coming across this thread.

The solution is to edit /etc/hostname (I tested on my system as this is what I suspected it to be) you can change it to more or less anything you want but I would suggest not using special characters such as "#"," " or "~".. Basically use alpha-numeric chars and "_" or "-" for spaces.

I hope this helps someone :D.

---

