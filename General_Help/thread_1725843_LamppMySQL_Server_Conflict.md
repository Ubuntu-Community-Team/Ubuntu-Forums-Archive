---
title: "Lampp/MySQL Server Conflict"
date: 2011-04-10
forum: General Help
---

### Post by coronacolada on 2011-04-10
Greetings All,

I recently installed lampp, and when trying to run MySQL afterward, kept getting the "can't connect through socket /var/run/mysqld/mysqld.sock" error. 

I saw a suggestion that I should install the MySql server (apt-get install mysql-server). I did that, and then was able to run mysql (mysql -u root -p). 

Great! 

However, now when I start my apache server, I get an error that another mySql daemon is already running. 

If I stop the mysql server service, I am able to view phpmyinfo, but it doesn't show the database I created.

I take this to mean that there's a conflict, and that lampp cannot cull data from the MySQL server (only from the client installed with it). However, I can't figure out how to login to the mysql client that was installed with lampp, as trying to do so gives me the error listed above. 

I don't think it's a difficult problem, but I have no idea how to fix it. Any help?

---

