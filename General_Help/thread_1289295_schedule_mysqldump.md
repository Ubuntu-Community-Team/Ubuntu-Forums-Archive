---
title: "schedule mysqldump"
date: 2009-10-12
forum: General Help
---

### Post by Dosshell on 2009-10-12
I can't get a scheduled daily backup of my mySQL database to work.
I have following command added in Gnome Schedule:
/usr/bin/mysqldump -Q -u MYUSER -pPASS db_name > /home/user/backupfile.sql

If i execute the command either in terminal or in gnome schedule it works great! But when it supposed to "time-execute" it creates an empty file.

Why doesn't it work on scheduled time?

---

### Post by Giblet5 on 2009-10-12
What happens if you redirect the input in the cron entry via:

```
0 19 * * * /usr/bin/mysqldump ..... < /dev/null > /tmp/mydump.log 2>&1
```

(Redirect stdin from /dev/null, redirect stdout and stderr to /tmp/mydump.log)

---

### Post by Dosshell on 2009-10-12
i executed
```

$su
$cron 0 19 * * * /usr/bin/mysqldump ..... < /dev/null > /tmp/mydump.log 2>&1
```
and the dumpfile sad:
```
cron: can't lock /var/run/crond.pid, otherpid may be 3239: Resource temporarily unavailable
```

---

