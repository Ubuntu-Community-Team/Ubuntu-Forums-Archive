---
title: "Difference between System&gt;Authorisations and System&gt;Users and groups"
date: 2009-07-20
forum: General Help
---

### Post by Andy06 on 2009-07-20
What is the difference? Even in Users and Groups, you can goto System>Users and Groups>Properties>User priveliges and grant/deny admin privileges. However, they don't seem to work or have any relevance at all. I can do things which are not ticked and sometimes have to get root access to do things that are indeed ticked. So does the users and groups privilege granting mechanism actually work?

Thanks

---

### Post by komputes on 2009-07-20
The difference is that System>Authorizations manages policies having to do with different applications and components while System>Users and Groups is used to restrict access to specific hardware or network resources.

If you are getting unexpected behavior using Authorizations, that should be reported as a bug on bugs.launchpad.net

---

