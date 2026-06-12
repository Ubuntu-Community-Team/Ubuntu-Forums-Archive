---
title: "Crontab to execute a php-script?"
date: 2006-04-04
forum: General Help
---

### Post by iluminate on 2006-04-04
Hi all Ubuntu's

I have read cron How2's, tested back and forward to get this working but STILL I can not get it to work.
So if there is someone who can give a helping hand to a newbie I would more than happy.
I am trying to run a php script located in /var/www/script.php and it should execute every day at 23:00.

* 23 * * * /var/www/script.php

Is this correct ?
Or do I have to add this to the path - /var/www/php script.php ??

---

### Post by BoSchafers on 2006-04-04
Try:

*23 * * * * wget -q -O /dev/null [http://example.com/php.php](http://example.com/php.php)

---

### Post by iluminate on 2006-04-05
Thnx for the reply!

Nope still wont work. Is there an really easy way to just test if the cron is working at all? Like echo something out?
What about -
1 * * * * echo "Hello World"

Also when I pipe it to a text file, the file is always empty.
PS.
Do I have to create the file manually or will it creat it for me?
D.S

---

### Post by Moobert on 2006-04-05
First install the terminal version of php:

```

sudo apt-get install php<version of php you are using>-cli

```

then edit your users crontab by:

```

crontab -e

```

this will most likely bring up vi, press "i" then input:

* 23 * * * php -q /var/www/script.php

then save the file out buy pressing escape followed by ":wq" and enter

---

### Post by iluminate on 2006-04-06
Hi,

php5-cli is allready installed and still i can not get it to work.
If I want to read what is going wrong, where can I do it?

If I want to pipe it to a textfile is this correct:

* 23 * * * php -q /var/www/script.php >> /home/myhomefolder/somelog.log
?
I checked the permissions of the file and it seems to be right.
What user is going to execute the cron job? www-data or it doesn't matter?

Many thanks in advance

---

### Post by iluminate on 2006-04-06
Hmm....
Can someone please help me troubleshoot where the prob. is?

```
gringo@blizzard:~$crontab -e
```

MC is my editor and I type in -
*/5 9-23 * * mon,tue,wed,thur,fri wall "Are we there yet?"

I save & exit!

```
crontab -l
```
Show me the job I have written above.
So accouring to the Wiki this should give me a message every 5 min - right?
But nothing!!!!!!!
Did ```
ps -ef |grep cron
```
Which gave me - root     22990     1  0 Apr05 ?        00:00:00 /usr/sbin/cron

So where am I going WRONG ???](*,)

---

