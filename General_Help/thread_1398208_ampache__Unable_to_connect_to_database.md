---
title: "ampache : Unable to connect to database"
date: 2010-02-04
forum: General Help
---

### Post by subodh.rohilla on 2010-02-04
I am trying to install ampache on Ubuntu 9.10 but during installation , it asks for copying ampache.cfg.php file in the /config folder ( Step 2 ) and after copying file , at step 3 it gives error "Unable to connect to database".

But the mysql user name and password is ok and the database is successfully created in step 1. 

I am not able to figure out what is the exact problem , i have tried restarting apache and mysql . Please specify which step i am missing . 
Thanks

---

### Post by slag02 on 2010-02-04
I am trying to install ampache and having the exact same problem

any help is appreciated

---

### Post by sgb77 on 2010-02-04
I was having the same issue, but got it to work by running the configuration in a browser where ampache is being installed. In other words, do not use any other computer other then the one you are installing it on.

Anyhow, that worked for me, hope it solves yours as well.

---

### Post by slag02 on 2010-02-05
after a little rest i was able to get it

permissions on the ampache.cfg.php file were set wrong

chmod 755  took care of that

---

### Post by subodh.rohilla on 2010-02-15
Thanks , It was only the problem of permissions. Now , I have installe dit but i am not able to login in  it by using by username and password.

Well , i was using latest build of ampache , so I was having issues now it is working perfectly because now i am using repository version

---

