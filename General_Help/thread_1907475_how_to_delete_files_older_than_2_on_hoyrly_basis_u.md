---
title: "how to delete files older than 2 on hoyrly basis using find command"
date: 2012-01-11
forum: General Help
---

### Post by nrmurali on 2012-01-11
we need to delete files older than 2 days on hourly basis by using find command in the script.....

script will run every hour.....

thank's in advance...

---

### Post by topsites on 2012-01-11
[http://lmgtfy.com/?q=delete+files+older+than+2+days+using+the+find+command](http://lmgtfy.com/?q=delete+files+older+than+2+days+using+the+find+command)

As for doing it every x hours, you'll need to use cron.hourly
[http://clickmojo.com/code/cron-tutorial.html](http://clickmojo.com/code/cron-tutorial.html)

---

### Post by nrmurali on 2012-01-11
we r using ubuntu 10.04 32 bit version operating system...

---

### Post by nrmurali on 2012-01-11
We need to delete the files older than two days but hour by hour we want delete. For example 1am to 2am first. 2am to 3am second, 3am to 4am third etc...

---

### Post by Lars Noodén on 2012-01-11
You can read up on [find](http://manpages.ubuntu.com/manpages/oneiric/en/man1/find.1.html) and look around for examples on the net.  It will be something like this:

```

find /some/path/ -mtime +2 -exec rm "{}" \;

```

Look at the option 'atime' for an explanation of how the time is calculated to make sure it is what you wanted.

To run it hourly, put your script in /etc/cron.hourly/

---

