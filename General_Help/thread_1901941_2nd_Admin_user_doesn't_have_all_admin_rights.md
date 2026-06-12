---
title: "2nd Admin user doesn't have all admin rights"
date: 2011-12-29
forum: General Help
---

### Post by Onesimus on 2011-12-29
I have created a second administrative user but they don't appear to have all the administration rights as the first user.  In particular, looking at /etc/group they don't belong to all the necessary groups.

In the User Account settings there used to be away to add users to particular groups - that all seems to have disappeared in 11.10.

Is there an additional application that I need ?

---

### Post by galvatron408 on 2012-01-01
type 'sudo vi /etc/group'

do what you want and then save it. done.

---

### Post by Onesimus on 2012-01-06
> **galvatron408 said:**
> type 'sudo vi /etc/group'

do what you want and then save it. done.

Is this the only suggestion ?  What happened to the nice application that allowed editing the groups that a user belonged to ?  Will it come back with the next version ?

---

