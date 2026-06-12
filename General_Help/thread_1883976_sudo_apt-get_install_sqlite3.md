---
title: "sudo apt-get install sqlite3"
date: 2011-11-20
forum: General Help
---

### Post by johniscool on 2011-11-20
Hi All, 

I am relatively new to Ubuntu, and so far love it. I have the latest version 11.10 set up to duel boot with Win 7.

Today I was trying to install SQLite3, did a 

```
sudo apt-get install sqlite3 
```

It seemed to install just fine. If I type:

```
sqlite3 --version
```

I get:

```
SQLite header and source version mismatch
```

I tried:

```

sudo apt-get remove sqlite3
sudo apt-get install sqlite3 

```

I still get the same thing. Any thoughts on how to fix this would be helpful. I have python and django installed, so I am not sure if that has something to do with it.

---

### Post by Paddy Landau on 2011-11-20
Try the following three commands.
```
sudo apt-get purge sqlite3 sqlite3-doc libsqlite3-0
sudo apt-get autoremove
sudo apt-get install sqlite3 sqlite3-doc
```

---

### Post by johniscool on 2011-11-20
That first command deleted everything. Now I need to reinstall Ubuntu.

But hey, now SQLite3 works...

---

### Post by Paddy Landau on 2011-11-21
> **johniscool said:**
> That first command deleted everything. Now I need to reinstall Ubuntu.
:confused: How?

I'm really sorry you hit that problem! I've never had that happen to me. How bizarre.

---

### Post by raja.genupula on 2011-11-21
actually i think the command should be 
```
sudo apt-get remove --purge <appname>
```

---

### Post by Paddy Landau on 2011-11-21
> **raja.genupula said:**
> actually i think the command should be 
```
sudo apt-get remove --purge <appname>
```
From the apt-get manual:> **remove --purge** is equivalent to the **purge** command.

---

