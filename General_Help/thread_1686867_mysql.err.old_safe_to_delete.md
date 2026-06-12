---
title: "mysql.err.old safe to delete?"
date: 2011-02-13
forum: General Help
---

### Post by charonn0 on 2011-02-13
While spelunking through my filesystem I came across this file:
/home/andrew/.local/share/akonadi/db_data/mysql.err.old

It's 368.7MB! Judging by its name, I surmise that it's probably not a critical file but I like to know what a file is before I delete it.

A more pressing question would be is having an error log this large indicative of a problem with Akonadi? 

Also, what exactly is Akonadi? I gather it's some sort of central datastore for various programs, though to what end is less than clear.

Kubuntu 10.10 x64


Edit To Add This:
The log consists of 
> InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11

repeated 2,402,435 times :o

---

### Post by Habitual on 2011-02-13
the error suggests that a mysql is already running when the log gets written to.

InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
InnoDB: Unable to lock ./ibdata1, error: 11

There should be another log called mysql.err - check that with ```
tail mysql.err
```

mysql.err.old is safe to delete, that's why it's called "old". :)

If in doubt just mv it with
```
mv /home/andrew/.local/share/akonadi/db_data/mysql.err.old /home/andrew/.local/share/akonadi/db_data/mysql.err.old.wtf
```

Check the contents of /home/andrew/.local/share/akonadi/db_data/mysql.err regularly.

1st google hit indicates Akonadi is KDE PIM - or at the "least" a KDE specific service or utility. 

Good Luck and HTH

---

### Post by charonn0 on 2011-02-15
*charonn0 deletes the old file with reckless abandon!

The not .old log has 4 stanzas of the same complaints as seen in the .old one. Nothing I can't ignore until my upcoming new build.

---

### Post by Habitual on 2011-02-16
> **charonn0 said:**
>  with reckless abandon!

Love the enthusiasm. Not so reckless when you know what to expect?

How about wreck less vs reckless? :D

Wisdom does not come with age re: "Nothing I can't ignore until my upcoming new build."

---

