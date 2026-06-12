---
title: "can't open a mysql database"
date: 2006-03-19
forum: General Help
---

### Post by bistro on 2006-03-19
Hi

I have installed mysql query browser and mysql admin. The server appears to be running Ok -  [screenshot]("http://www.amberpla.net/server.jpg") - but evry tiem I try to connect to a database, either through the query browser or via the 'Catalogs' option in mysqladmin, the windows just shut down.

Any advice, please?

Thanks very much

Dave

---

### Post by ToiletDuck on 2006-03-19
How do you get the gui to come up?

---

### Post by bistro on 2006-03-19
Hi

both the query browser and admin open OK. The query browser gui shuts down after I enter my password. The admin gui shuts down when I click on one of the databases via 'Catalogs' or when I click on 'Server Connections'.

Dave

---

### Post by hw-tph on 2006-03-19
So what happens when you connect with the regular client (/usr/bin/mysql)?


Håkan

---

### Post by DoktorSeven on 2006-03-19
Seems to work fine here.  If you run **mysql-admin** from a terminal, do any error messages print in the terminal when it crashes?

---

### Post by bistro on 2006-03-19
[QUOTE=DoktorSeven]Seems to work fine here.  If you run **mysql-admin** from a terminal, do any error messages print in the terminal when it crashes?[/QUOTE]
Yes, I get "Segmentation fault" - I googled it to read an explanation but I don't know what to do about it.

---

### Post by alkalined on 2006-05-06
I'm having the same problem. 
Since a google research did not help I tried submitting it as a mysql bug, hopefully get some help from there. :( 
[http://bugs.mysql.com/bug.php?id=19587&thanks=2&notify=3](http://bugs.mysql.com/bug.php?id=19587&thanks=2&notify=3)

---

### Post by deathshadow on 2006-05-06
I had the same problem initially on one server with the 64 bit version, the only solution I could find that worked was to switch back to the 32 bit version - after that it was fine.

64 bit - vague computing term meaning 'not ready for prime-time'

---

