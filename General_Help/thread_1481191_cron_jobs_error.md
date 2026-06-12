---
title: "cron jobs error"
date: 2010-05-12
forum: General Help
---

### Post by milindras on 2010-05-12
Hi,
I have sheduled 02 cron jobs for a website on my web server.
 
The command is im trying to run :
 
lynx -source [http://www.mydomain.co.uk/cron/queue.php](http://www.mydomain.co.uk/cron/queue.php)
&
lynx -source [http://www.mydomain.co.uk/cron/sendmail.php](http://www.mydomain.co.uk/cron/sendmail.php) 
 
When i run it the out put comes as :
 
[FONT=Courier New]/bin/sh: lynx: command not found
[/FONT]
when i run the same command on my other web server working fine. 
Dont know why its not on this server. Actually this server i built recently.
The server is Ubuntu 8 LTS.
 
Many Thanks

---

### Post by iponeverything on 2010-05-12
do:
```
which lynx

```

then use the full path in cron, like

```
/usr/bin/lynx
```

---

### Post by milindras on 2010-05-12
code 
which lynx
doest give any out put
 
if I give the full path it says :
/bin/sh: /usr/bin/lynx: No such file or directory

Should I need to install anything to run that command? (lynx)
 
Thanks

---

### Post by iponeverything on 2010-05-12
This will install it.

```
sudo apt-get install lynx
```

---

### Post by milindras on 2010-05-12
Thanks. Thats what it needed.
 
Thanks again

---

