---
title: "wget doen't work"
date: 2010-12-30
forum: General Help
---

### Post by Ali Kante on 2010-12-30
Hi,

when I try to use this:

```
wget ubuntu.com
```I get the following error:
```
Resolving www.myproxy... failed: Name or service not known.
wget: unable to resolve host address ´www.myproxy'
```But the actual name of my proxy is:
[www.myproxy.com:8080]("http://www.myproxy.com:8080")

Where does mget get's it's proxy variable? If I use "env | grep proxy" the settings are correct.

Any ideas?

---

### Post by hawkmage on 2010-12-30
Do you have a file in your home directory with the name ".wgetrc"?  If not do you have the file "/etc/wgetrc"?  Check them to see of there is a line defining your proxy

---

### Post by Ali Kante on 2011-01-01
Thank you and happy new year. I'll try it out on monday.

---

### Post by Ali Kante on 2011-01-03
Thanks again, it now seams to work after I removed all proxies and reconfigured them again in System>Preferences>Network Proxy! :p

---

