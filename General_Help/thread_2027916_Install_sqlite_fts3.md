---
title: "Install sqlite fts3"
date: 2012-07-17
forum: General Help
---

### Post by Enissay on 2012-07-17
Hi all,

I want to install sqlite fts3 to use it in a work for school... I found no tutorial how to install it, so can someone tell me how please ?

ps: I only found tutos on installing sqlite only... I heard That it's the same method and I have to enable the full text mode, I don't know how :/

Thanks in advance

---

### Post by spjackson on 2012-07-17
Simply install the sqlite3 package. fts3 is a compile time extension that is already enabled in the Ubuntu package. Once installed, you can test it like this.
```

$ sqlite3 temp.sqlite
SQLite version 3.7.9 2011-11-01 00:52:41
Enter ".help" for instructions
Enter SQL statements terminated with a ";"
sqlite> CREATE VIRTUAL TABLE pages USING fts3(title, keywords, body);
sqlite> .tables
pages           pages_content   pages_segdir    pages_segments
$ 

```For more information on fts3 see [http://www.sqlite.org/fts3.html](http://www.sqlite.org/fts3.html)

---

### Post by Enissay on 2012-07-18
I've the same output as you :D

Thanks mate :)

---

