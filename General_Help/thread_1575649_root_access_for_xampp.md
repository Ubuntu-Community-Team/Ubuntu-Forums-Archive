---
title: "root access for xampp"
date: 2010-09-16
forum: General Help
---

### Post by natefons on 2010-09-16
i installed xampp using a tutorial posted here, but now the issue is i dont have priviledge to that directory.

currently the xampp folder is located in 
/opt/

and i cant seem to fig out how i can get privil to that folder.

(my user is "nate" not root)


how can i allow myself to access to this folder?
thanks
-Nate

---

### Post by gandaran on 2010-09-16
open root nautilus window, type in terminal
```
gksu nautilus
```

---

### Post by 5ky on 2011-07-05
Alternatively you can run the  following code in terminal.

sudo chmod 777 -R /opt/lampp/htdocs/

This will change the ownership of the htdocs folder to your user, the -R  option  makes it recursive for all folders and  files  inside htdocs.

In most cases, /htdocs/ is really the only folder you'll need full user access to when you use xampp. I believe it's a good idea to not change the permissions of the /opt/ folder itself.

---

### Post by Stagleton on 2011-10-12
w00t, thanks that worked for me

---

### Post by Stagleton on 2011-10-12
after I did this, now xampp asks for username and password to access xamp start which it did not before. any ideas?

---

### Post by Stagleton on 2011-10-12
.....1 hour later, just after this first post, I tried lampp for username and no password. it worked...


geez louis!

---

