---
title: "Hi, guy do you know how to conf apache server when is not in etc directory"
date: 2009-08-05
forum: General Help
---

### Post by roquin on 2009-08-05
Hi, guy do you know how to conf apache server when is not in etc directory. im trying hard to install apache but it allway go to  usr directory. does some body knows how to fix this problem? thanks

---

### Post by Cheesemill on 2009-08-05
How are you installing Apache? If you just do:
```
 
sudo apt-get install apache2

```it will install everything in the correct directories.

---

### Post by louieb on 2009-08-05
/etc is for configuration files. 

/usr/sbin is the normal install location for apache  
an alternate would be to install in /opt (Xampp would install it there) 

Just kind of confusing at first - what goes where. this may help. [Filesystem Hierarchy Standard]("http://www.pathname.com/fhs/pub/fhs-2.3.html")

---

