---
title: "make umask stick to directory"
date: 2006-03-07
forum: General Help
---

### Post by fobster on 2006-03-07
i am trying to umask the /var/www directory,  i change it to 002 and it changes back to 022.  In /etc/profile, umask is set to 022.  I dont know if i want to change this globally for everyone, just want /var/www set to 002 for certain users.  How would I do this?

thx

---

### Post by colo on 2006-03-07
You can't set a umask based on your CWD, just per-shell.

With some hacking in /etc/profile or each user's bashrc (an alias for "cd" sourcing a hidden file in each directory the issuer decends into comes to mind), there might be ways to do this, but they are not completely safe, I'd say.

Would you mind telling us what to acchieve? Maybe there are other, more elegant ways to fulfill your specific needs :)

---

### Post by fobster on 2006-03-07
Basically, i want anyone in group www-data to have write access to /var/www.  For example, if 'a' and 'b' are in group www-data.  If 'a' creates a file in /var/www 'b' will be able to edit it.

---

### Post by nebajoth on 2008-05-27
I want this same functionality.  Long overdue bump!

Anyone?

---

