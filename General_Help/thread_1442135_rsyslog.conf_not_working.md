---
title: "rsyslog.conf not working"
date: 2010-03-29
forum: General Help
---

### Post by Yadda on 2010-03-29
Hello,

I have added the line to rsyslog.conf

```
local3.*        /var/log/foo
```

I then create the log file with

```
sudo touch /var/log/foo
```

when I run the command

```
logger -p local3.info foobar
```

foobar does not appear in the /var/log/foo but it does appear in several other logs.

What am I doing wrong?

---

