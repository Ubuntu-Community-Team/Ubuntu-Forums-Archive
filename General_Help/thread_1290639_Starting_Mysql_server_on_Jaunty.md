---
title: "Starting Mysql server on Jaunty"
date: 2009-10-13
forum: General Help
---

### Post by aren55555 on 2009-10-13
Hi all,

I've been trying to set-up a server with mysql.
I have it all installed, but I am not exactly sure how to start it.

Right now I am using this command to start the server:
```
sudo /etc/init.d/mysql start
```

Furthermore I have to do this every time I start my computer to start up the mysql server.

My two questions are:
1. Is this the correct way to start the mysql server?
2. Is there a way to automate this so that mysql is always running since startup?

---

### Post by wodzu12 on 2009-10-14
it is correct way
actually if you have installed it with the package manager, it has already been set up to initialise with every boot (and exactly this way)

just check if you have mysql server running  after boot - search for mysqld with:
```
sudo ps -e
``` 
or just type in the terminal to connect to it as a root user:
```
mysql -u root -p
```

if it doesnt start automatically, just type in the terminal:
```
sudo update-rc.d mysql defaults
```
it will add the command you are already have been using to the start queue

actually running this last command will probably give you info, that this command is in the queue already

---

