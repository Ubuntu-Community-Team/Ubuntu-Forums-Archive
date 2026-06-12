---
title: "Cron - Command Path"
date: 2011-09-08
forum: General Help
---

### Post by lol22 on 2011-09-08
hi..
m trying to run this file for cron job
/var/www/vhosts/**MySiteName.com**/httpdocs/mail.php
 
what path shud i use for command path?? currently i have tryd these:

  /php 
/var/www/vhosts/**MySiteName.com**/httpdocs/mail.php
and
/usr/local/bin/php /var/www/vhosts/**MySiteName.com**/httpdocs/mail.php
 
m using following:
[B]GNU/Linux Ubuntu 10.04-LTS.
Plesk V10.1.1 (64BITS)
[/B]
 
[B][COLOR=red]thanks in advance[/COLOR]
[/B]

---

### Post by Habitual on 2011-09-08
> **lol22 said:**
> hi..
m trying to run this file for cron job
/var/www/vhosts/**MySiteName.com**/httpdocs/mail.php
 
what path shud i use for command path?? currently i have tryd these:



Open a terminal and type
```
which php
```

then modify the cron with that path + -f /var/www/vhosts/MySiteName.com/httpdocs/mail.php

```
/path/to/php -f /var/www/vhosts/MySiteName.com/httpdocs/mail.php
```

---

### Post by lol22 on 2011-09-09
> **Habitual said:**
> Open a terminal and type
```
which php
```
 
then modify the cron with that path + -f /var/www/vhosts/MySiteName.com/httpdocs/mail.php
 
```
/path/to/php -f /var/www/vhosts/MySiteName.com/httpdocs/mail.php
```
 
 
hey i have tryd this but its not working:
 
/usr/bin/php -f /var/www/vhosts/**MySIteName.com**/httpdocs/mail.php

---

### Post by lol22 on 2011-09-09
its urgent can anyone help me out..

---

### Post by Bodsda on 2011-09-09
> **lol22 said:**
> its urgent can anyone help me out..
 
Does the command work if you run it from a terminal?
 
Bodsda

---

### Post by lol22 on 2011-09-09
yes it works from terminal..

---

### Post by Bodsda on 2011-09-09
> **lol22 said:**
> yes it works from terminal..
 
I'm not very proficient with cron, but I believe the problem is either with the command cron is supposed to be running, or permissions.
 
Can you paste the output of 
```

crontab -l

```
 
Bodsda

---

### Post by lol22 on 2011-09-09
0,15,30,45      *       *       *       *       /opt/psa/admin/sbin/backupmng >/dev/null 2>&1

---

### Post by Bodsda on 2011-09-09
> **lol22 said:**
> 0,15,30,45 * * * * /opt/psa/admin/sbin/backupmng >/dev/null 2>&1
 
Am I missing something, or are you not using crontab for running php???
 
Bodsda

---

### Post by lol22 on 2011-09-09
no..i am only using page and command on my shedule task functionality ...

---

### Post by lol22 on 2011-09-09
i want to run a file mail.php on 1st day of every month at 12:01 am

---

### Post by Bodsda on 2011-09-09
> **lol22 said:**
> i want to run a file mail.php on 1st day of every month at 12:01 am
 
This crontab entry should work
 
01,0,1,1-12,* /usr/bin/php -f /var/www/vhosts/**MySIteName.com**/httpdocs/mail.php 
 
Bodsda

---

### Post by lol22 on 2011-09-09
ok..i will try this...
 
thnx for ur support :)

---

### Post by lol22 on 2011-09-09
> **Bodsda said:**
> This crontab entry should work
 
01,0,1,1-12,* /usr/bin/php -f /var/www/vhosts/**MySIteName.com**/httpdocs/mail.php 
 
Bodsda
and wat shud i use if i want to run every monday at 12.01 AM?

---

### Post by Bodsda on 2011-09-09
> **lol22 said:**
> and wat shud i use if i want to run every monday at 12.01 AM?
 
I think
 
01,12,*,*,1
 
Bodsda

---

### Post by lol22 on 2011-09-20
hi i have tried this path but its not working
 
/usr/bin/php -f /var/www/vhosts/MySIteName.com/httpdocs/mail.php
 
it works when i run it from terminal
 
 
m using following:
GNU/Linux Ubuntu 10.04-LTS.
Plesk V10.1.1 (64BITS)

---

### Post by lol22 on 2011-09-20
its a urgent.. please help me out with command path

---

### Post by dcstar on 2011-09-20
> **lol22 said:**
> its a urgent.. please help me out with command path

Put the php command in a proper Bash script and use cron to run the script.

---

