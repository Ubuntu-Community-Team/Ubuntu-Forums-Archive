---
title: "Crontab on Ubuntu 6.06"
date: 2009-06-30
forum: General Help
---

### Post by dany84 on 2009-06-30
Hi,
I'm trying to set up crontab to execute a php script.

My crontab file content is:

* * * * * php /var/myDirectory/myfile.php>/tmp/myfile.log 2>/tmp/myfile.err 

The file is successfully executed from command line typing:

php /var/myDirectory/myfile.php

Using crontab it doesn't work.
Crontab service is running, in crontab log file I can't see anything regarding the execution of my script.
I've even tried to run a simpler command:

* * * * * echo "hello" > /tmp/log.txt

but it doesn't work at all.

My crontab file is located in /var/spool/cron/crontabs and it's called "root" as I access with root profile to the command line.

Anyone knows why it's not working?

Thanks :)

---

### Post by ManiacDan on 2009-06-30
Edit crontabs directly using:
```
crontab -e
```

View crontabs using:
```
crontab -l
```

If crontab -l doesn't show you anything, no crontab is installed.

-Dan

---

### Post by dany84 on 2009-06-30
> **ManiacDan said:**
> Edit crontabs directly using:
```
crontab -e
```View crontabs using:
```
crontab -l
```If crontab -l doesn't show you anything, no crontab is installed.

-Dan

Already done.

Crontab is installed, my crontab file is read and written, but crontab doesn't run and no errors are shown in log.

---

### Post by Cheesehead on 2009-06-30
User crontabs are stored at /var/spool/cron/crontabs
If you are running a user-level cron job, use the crontab -e and -l commands to set the user-level crontab.


But root's crontab is stored at /etc/crontab. That's why your particular crontab isn't working.

Editing root's crontab is a *really* *bad* *idea*. Instead, use the cron.* folders provided.

If you are running a periodic script (hourly, daily, weekly, monthly) as root, put a link to the script in the /etc/cron.hourly (or .daily or .weekly or .monthly) folder. 

Special scripts that run at different intervals should be linked to the /etc/cron.d folder.

Think about permissions - these scripts will run as root, not a user, and may have different consequences than you may expect.

There are several very good cron tutorial scattered around the web to explain the how and why of the root crontab without damaging your system.

---

### Post by dany84 on 2009-06-30
> **Cheesehead said:**
> User crontabs are stored at /var/spool/cron/crontabs
If you are running a user-level cron job, use the crontab -e and -l commands to set the user-level crontab.


But root's crontab is stored at /etc/crontab. That's why your particular crontab isn't working.

Editing root's crontab is a *really* *bad* *idea*. Instead, use the cron.* folders provided.

If you are running a periodic script (hourly, daily, weekly, monthly) as root, put a link to the script in the /etc/cron.hourly (or .daily or .weekly or .monthly) folder. 

Special scripts that run at different intervals should be linked to the /etc/cron.d folder.

Thank you very much!
So, if I save my file in folder /etc/cron.d - as I'm running the script every minute -  it should work, right?

> 
Think about permissions - these scripts will run as root, not a user, and may have different consequences than you may expect.

There are several very good cron tutorial scattered around the web to explain the how and why of the root crontab without damaging your system.
Any link? I'm a bad searcher, in two days I've found nothing about this :oops:

---

### Post by t4thfavor on 2009-06-30
1-59 * * * * /usr/bin/php yourscriptname>> your.txt

Cron doesn't even know where php is :)

I do it that way anyways with perl, and it works. If its a root level cron job, you need to sudo crontab -e.

EDIT:
nm, the sudo crontab -e was on my trixbox which already was a root login, I wasn't reading my terminal properly...

---

### Post by dany84 on 2009-06-30
> **t4thfavor said:**
> 1-59 * * * * /usr/bin/php yourscriptname>> your.txt

Cron doesn't even know where php is :)

I do it that way anyways with perl, and it works. If its a root level cron job, you need to sudo crontab -e.

I tried also that, but the problem is that my file is not being executed at all.
And now I'm concentrating on this simple script:

* * * * * echo "hello" > /tmp/log.txt

just to see if it runs at least.

---

### Post by t4thfavor on 2009-06-30
1-59/5 * * * * perl /etc/asterisk/MonitorTrunks.pl >> /etc/asterisk/trunks.log

runs a cron job every 5 minutes. I would not understand why your script does not run.

Perhaps Ubuntu runs them differently.


Nope, 

1-59 * * * * /bin/bash /home/chance/bob.sh >> /home/chance/bob.out

executes bob.sh and puts its contents into /home/chance/bob.out every minute without fail.

your doing it wrong... 


did you make sure your outfiles were created, that may be what I did differently.

---

### Post by dany84 on 2009-06-30
> **t4thfavor said:**
> 
did you make sure your outfiles were created, that may be what I did differently.
I've created an empty file log.txt but my crontab doesnt' edit it.
According to log, there are some files in folder cron.d that runs as root when they have to, but my file is totally ignored.
Really don't know what I'm doing wrong...

---

### Post by HotForLinux on 2009-07-13
The files need not be created in advance but be careful:  if you have been touching things around, watch for the permissions 

sudo echo "hello" > somefile

won't write in somefile anything if you don't have permissions to write in it.

---

