---
title: "Crontab entry doesn't work"
date: 2011-05-18
forum: General Help
---

### Post by andriu1 on 2011-05-18
Hi all,

    Now here i am trying to set up a task in crontab of a Ubuntu 10.0.4, but I've been making tests and it doesn't work me, so i would like your help to check the mistake.

    The task must run a script to stop some services and to reboot the machine

    These are the steps that I've followed

    First, I've created the script, reinicio.sh:

```
$ sudo vi reinicio.sh
#!/bin/sh
date > /salida.txt
echo "Stopping ldap service..." >> /salida.txt
service slapd stop >> /salida.txt
echo "Stopping mysql service..." >> /salida.txt
service mysql stop >> /salida.txt
echo "Restarting ..." >> /salida.txt
/sbin/shutdown -r >> /salida.txt
```     The first thing that is very strange is that mysql stop instruction doesn't work, although slapd works fine. But, if I execute manually "sudo service mysql stop" in command line it works, but it doesn't work when i run the script through the crontab

     Second, I've created task in crontab

```
$ sudo crontab -e -u root
```    Like this, to test the script reinicio.sh at 14:25, or another time modify the parameters.

```
$ sudo crontab -l -u root
# m h  dom mon dow   command
25 14 * * * /usr/bin/reinicio.sh

$ 
```    Well, if I check the output file salida.txt, it seems that the task works, and the script has run, but no system restart has been launched

$ cat /salida.txt 
Wed May 18 14:25:01 PDT 2011
Stopping ldap service...
Stopping OpenLDAP: slapd.
Stopping mysql service...
Restarting ...

Could anyone help me, please?

Thanks in advance

Regards
Andres

---

### Post by andriu1 on 2011-05-18
Ok Ok, I've changed restart command to $shutdown -r now and now it works, but mysql stop command doesn't give me any track into the output file "salida.txt". I think that this instruction does not execute.

How can i do/test?

Thanks again
Andres

---

### Post by andriu1 on 2011-05-19
Ok ok again, "$sudo service mysql stop" resolve the other problem. Now it works.

Regards,
Andres

---

