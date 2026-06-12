---
title: "change file/folder permissions"
date: 2009-11-03
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2009-11-03
/opt/lampp/htdocs
i would like give it the same permissions as the home folder has
i would rather not use 
gksu /opt/firefox/firefox 
just to use fireftp to have access to add/change files/folder in that location

---

### Post by Barriehie on 2009-11-03
**chmod** is the cli command to change file mode bits, you can also do this with Nautilus; select the folder > Properties > Permissions.  You may also have to change the owner, **chown**.

Barrie

---

### Post by pqwoerituytrueiwoq on 2009-11-03
thanks

---

