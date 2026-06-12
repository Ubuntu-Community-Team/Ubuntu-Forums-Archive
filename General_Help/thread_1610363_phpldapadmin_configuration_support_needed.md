---
title: "phpldapadmin configuration support needed"
date: 2010-10-31
forum: General Help
---

### Post by natomb on 2010-10-31
Hello together,


I am fighting with phpldapadmin since a couple of days and cannot get it working correctly. I can connect to the LDAP server, login and browse the directory. I was even able to create a new user group, however, I had to add the ldap server administrator as the first group member.

Yet, I have two obstacles that I cannot overcome even after several days of research:

(1) when I try to create a new user group, I must add an existing user account. However, there might be times when a new group is created while there are no users for this group do exist. How can I overcome this?

(2) when I try to create a new user, I get the following error message:

```
Template Value Error: This template uses a selection list for [gidNumber], however the selection list is empty.
```

I followed the official Ubuntu tutorial for setup of my LDAP - with modifications to domain name, password, etc.


Any support is highly appreciated, because I try to fix this problem since over a week now.


Kindest regards
  Bjoern

---

### Post by natomb on 2011-02-27
I am no more use phpldapadmin but instead use Apache Directory Studio and ldapscripts.

---

