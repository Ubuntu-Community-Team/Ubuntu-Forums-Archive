---
title: "mysql: /etc/init.d/mysql doesn't do anything."
date: 2010-07-10
forum: General Help
---

### Post by intheflesh on 2010-07-10
Hello! I've installed **mysql-server-5.1** and I can start the daemon manually (when I **[FONT=Courier New]mkdir mysqld/[/FONT]** in **[FONT=Courier New]/var/run[/FONT]** and **[FONT=Courier New]chown[/FONT]** it to **[FONT=Courier New]mysql.mysql[/FONT]**) and run **[FONT=Courier New]mysql[/FONT]**, create users, databases, tables, grant privileges - everything. But when I reboot, the directory is gone and mysql service not started.

Running **[FONT=Courier New]sudo /etc/init.d/mysql start[/FONT]** (or **[FONT=Courier New]stop[/FONT]** or **[FONT=Courier New]restart[/FONT]** or **[FONT=Courier New]status[/FONT]**) just prints the message that the script I've been trying to invoke has been converted into an Upstart job, and suggesting me to run **[FONT=Courier New]service mysql start[/FONT]***[FONT=Courier New]/or whatever[/FONT]* (which doesn't do anything, it does not even print any messages, even when I prefix it with **[FONT=Courier New]sudo[/FONT]**).

Everything with *mysql-* in front is installed: mysql-server, mysql-server-5.1, mysql-client, mysql-client-5.1, mysql-common...

How do I make it run on startup, and with [FONT=Courier New]**/****etc/init.d/mysql start**[/FONT]?
For the record, **[FONT=Courier New]sudo service apache2 restart[/FONT]** works. :-|

---

### Post by Leppie on 2010-07-10
have you checked the syslog after trying to launch it?
```
sudo service mysql start
tail /var/log/syslog
```
could you post the output here?

---

### Post by intheflesh on 2010-07-10
```

$ sudo service mysql start
$ tail /var/log/syslog
Jul 10 19:20:46 emptiespace nullmailer[1392]: Starting delivery: protocol: smtp host: mail. file: 1274915713.14710
Jul 10 19:20:46 emptiespace nullmailer[5870]: smtp: Failed: Connect failed
Jul 10 19:20:46 emptiespace nullmailer[1392]: Sending failed:  Host not found
Jul 10 19:20:46 emptiespace nullmailer[1392]: Starting delivery: protocol: smtp host: mail. file: 1275515893.24988
Jul 10 19:20:46 emptiespace nullmailer[5872]: smtp: Failed: Connect failed
Jul 10 19:20:46 emptiespace nullmailer[1392]: Sending failed:  Host not found
Jul 10 19:20:46 emptiespace nullmailer[1392]: Starting delivery: protocol: smtp host: mail. file: 1273266313.19238
Jul 10 19:20:46 emptiespace nullmailer[5878]: smtp: Failed: Connect failed
Jul 10 19:20:46 emptiespace dhclient: bound to 192.168.1.8 -- renewal in 868701201 seconds.
Jul 10 19:20:53 emptiespace kernel: [17971.846253] ath5k phy0: unsupported jumbo


```

At first it was showing only nullmailer messages, so I stopped the nullmailer service. Should I have done that?

---

### Post by rogerdg on 2010-07-10
It looks like SMTP clobbered your MySql messages.  Try this:
> sudo service mysql start; tail /var/log/syslogPutting a ; between 2 commands forces the second to run immediately following the first, and may allow you to catch the messages output by mysql.

> sudo service mysql start; tail -20 /var/log/syslog Will cause the last 20 messages to be displayed (you can change the 20).  Adding "| less" to the end of the line (omitting the quotes) will allow you to scroll through the messages if you use a number of lines that is greater than the lines on your screen.  Press SPACE after reading a full screen, q to quit.

---

### Post by Leppie on 2010-07-10
alternatives are, running the following command:
```
cat /var/log/syslog | grep mysql
```

or open 2 termnials, in one run:
```
tail -f /var/log/syslog
```
and then in the second run:
```
sudo service mysql start
```

---

### Post by intheflesh on 2010-07-20
> **Leppie said:**
> alternatives are, running the following command:
```
cat /var/log/syslog | grep mysql
```Returns nothing.

> **Leppie said:**
> or open 2 termnials, in one  run:
```
tail -f /var/log/syslog
```and then in the second run:
```
sudo service mysql start
```
That one just shows nullmailer messages (about 100 a second), but nothin like 'mysql' is printed.

Btw, do I need nullmailer service? I'm not running a SMTP server or anything. Stopping it desn't seem to break anything...

---

