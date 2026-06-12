---
title: "Ubuntu Faillog confusion"
date: 2011-07-11
forum: General Help
---

### Post by ondemanddesign on 2011-07-11
If I understand correctly, faillog -a should show all the accounts I have, and how many failed log in attempts have been made. I intentionally entered the incorrect password for a user multiple times, yet the output of faillog -a never changed.

```

ftp             0        0   12/31/69 17:00:00 -0700

```

Again, my goal is to check which users have had failed log in attempts without having to sift through the auth.log, is this possible?

---

### Post by ondemanddesign on 2011-07-13
Bump, I need some input on this. I can't seem to get a solid answer about when data goes into this database.

---

### Post by Rubi1200 on 2011-07-13
Hi,
you should also take a look at the following commands:

```
last
```
show listing of last logged in users

```
sudo lastb
```shows a log of the        file **/var/log/btmp**, which contains all the bad login attempts.
[http://manpages.ubuntu.com/manpages/natty/en/man1/lastb.1.html](http://manpages.ubuntu.com/manpages/natty/en/man1/lastb.1.html)

---

### Post by ondemanddesign on 2011-07-14
> **Rubi1200 said:**
> Hi,
you should also take a look at the following commands:

```
last
```
show listing of last logged in users

```
sudo lastb
```shows a log of the        file **/var/log/btmp**, which contains all the bad login attempts.
[http://manpages.ubuntu.com/manpages/natty/en/man1/lastb.1.html](http://manpages.ubuntu.com/manpages/natty/en/man1/lastb.1.html)

Thank you, but what qualifies a bad login attempt? I intentionally attempted to log in using a bad password several times but never appeared on this list.

---

