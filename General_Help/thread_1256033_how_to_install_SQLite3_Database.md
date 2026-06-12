---
title: "how to install SQLite3 Database"
date: 2009-09-02
forum: General Help
---

### Post by suresh_vandiyur on 2009-09-02
how to install the SQLite3 database in kubuntu

---

### Post by t0p on 2009-09-02
Try this in konsole:

```
sudo apt-get install sqlite3
```

---

### Post by suresh_vandiyur on 2009-09-02
> **t0p said:**
> Try this in konsole:

```
sudo apt-get install sqlite3
``` No need for other configuration?

---

### Post by lovinglinux on 2009-09-02
> **t0p said:**
> Try this in konsole:

```
sudo apt-get install sqlite3
```

The package sqlite3 is not the same as SQLite 3, it's just a command-line tool for accessing SQLite 3. The SQLite 3 library, which is installed by default and used by a lot of Gnome applications, is libsqlite3-0.

> **suresh_vandiyur said:**
> No need for other configuration?

I believe SQLIte does not require any configuration, because it's not a standalone server database manager.

> Unlike client-server database management systems, the SQLite engine is not a standalone process with which the application program communicates. Instead, the SQLite library is linked in and thus becomes an integral part of the application program. 

What are you trying to achieve anyway?

---

