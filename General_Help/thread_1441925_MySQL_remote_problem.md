---
title: "MySQL remote problem"
date: 2010-03-29
forum: General Help
---

### Post by mosquetero on 2010-03-29
Hi all!!

I am using two PCs, they all have the same configuration although one has Windows XP and the other Ubuntu 9.04. I want them to connect to the MySQL server of the other one. I was having problems because I was getting always an exception of communications link failure. I solved it in Windows with: 

```

grant all on databasename.* to your_mysql_user@remote_host identified by 'your_mysql_user_password'; 

```

However in Ubuntu it is not working. I even restarted the server but I cannot connect to the Ubuntu Mysql server with my Windows PC :(. Anyone knows if I must do an extra step in Ubuntu?

Thanks in advance

---

### Post by mosquetero on 2010-03-29
Solution found! It was in an already existing Ubuntu thread:

[http://ubuntuforums.org/showthread.php?t=229868](http://ubuntuforums.org/showthread.php?t=229868)

Thanks lamego

---

