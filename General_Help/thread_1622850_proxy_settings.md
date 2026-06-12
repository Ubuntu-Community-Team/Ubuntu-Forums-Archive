---
title: "proxy settings"
date: 2010-11-16
forum: General Help
---

### Post by ub007 on 2010-11-16
Hi ALl,

 I use a proxy to connect to web, and from shell do a 
export http_proxy=XXXXXXXXXXXXXXXXXXXXX

But this is valid only on that shell, ie if I open a new terminal I cant connect to the internet from it. What is the best way to make these proxy settings persistant across all shells?

Thanks in advance

Cheers
Dave

---

### Post by dcstar on 2010-11-16
> **ub007 said:**
> Hi ALl,

 I use a proxy to connect to web, and from shell do a 
export http_proxy=XXXXXXXXXXXXXXXXXXXXX

But this is valid only on that shell, ie if I open a new terminal I cant connect to the internet from it. What is the best way to make these proxy settings persistant across all shells?

Thanks in advance

Cheers
Dave

Apart from System-Preferences-Network Proxy?

---

### Post by ub007 on 2010-11-16
from command line?

---

### Post by anglican on 2010-11-16
> **ub007 said:**
> Hi ALl,

 I use a proxy to connect to web, and from shell do a 
export http_proxy=XXXXXXXXXXXXXXXXXXXXX

But this is valid only on that shell, ie if I open a new terminal I cant connect to the internet from it. What is the best way to make these proxy settings persistant across all shells?

Thanks in advance

Cheers
DavePut the command into a file /etc/profile.d/proxy.sh.

H

---

