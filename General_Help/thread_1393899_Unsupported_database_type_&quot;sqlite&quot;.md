---
title: "Unsupported database type &quot;sqlite&quot;"
date: 2010-01-29
forum: General Help
---

### Post by kalivos on 2010-01-29
I have attempted to install Trac from several guides online, all end with the error message > TracError: Unsupported database type "sqlite"

This is Ubuntu Server (Karmic) & Trac .11 from apt-get

Output from Python:
```
>>> import sqlite
>>> sqlite.version
'1.0.1'
>>> sqlite._sqlite.sqlite_version()
'2.8.17'
```

Any ideas?

---

