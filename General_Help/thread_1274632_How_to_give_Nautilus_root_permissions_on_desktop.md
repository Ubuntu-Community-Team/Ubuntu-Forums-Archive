---
title: "How to give Nautilus root permissions on desktop?"
date: 2009-09-24
forum: General Help
---

### Post by DapperMe17 on 2009-09-24
Hi,

I'm trying to open Nautilus via terminal. I get the root(Desktop) folder permission. How can I add a root folder to desktop?

---

### Post by aysiu on 2009-09-24
> **DapperMe17 said:**
> Hi,

I'm trying to open Nautilus via terminal. I get the root(Desktop) folder permission. How can I add a root folder to desktop?
Paste in the command (for the launcher on your desktop or in the terminal): ```
gksudo nautilus
```

---

### Post by DapperMe17 on 2009-09-24
I tried that, however received the dame error box...

Nautilus could not create "root/Desktop"

---

### Post by aysiu on 2009-09-24
Not sure what the problem is. How about pasting in these commands? ```
sudo chown -R root:root /root
sudo mkdir -p /root/Desktop
gksudo nautilus
```

---

### Post by DapperMe17 on 2009-09-24
1. Worked fine
2. Says file already exists
3. Same nautilus error.


?

---

### Post by DapperMe17 on 2009-09-24
Thanks...I solved it. 

I wiped the /root/Desktop folder via terminal, the I ran your series of commands & Viola!!!

Thanks for your time!

---

### Post by &#1580;&#1608;&#1578;&#1740;&#1575;&#1585; on 2009-09-24
u can press ctrl+h when it show u Desktop to show hidden files too.






bjyn,

---

