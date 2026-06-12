---
title: "Print Management Software"
date: 2009-08-17
forum: General Help
---

### Post by namdung on 2009-08-17
Is there any FOSS Print Management application for centralised Print Manager and Print Monitor? So far I'm only able to find proprietary versions like Print Manager Plus, PaperCut etc which runs on Windows.
My main requirement is to monitor printing and implement a quota system based on LDAP authentication.

---

### Post by namdung on 2009-08-18
Anybody???

---

### Post by dmizer on 2009-08-18
I'm not sure what you mean ... is System > Administration > Printing insufficient?

If so, have you tried [noparse]http://your-computer-ip:631[/noparse]

---

### Post by namdung on 2009-08-18
> **dmizer said:**
> I'm not sure what you mean ... is System > Administration > Printing insufficient?

If so, have you tried [noparse]http://your-computer-ip:631[/noparse]

My requirement is a Print Management Software which keep tracks and monitor all the printers in my office. User would be authenticated with LDAP and quota would be applied to control printing.

Proprietary solution for Windows : [Print Manager Plus]("http://www.softwareshelf.com/products/print_manager_plus_enterprise.htm")

I'm looking for a FOSS alternative.

---

### Post by dmizer on 2009-08-18
I think most of that can be done via cups with the exception of ldap.

Edit:
Cups does support kerberos auth.

---

