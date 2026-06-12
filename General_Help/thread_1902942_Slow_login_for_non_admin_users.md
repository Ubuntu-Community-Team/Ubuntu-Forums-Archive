---
title: "Slow login for non admin users"
date: 2012-01-01
forum: General Help
---

### Post by manishmk on 2012-01-01
Hi
Gnome login for my user with admin privs works fine. But all non admin(users with no root privs) users login is very slow. All actions- login, opening firefox or any other app is slow thereafter. No other user is logged in that time. Any help?
Thx

---

### Post by rsvancara on 2012-01-01
Are you using LDAP, NIS, or any other form of external authorization?  I have seen this problem you describe when PAM can not obtain the information it needs in a timely fashion, which gives the impression the system is slow.  

--
[Know Your Linux?]("http://www.knowyourlinux.com/")

---

### Post by manishmk on 2012-01-02
No NIS or any other form of complexity. I actually gave existing users all privs including admin, but they are still slow to login. Seems the issue is not limited to non-admin users. I tried creating a new user with admin privs, its also slow.
Any insight?
Thx

---

