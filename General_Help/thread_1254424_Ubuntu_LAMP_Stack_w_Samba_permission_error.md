---
title: "Ubuntu LAMP Stack w/ Samba permission error"
date: 2009-08-31
forum: General Help
---

### Post by freshtealeaf on 2009-08-31
I changed the user/group of /var/www to www-data so I could run this script in PHP using the fopen() function. However, now I can't access my Samba shares through my windows clients, I can SEE them but I can't open them. Permission denied :( Anyone have a clue how to fix this?

I used chown -R www0data and chgrp -R www-data on /var/www

---

