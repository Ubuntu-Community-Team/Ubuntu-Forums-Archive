---
title: "Permiissions to edit conf file"
date: 2009-06-30
forum: General Help
---

### Post by babbar.ankit on 2009-06-30
To enable TCP/IP I have to uncomment the line in the directory 
/etc/postgresql/8.3/main/postgresql.conf 
#listen_addresses = 'localhost'

but when i do save the file after uncommenting it say u don't have permissions to do that help urgent!

---

### Post by Soul-Sing on 2009-06-30
via ```
gksudo nautilus
``` you navigate via nautilus to that file with permission to edit it.

---

