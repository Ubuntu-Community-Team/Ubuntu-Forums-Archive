---
title: "Pure-FTPd Permissions"
date: 2009-07-04
forum: General Help
---

### Post by cpm30 on 2009-07-04
Alright, so I know that www-data needs to be the owner of /var/www. I'm using Pure-FTPd and I can successfully create a user and be able to read the contents of the /www/ folder. However, for some reason, I can not write or delete. 
 
My local user is "wwwuser" in the group "wwwgroup"
I set the home directory for wwwuser to be in /var/www/ and also added the user to be a member of the www-data group as well. 
 
The username I created in pureftp (webupload) links to the wwwuser. Like I said I still can't read or write. 
 
I was curious to see if there's a special command I need to give permissions to wwwuser for the www folder. Obviously if I set the owner to be wwwuser everything works, however no one can go to my website. (Forbidden).
 
Any suggestions?

---

