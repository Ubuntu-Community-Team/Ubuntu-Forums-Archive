---
title: "How to save changes in .conf files"
date: 2010-04-26
forum: General Help
---

### Post by velbon on 2010-04-26
Hi all,
 
i am currently working on ldap server configuration and i had made changes on smb.conf file but i don't know how to save these change. please can someone help me.
i am using ubuntu 9.10
 
Regards,
Gerald

---

### Post by polki@mac.com on 2010-04-27
I'm assuming you're using nano to edit the file here:

sudo nano /path/to/file.conf

Use your own password (it won't show) and press enter.

If you're using gedid, start by pressing alt + f2. In the square the pops up, type:

gksu gedit /path/to/file.conf

Enter your password and configure away! :-)

---

