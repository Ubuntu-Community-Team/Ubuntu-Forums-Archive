---
title: "Error connecting to mysql"
date: 2011-04-04
forum: General Help
---

### Post by duckyq on 2011-04-04
Hi all, i'm trying to connect to mysql which is on windows server 2008 via ubuntu, and this error message [COLOR=#333333]ERROR [/COLOR][COLOR=#4e0000]1042[/COLOR][COLOR=#888888]([/COLOR][COLOR=#333333]HY000[/COLOR][COLOR=#888888]):[/COLOR][COLOR=#333333] Can[/COLOR][COLOR=#4e0000]'[/COLOR][COLOR=#333333]t get hostname [/COLOR][COLOR=#0c2d53]for[/COLOR][COLOR=#333333] your address appears, i'm able to ping my windows server 2008, i've attach a screenshot of the error. i've installed mysql-client-core-5.1. [/COLOR][COLOR=#333333]Any help would be greatly appreciated. [/COLOR]

---

### Post by duckyq on 2011-04-04
bump

---

### Post by Ryan Dwyer on 2011-04-04
The MySQL server is unable to resolve the client's IP address into a hostname. You should fix it using whatever method you want (try installing winbind on the client), then run FLUSH HOSTS on the server and try connecting again.

If that fails, you could try adding a DNS PTR record for the client's IP or add an entry to the server's hosts file, then run FLUSH HOSTS again.

You could also add skip-name-resolve to MySQL's config file under the [mysqld] section, then restart MySQL.

---

### Post by duckyq on 2011-04-04
> **Ryan Dwyer said:**
> The MySQL server is unable to resolve the client's IP address into a hostname. You should fix it using whatever method you want (try installing winbind on the client), then run FLUSH HOSTS on the server and try connecting again. 
 
If that fails, you could try adding a DNS PTR record for the client's IP or add an entry to the server's hosts file, then run FLUSH HOSTS again..
 
Hi ryan can you provide more details on these 2 solutions?
 
> **Ryan Dwyer said:**
>  
You could also add skip-name-resolve to MySQL's config file under the [mysqld] section, then restart MySQL.
i've tried this before but it doesn't seem to work

---

### Post by dazman19 on 2011-04-04
your user needs to be user@ip 

CREATE USER 'jeffrey'@'localhost' IDENTIFIED BY 'mypass'; thats probably what you ahve in the database

you need to alter it on the localhost if you cant log in remotely.

to 'jeffrey'@'%' or if you only want access from the one IP then:

'jeffrey'@'192.168.185.123'

---

