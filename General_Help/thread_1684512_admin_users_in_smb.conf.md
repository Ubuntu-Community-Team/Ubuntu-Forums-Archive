---
title: "admin users in smb.conf"
date: 2011-02-09
forum: General Help
---

### Post by zzitdegc on 2011-02-09
Hello,
   I'm trying to create folder share in samba with permissions that will only allow 2 of our users rwx permissions with everyone else r+x. If I were to edit the smb.conf file and add those to users as admin what is the best way to do that? example: 

admin user = domain+"user1"
admin user = domain+"user2"

or is should I add them to the same line some how.

Any suggestions would be appreciated, thanks.

---

### Post by garpenholm on 2011-12-13
I just added them separated with a comma, and it worked fine for me.

e.g; 

admin user = user1, user2

---

