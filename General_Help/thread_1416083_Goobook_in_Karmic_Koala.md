---
title: "Goobook in Karmic Koala?"
date: 2010-02-25
forum: General Help
---

### Post by chaanakya_chiraag on 2010-02-25
Hey guys!  I'm trying to get goobook to work in Karmic, but I can't get the correct dependencies/python modules installed.  I've installed python-gdata, which I thought was all I needed.  However, goobook still comes back with:
```
Traceback (most recent call last):
  File "/home/chiraag/scripts/goobook.py", line 37, in <module>
    from gdata.contacts.client import ContactsClient, ContactsQuery
ImportError: No module named client

```What should I install?  Thanks!

- Chiraag

---

### Post by chaanakya_chiraag on 2010-02-25
*Bump*

---

### Post by chaanakya_chiraag on 2010-02-26
Anyone??

---

### Post by zzart on 2010-03-03
hey

 Im having the same error msg :( did anyone find answer yet ?

--------
oki i ' ve found the answer .. in case somebody finds it helpful you need to uninstall the ubuntu repo gdata and install the one from [http://code.google.com/p/gdata-python-client/downloads/list](http://code.google.com/p/gdata-python-client/downloads/list)

---

### Post by chaanakya_chiraag on 2010-03-03
Thanks!  That got me past that error. Now, goobook is complaining that it can't log in!  I put the correct stuff in .netrc, so I'm not sure why it's not able to log in.  However, that's for a different thread :D  Marking thread solved :)
- Chiraag

---

