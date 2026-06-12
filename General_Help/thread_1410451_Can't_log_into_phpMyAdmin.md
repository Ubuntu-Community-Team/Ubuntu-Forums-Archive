---
title: "Can't log into phpMyAdmin"
date: 2010-02-18
forum: General Help
---

### Post by Hovercat on 2010-02-18
I'm trying to log into phpMyAdmin, but when I go to the page, I type in my username and password, click Go, and then the page refreshes with no error message...

Please help...

---

### Post by n0dix on 2010-02-18
What tutorial do you use to install phpmyadmin?

---

### Post by Hovercat on 2010-02-18
Uhm, I don't remember. I don't think I used a tutorial.

---

### Post by pirateghost on 2010-02-18
if its the first time you have set up mysql and have not set up another user, you will need to log into it as root

---

### Post by n0dix on 2010-02-18
Do you set the blowfish_secret.inc file?
See this guide: [https://help.ubuntu.com/community/ApacheMySQLPHP#Phpmyadmin and mysql-admin](https://help.ubuntu.com/community/ApacheMySQLPHP#Phpmyadmin and mysql-admin)

---

### Post by Hovercat on 2010-02-18
No, I'll look at that guide now.

---

### Post by RileyLynx on 2011-06-14
I just had this issue,

Installing php5-cgi fixed it. Must be a missing dependency in the phpmyadmin package?

---

