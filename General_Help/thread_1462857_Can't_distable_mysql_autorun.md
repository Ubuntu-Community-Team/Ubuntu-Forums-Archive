---
title: "Can't distable mysql autorun"
date: 2010-04-26
forum: General Help
---

### Post by Lord_JABA on 2010-04-26
I delete every symlink to mysql in rc but it's still starting.
Plese advice. ```
sudo ls /etc/rc*|grep sql
``` returns nothing

---

### Post by Lord_JABA on 2010-05-04
Any ideas? Maybe a should post it as bug on launchpad?
It's really off:
[IMG]http://img687.imageshack.us/img687/4774/runlevel.png[/IMG]

But is on:
```
ps -A|grep mysql
  878 ?        00:00:03 mysqld

```

---

### Post by gmargo on 2010-05-04
On my 9.10 Karmic system, I ran
```

update-rc.d -f mysql remove

```and now mysql does not start at boot.  FYI, this is the "proper" command-line method to edit the symlinks in the rc.d directories.

If that does not work, and the daemon is still started, it may be getting started via a dependency of another tool that is being started.  (I was hoping to test that theory, but the update-rc.d worked for me.  Try "grep mysql /etc/rc*.d/*" to see if anyone else is referencing it.)

---

### Post by Lord_JABA on 2010-05-05
thank's. It's a reminder- every day you can learn something.

---

### Post by Lord_JABA on 2011-01-28
In maverick it is bit more complicated due to trasition from init to [Upstart]("http://upstart.ubuntu.com/index.html").
The init is now event based which mean not starting a queue of processes but something like "when network up start this and that" or "when file system up start that and that" etc. . This mean You must find corresponding /etc/init(in this case /etc/init/mysql.conf) entry and rem (#) "start on" line.
Hope it helps somebody

PS maybe somebody knows update-rc.d like utility working with upstart ??

---

### Post by veggen on 2011-01-28
Sorry for the off-topic, but what's the tool you used on that screenshot?

---

