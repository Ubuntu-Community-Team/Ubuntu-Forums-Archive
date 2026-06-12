---
title: "Courier POP authentication issues"
date: 2011-08-17
forum: General Help
---

### Post by KuduIO on 2011-08-17
```
root@localhost:~# netcat localhost 110
+OK Hello there.
user xxx
+OK Password required.
pass xxx
-ERR Temporary problem, please try again later
```

From syslog:
```
Aug 17 11:31:47 localhost pop3d: Connection, ip=[::ffff:127.0.0.1]
Aug 17 11:31:51 localhost authdaemond: authmysql: mysql_select_db(ehcp) error: Unknown database 'ehcp'
Aug 17 11:31:51 localhost pop3d: LOGIN FAILED, user=xxx, ip=[::ffff:127.0.0.1]
Aug 17 11:31:51 localhost pop3d: authentication error: Input/output error
```

I installed ehcp a long time ago and thought I had got rid of it. How can I fix this?

---

