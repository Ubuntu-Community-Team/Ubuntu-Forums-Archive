---
title: "trying to grasp /var with permissions..."
date: 2010-05-25
forum: General Help
---

### Post by blackhawx on 2010-05-25
I have apache2, MySQL and PHP set up on my system.
Lets say I created a web site folder in my /var directory that was /var/mysite/ and lets say my user has "create and delete" file access but not my group, Is this is a safe/flexible method to follow, especially for building a dynamic php development sites on my localhost? 

Another developer advised me to log into the terminal as my username $USER (as upose to root), then go to that directory and manage my php files in /var/mysite?  Or is it better practice to store all my web developing content files in the /var/www/ directory?

Should ownership of the /var folder be the root user? or my user?

Thanks

---

### Post by blackhawx on 2010-05-26
I got it worked out - don't tamper with root permissions and set user access only on files and folders i'm working on.

---

