---
title: "Cron Job confuses me"
date: 2009-11-05
forum: General Help
---

### Post by tropdoug on 2009-11-05
I have a cron job I have written following a number of different threads 

the job is in /etc/crontab see below

```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user    command
17 *    * * *    root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
# Close down machine every night
0 21     * * *     root    shutdown -P 
# "touch" a test file every minute
* * * * * root touch /tmp/root-crontab-test

```I also included the test file to see if I had the cron working. and it does work. However the shutdown line does not activate and I cannot see what is wrong. 

The other thing that confuses me, is that I get this file from sudo gedit /etc/crontab however if I navigate in nautilus to /etc there is no such file, so where is it stored and how is it invoked? 

after editing the file and saving it, I closed the terminal, is this part of the problem?

Some clarification would be greatly appreciated. 

Thanks in advance.

---

### Post by DaithiF on 2009-11-05
the issue may be that the shutdown command also expects to be given a time at which to shutdown.  Usually 'now' is used for this, so your command should be:
```
shutdown -P now

```

---

### Post by breadlord on 2009-11-05
Why not just use poweroff - it takes no arguments.

---

### Post by dvlchd3 on 2009-11-05
I believe you have to specify full paths instead of aliases.

i.e.

```

/sbin/shutdown -P now

```

I would also check the cron logfile and see if it is throwing any errors (/var/log/cron I think).

---

### Post by dcstar on 2009-11-05
> **tropdoug said:**
> 
........
The other thing that confuses me, is that I get this file from sudo gedit /etc/crontab however if I navigate in nautilus to /etc there is no such file, so where is it stored and how is it invoked? 

after editing the file and saving it, I closed the terminal, is this part of the problem?

Some clarification would be greatly appreciated. 


You should not really be editing the file that way, the correct way to edit (as root) crontab is:

```
sudo crontab -e
```

---

