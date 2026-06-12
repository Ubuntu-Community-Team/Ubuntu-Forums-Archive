---
title: "MYSQL Connection problem"
date: 2012-02-13
forum: General Help
---

### Post by Mrkrabz1 on 2012-02-13
I'm running Ubuntu desktop and I have installed Apache, PHP, MYQl etc. I have gone in and setup the MYSQL database needed for my game server. However once I started the server MYSQL comes back with this error:

```

Error connecting to DB: Lost connection to MySQL server at 'reading initial communication packet', system error: 0

```

Password and everything is fine, everything is over localhost so a firewall shouldn't be an issue (its disabled afaik anyway). I'm also using tmysql (Game server plugin).

Repost from other section.

---

### Post by lechien73 on 2012-02-13
Hi and welcome to the forums,

What's the content of your /etc/hosts.deny file?

You're looking for lines like:

```
ALL: ALL: DENY
```

or

```
mysqld: ALL: DENY
```

---

### Post by cabaro on 2012-02-13
Try changing the bind-address to your ip.

[https://help.ubuntu.com/8.04/serverguide/C/mysql.html](https://help.ubuntu.com/8.04/serverguide/C/mysql.html)

---

### Post by Mrkrabz1 on 2012-02-13
> **lechien73 said:**
> Hi and welcome to the forums,

What's the content of your /etc/hosts.deny file?

You're looking for lines like:

```
ALL: ALL: DENY
```

or

```
mysqld: ALL: DENY
```

Everything is commented out.

```


# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.
#
# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID

```

As for my bind IP it's already set to my Dedi's IP. (Plus this is all localhost anyway).

Running sudo netstat -tap | grep mysql 
gives

```

tcp        0      0 ks365791.kimsufi.:mysql *:*                     LISTEN      8324/mysqld

```

---

### Post by SeijiSensei on 2012-02-13
> **Mrkrabz1 said:**
> ```

tcp        0      0 ks365791.kimsufi.:mysql *:*                     LISTEN      8324/mysqld

```

Why is it listening on port 8324?  The default MySQL port is 3306.

---

### Post by Mrkrabz1 on 2012-02-13
> **SeijiSensei said:**
> Why is it listening on port 8324?  The default MySQL port is 3306.

I've just noticed that myself, I tried changing my script to use that port and it still says the same error.

---

### Post by Mrkrabz1 on 2012-02-13
port		= 3306

This is in my my.cnf how come it's not on that port?

---

### Post by Mrkrabz1 on 2012-02-13
Upon doing netstat -nat



tcp        0      0 94.23.5.200:3306        0.0.0.0:*               LISTEN

It's on 3306?

---

### Post by SeijiSensei on 2012-02-14
My mistake. I think I confused the process ID with the port.  The first entry you showed used the symbolic service name "mysql" rather than 3306 since you hadn't used the -n switch.

Sorry!

Did you install the mysql client as well as mysql-server?  Can you connect to the database with that?

```
mysql --user=user_name --password=your_password db_name
```

---

