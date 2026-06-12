---
title: "Restart SAMBA"
date: 2010-06-05
forum: General Help
---

### Post by theozzlives on 2010-06-05
```
ozzie@ozzie-laptop:~$ sudo /etc/init.d/samba restart
[sudo] password for ozzie: 
sudo: /etc/init.d/samba: command not found
o
```

How do you do it now days?

---

### Post by sdennie on 2010-06-05
On newer version of Ubuntu, /etc/init.d commands (unfortunately) are deprecated.  Try:

```

sudo service smbd restart

```

---

### Post by theozzlives on 2010-06-05
> **sdennie said:**
> On newer version of Ubuntu, /etc/init.d commands (unfortunately) are deprecated.  Try:

```

sudo service smbd restart

```

Just when you think you got it down....

---

### Post by keepitsimpleengr on 2012-07-04
> **sdennie said:**
> On newer version of Ubuntu, /etc/init.d commands (unfortunately) are deprecated.  Try:

```

sudo service smbd restart

```

This doesn't work in 12.04...

---

### Post by Quackers on 2012-07-04
This thread is 2 years old and consequently things may have changed.

---

