---
title: "shell script needed"
date: 2010-06-21
forum: General Help
---

### Post by UT8F on 2010-06-21
Hello, I need shell script, it should look this:

I run it with command: sudo sh script.sh
And it's executes command /etc/init.d/networking restart every 15minutes, untill I kill it with ctrl+c

---

### Post by UT8F on 2010-06-21
I tried write It by my self:

```
while [ 1 ]; do
/etc/init.d/networking restart
sleep 900
done
```
I'm not a good shell coder, so will it work good, ir maby somethink need to modify?

---

### Post by kaivalagi on 2010-06-21
Looks okay

Alternatively create a script to restart the network once and then run it as a cron job...[http://en.wikipedia.org/wiki/Cron](http://en.wikipedia.org/wiki/Cron)

If you put this as the first line:

```
#!/bin/sh
```

And make the script executable:

```
chmod +x /path/to/script/file
```

You can call it directly from cron which will run it as a root user

---

### Post by Johnsie on 2010-06-21
+1 For the cron job


Create the script and then set cron to run that script every 15 minutes. Cron is great for anything that needs to be scheduled to run at intervals.

---

### Post by philinux on 2010-06-21
Moved to general help.

---

