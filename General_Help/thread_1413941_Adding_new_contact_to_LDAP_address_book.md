---
title: "Adding new contact to LDAP address book"
date: 2010-02-23
forum: General Help
---

### Post by borobudur on 2010-02-23
Hi, 
I have my own LDAP server with my address book on it. Everything work fine, also with Evolution. I can read and edit my contacts. 
One thing doesn't work: I can not add a new contact to the server through Evolution. Getting an Permission denied error. 
Has anyone an idea?
Thanks!

---

### Post by borobudur on 2010-02-23
Found it
```
send_ldap_result: err=50 matched="" text="no write access to parent"
```

---

