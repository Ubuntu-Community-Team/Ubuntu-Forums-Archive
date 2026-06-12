---
title: "where are the databases held by phpmyadmin?"
date: 2009-07-14
forum: General Help
---

### Post by kapi on 2009-07-14
Hi there,

I was trying to locate the databases made when I use phpmyadmin but am having some difficulty - does anyone know where phpmyadmin holds them?

Thanks

---

### Post by nikgare on 2009-07-14
/var/lib/mysql

---

### Post by kapi on 2009-07-14
Thanks, I knew I was in the right direction but just couldn't see it.

I opened one of the files up corresponding to a database I made but don't recognize any of the file extensions ( yeah I suppose I'm too used to Access and everything ending with .db).
 
Is the only I can manipulate the database via phpmyadmin or is there another way?

---

### Post by kogger on 2009-07-14
Pretty sure you can use the mysql shell (just run 'mysql' in a terminal), but that requires knowing the commands to do so.

---

