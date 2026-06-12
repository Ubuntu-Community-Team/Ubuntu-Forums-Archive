---
title: "MySQL Terminal question"
date: 2011-03-15
forum: General Help
---

### Post by Kruzus on 2011-03-15
Hello all! I am new here :D My name is Bek, and I got few questions :D

I've watched the movie "The Social Network" and there is a scene that young developers of Facebook they use some kind of software that they see REAL time mysql query updates. Like when users registered/clicked like/dislike they saw that on the monitor. I just wondered can i do that? Is there any software? 

Thank you!

---

### Post by falko on 2011-03-15
You could enable MySQL logging in /etc/mysql/my.cnf and then tail the MySQL log. But please note that this can hurt performance.

---

### Post by Kruzus on 2011-03-15
> **falko said:**
> You could enable MySQL logging in /etc/mysql/my.cnf and then tail the MySQL log. But please note that this can hurt performance.

is there any php scpipts that you select your table and it will refresh when it's written (not phpmyadmin) well like similar of that one. I really dont want to mess up the mysql config and make it slower :S

---

