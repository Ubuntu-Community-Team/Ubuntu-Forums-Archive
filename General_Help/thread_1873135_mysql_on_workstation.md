---
title: "mysql on workstation"
date: 2011-10-31
forum: General Help
---

### Post by lonewolf69 on 2011-10-31
I have a new machine and want to start using mysql.  I try to connect  and cannot get in.  I have not logged in yet so I am trying to reset the  password in a terminal with...
sudo /etc/init.d/mysql reset-password

and it returns...
sudo: /etc/init.d/mysql: command not found

What is wrong here?

Thank you in advance.

Keith

---

### Post by prodigy_ on 2011-10-31
MySQL isn't installed by default. If you didn't install it, read [this HOWTO](https://help.ubuntu.com/11.04/serverguide/C/mysql.html).

In any case, you're also using the wrong command. **/etc/init.d/mysql** is the MySQL server init script and even when MySQL is installed this script only understands certain server-related options like **start** or **restart**.

The command that starts MySQL client is simply **mysql**. Run **man mysql** for more info.

---

### Post by lonewolf69 on 2011-10-31
Thank you....its working.  I have a related question...

Before I installed when I pinged it it replied.  Why is that?:-k

---

### Post by prodigy_ on 2011-10-31
You don't ping an application port, you ping an IP address. ;)

To check for listening TCP ports you could use **netstat** (locally) or **telnet**. Specifically for local MySQL (on the default port): ```

netstat -atn | grep ':3306 '
telnet localhost 3306

```

---

