---
title: "Password Protecting LAMP Directory?"
date: 2010-05-20
forum: General Help
---

### Post by elbrian on 2010-05-20
I have a LAMP box which runs on Ubuntu 8.10 on it.

I am looking to password protect the web directory, so when a visitor accesses any site within they are prompted for a username/password.

Is there a package available that can help me with this?

Any advice would be greatly appreciated.

Also, please keep in mind that I am far from a Linux pro.

Thanks!

---

### Post by bodhi.zazen on 2010-05-20
You can do this in many ways.

If you have adminstrative access to the server config file, put it in the the < Directory >

Otherwise use .htaccess (this is slower).

See the bottom of this long post for details and references


[http://ubuntuforums.org/showpost.php?p=9265566&postcount=3](http://ubuntuforums.org/showpost.php?p=9265566&postcount=3)

---

