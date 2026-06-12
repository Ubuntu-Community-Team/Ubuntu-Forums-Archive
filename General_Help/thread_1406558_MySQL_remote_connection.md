---
title: "MySQL remote connection"
date: 2010-02-14
forum: General Help
---

### Post by ikon_ on 2010-02-14
I presume this is not the exact place to post this thread, but I thought just in case somebody might be able to help me .
I am trying to connect to a mysql database remotely, although I can login to the machine and I also have the mysql username and password but it doesn't allow me to access it. It gives an error.
```
"Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (13)"
```
I really need to fix the problem quickly. Somebody please help.

---

### Post by theDaveTheRave on 2010-02-23
ikon_

first off you should ensure that you are able to "ping" the system you are attempting to log into.

Then depening on the user that is trying to log in remotely you will need to ensure that they have the relavent permissions to log in.

Default permissions are for the user to only have access from @localhost

YOu can either set it to a specified IP or set it to '%' (the mysql wild card character meaning 'all hosts' in this instance).

so assuming you have a user called 'ikon_' with a password of (for arguments sake) 'remote' you could log on with this code...

```

mysql -uikon_ -h255.255.255.255 -p

```

obviously replace 255.255.255.255 with the ip of your target machine.

the terminal will then ask for the password for the user, and hey presto, you should be logged in!

if you think you may have an problem with the server, to check you have the right command to log in you can check it with this command....

```

mysql -uanonymous -h193.62.203.76

```

This is a public database. If you don't get to the mysql prompt you obviously have other problems, such as not having the 'client' installed correctly on the terminal you are connecting from.

to confirm you can run a

```

show databases;

```

you will notice that this public server doesn't have a password attached to the user identified as 'anonymous', as this user only has select options.

hope that helps you out

david

---

