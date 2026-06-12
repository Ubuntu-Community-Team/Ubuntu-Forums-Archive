---
title: "Can't connect to mysql from remote AND local web server"
date: 2009-10-05
forum: General Help
---

### Post by sdlyr8 on 2009-10-05
I have a ubuntu box that is acting like my server that just runs my database and apache on it. I want to be able to connect to the database from my windows machine and other ubuntu machine. I enabled the remote access to it, but now I can't connect from the local machine to its database and the web server can't connect either. what do I need to set to be able to log in from a remote machine and still have access locally?

---

### Post by elvisd on 2009-10-05
Hi,

in /etc/mysql.my.cnf you should configure the bind-address parameter.
then in mySql you should configure the user from which host is able to connect.

---

