---
title: "'service mysql start' &quot;alternate user&quot;"
date: 2010-06-08
forum: General Help
---

### Post by iMisspell on 2010-06-08
If there a way to start (and stop) a single service under an alternate user (not root) ?

I have a cron job on a desktop machine (lucid) which will backup a few MySQL tables (on that machine), but the mysql engine will not all ways be running, so the script will *`service mysql status`* and from there start the service if it is shut down. The thing is the cron job is under a user account and not the root account (running the cron job under the root account is not an option).

If anyone could give me a heads-up on how to start a service under an alternate user that would be great.

_

---

### Post by iMisspell on 2010-06-11
Just bringing it around for some fresh eyes...

---

### Post by Ryan Dwyer on 2010-06-11
Create a separate script called start-mysql. In it, put the following:

#!/bin/bash
service mysql start

Make the owner/group root, make it executable, then chmod u+s start-mysql. This means anyone can execute it as root.

Then change your cron script to call that file.

---

### Post by diesch on 2010-06-12
> **Ryan Dwyer said:**
> Create a separate script called start-mysql. In it, put the following:

#!/bin/bash
service mysql start

Make the owner/group root, make it executable, then chmod u+s start-mysql. This means anyone can execute it as root.


No. For security reasons he SUID bit doesn't work with scripts under Linux.

---

### Post by iMisspell on 2010-06-12
> **diesch said:**
> No. For security reasons he SUID bit doesn't work with scripts under Linux.
So it is not possible ?

Is that why it produces the same results as trying to start it from command line with non-root user ?
> me@here:~/Desktop$ ./mysql_service.sh
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.95" (uid=1000 pid=26922 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
me@here:~/Desktop$


Thanks for the suggestion though, Ryan Dwyer.


_

---

### Post by diesch on 2010-06-18
> **iMisspell said:**
> So it is not possible ?


Either use a language that compiles to native code (like C) to write a program that starts the MySQL server  and set it SUID root or use sudo to allow the user to run  "/usr/sbin/service mysql start" as root without a password

---

