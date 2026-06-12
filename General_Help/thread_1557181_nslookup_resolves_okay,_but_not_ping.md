---
title: "nslookup resolves okay, but not ping?"
date: 2010-08-20
forum: General Help
---

### Post by lumix on 2010-08-20
Another linux mystery.  My resolv.conf has 192.168.199.15 and no domain information:

* >nslookup mail2.mydom.local #works fine
* >ping mail2.mydom.local #doesn't resolve

In fact no combination of domain suffixes ( or lack thereof) works with ping ( or any other networked app).

If I add "search mydom.local" to resolv.conf then:

* >ping mail2  #works fine

So what gives?  How is it that my dns server can return my internal addresses with no problem, but my actual dns client fails?

---

