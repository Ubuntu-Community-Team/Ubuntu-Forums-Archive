---
title: "strange permissions problem"
date: 2009-09-21
forum: General Help
---

### Post by RuleMaker on 2009-09-21
Hi people, here I am with another "strange" permissions problem.
Take a look at the following:

```
rulemaker@desktop ~ $ whoami 
rulemaker
rulemaker@desktop ~ $ groups rulemaker 
rulemaker adm dialout cdrom www-data plugdev lpadmin admin sambashare
rulemaker@desktop ~ $ ls -l /var/www/index.html 
-rw-rwxr-- 1 www-data www-data 0 2009-09-21 19:47 /var/www/index.html
rulemaker@desktop ~ $ echo "test" > /var/www/index.html 
bash: /var/www/index.html: Permission denied
```

How come that I don't have permissions to write in that file when I am in www-data group?

Damn, I had to restart my PC and it solved the problem (it's probably because I've just added myself to that group).

---

### Post by schmidtbag on 2009-09-21
first, where did the group "www-data" come from?  secondly, typically groups don't grant you permissions to other programs, although sometimes that does happen.  but, in your case, you're using echo, a /bin command which is executable by all, and you're telling echo to write a file in /var, which is only accessible by root.  therefore, you should put a "sudo" in front of the command which will give you the right to do what you want

---

### Post by alphaniner on 2009-09-21
I think it may have something to do with redirection.  Have you tried editing the file with vi or something?

Edit: I made a file in a directory I own to test this, and I couldn't redirect but I could edit directly.  But schmidtbag is right, you will still need to use sudo due to the location of the file.

---

### Post by RuleMaker on 2009-09-21
People, thanks for your time but I have solved this.
I edited the first post but I will write it again in case it happens to somebody else.

I have freshly added myself to www-data group so I had to restart my PC (probably relogin would work too) in order to gain permissions.


Thanks again.

---

### Post by John Cheng on 2009-09-21
Glad to hear you solved it. As you suspected, a new login would take care of it.

FYI - the command "id -Gn" will show your currently active groups. When you add yourself to a new group, you may need to re-login for it to take affect, or you may use "newgrp www-data" to update your group settings without logging in again.

---

