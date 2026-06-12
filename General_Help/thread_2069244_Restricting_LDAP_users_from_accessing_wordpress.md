---
title: "Restricting LDAP users from accessing wordpress"
date: 2012-10-10
forum: General Help
---

### Post by Deepak A on 2012-10-10
I have one ladp server configured and I have added 10 users. I am using sample ldap login plugin for logging in to wordpress. What I am trying to do is, i need only 5 out of 10 users to login to the wordpress. Other 5 won't be having access to wordpress. How can I achieve this? thanks in advance..

---

### Post by Deepak A on 2012-10-11
Somebody please help me..

---

### Post by lykwydchykyn on 2012-10-11
I don't know which plugin you're using, and I can't say to have done this before, but the usual method is to add the five users who need access to an LDAP group, and then require group membership for login (this would be an option in the plugin, if it's possible).

---

