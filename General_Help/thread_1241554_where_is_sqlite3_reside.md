---
title: "where is sqlite3 reside?"
date: 2009-08-16
forum: General Help
---

### Post by lutubu on 2009-08-16
Hi everyone
I am new to Linux, I am trying to install wxSqlite to Ubuntu Jaunty and it needs to know which directory sqlite3 has been installed into. Synaptic Package Manager indicates that sqlite3 has been installed but I can't find where it is, can someone help please. Thanks in advance

---

### Post by DeMus on 2009-08-16
> **lutubu said:**
> Hi everyone
I am new to Linux, I am trying to install wxSqlite to Ubuntu Jaunty and it needs to know which directory sqlite3 has been installed into. Synaptic Package Manager indicates that sqlite3 has been installed but I can't find where it is, can someone help please. Thanks in advance

In Synaptic look again for sqlite3.
Then right-click that line and choose properties.
Look in TAB Installed Files.

---

### Post by lovinglinux on 2009-08-16
Please notice that **sqlite3** package is a command-line interface for SQLite 3. I don't know if is that what you need, but it doesn't work without SQLite 3 shared libraries, which are provided by **libsqlite3-0**. So if you need SQLite3 as a whole, I guess what you are looking for is at **/usr/lib/libsqlite3.so.0**. If you need the command-line tool, then you will find it at **/usr/bin/sqlite3**.

---

