---
title: "Gnucash: Cleaning up and backing up"
date: 2011-05-16
forum: General Help
---

### Post by jgb2185 on 2011-05-16
I need to clean up and establish a regular backup protocol for my Gnucash data. Let's start simple and discuss just the cleanup.

I have several dozen data files in my Gnucash data directory. Here are the most recent twenty; the first one in the list is the file that currently opens when I launch Gnucash:

```
-rw-r--r--  1 khn khn 1028050 2011-05-15 16:20 accounts.20110102212607.xac 
-rw-r--r--  1 khn khn  249254 2011-05-15 16:20 accounts.20110102212607.xac.20110515161546.log
-rw-r--r--  1 khn khn 1027801 2011-05-15 16:15 accounts.20110102212607.xac.20110515162053.xac
-rw-r--r--  1 khn khn    1432 2011-05-15 16:10 accounts.20110102212607.xac.20110515160722.log
-rw-r--r--  1 khn khn 1027892 2011-05-15 16:07 accounts.20110102212607.xac.20110515161543.xac
-rw-r--r--  1 khn khn    1404 2011-05-15 16:02 accounts.20110102212607.xac.20110515160128.log
-rw-r--r--  1 khn khn 1027995 2011-05-15 16:01 accounts.20110102212607.xac.20110515160719.xac
-rw-r--r--  1 khn khn    1546 2011-05-15 15:56 accounts.20110102212607.xac.20110515155228.log
-rw-r--r--  1 khn khn 1027729 2011-05-15 15:52 accounts.20110102212607.xac.20110515160125.xac
-rw-r--r--  1 khn khn    4565 2011-05-15 15:52 accounts.20110102212607.xac.20110515154608.log
-rw-r--r--  1 khn khn 1027190 2011-05-15 15:46 accounts.20110102212607.xac.20110515155222.xac
-rw-r--r--  1 khn khn   22813 2011-05-15 15:43 accounts.20110102212607.xac.20110515154000.log
-rw-r--r--  1 khn khn     170 2011-05-13 13:42 accounts.20110102212607.xac.20110513134228.log
-rw-r--r--  1 khn khn 1026040 2011-05-13 13:42 accounts.20110102212607.xac.20110515154602.xac
-rw-r--r--  1 khn khn     192 2011-05-13 13:40 accounts.20110102212607.xac.20110513133848.log
-rw-r--r--  1 khn khn 1026040 2011-05-13 13:38 accounts.20110102212607.xac.20110513134222.xac
-rw-r--r--  1 khn khn   13460 2011-05-13 13:38 accounts.20110102212607.xac.20110513133512.log
-rw-r--r--  1 khn khn 1025906 2011-05-13 13:35 accounts.20110102212607.xac.20110513133841.xac

```
Obviously, something happened on or about Jan 2 of this year. Looking further back, I find this:

```
-rw-r--r-- 1 khn khn 965056 2011-01-02 21:26 accounts
```

This file shows up in Nautilus as a gzip file. I have a vague memory of encountering an error when opening Gnucash one day, and subsequently opening a backup file.

Questions:

[LIST=1]
[*]Can I delete all the [FONT="Courier New"].log[/FONT] files in this directory?
[*]Can I delete all but the most recent few [FONT="Courier New"].xac[/FONT] files (after backing up the older files)?
[*]Can I rename [FONT="Courier New"]accounts.20110102212607.xac[/FONT] to just plain accounts and use that as the default data file from now on?
[/LIST]

Many thanks for your help...

JGB

---

### Post by frankl6910 on 2011-12-10
> **jgb2185 said:**
> I need to clean up and establish a regular backup protocol for my Gnucash data. Let's start simple and discuss just the cleanup.

I have several dozen data files in my Gnucash data directory. Here are the most recent twenty; the first one in the list is the file that currently opens when I launch Gnucash:

```
-rw-r--r--  1 khn khn 1028050 2011-05-15 16:20 accounts.20110102212607.xac 
-rw-r--r--  1 khn khn  249254 2011-05-15 16:20 accounts.20110102212607.xac.20110515161546.log
-rw-r--r--  1 khn khn 1027801 2011-05-15 16:15 accounts.20110102212607.xac.20110515162053.xac
-rw-r--r--  1 khn khn    1432 2011-05-15 16:10 accounts.20110102212607.xac.20110515160722.log
-rw-r--r--  1 khn khn 1027892 2011-05-15 16:07 accounts.20110102212607.xac.20110515161543.xac
-rw-r--r--  1 khn khn    1404 2011-05-15 16:02 accounts.20110102212607.xac.20110515160128.log
-rw-r--r--  1 khn khn 1027995 2011-05-15 16:01 accounts.20110102212607.xac.20110515160719.xac
-rw-r--r--  1 khn khn    1546 2011-05-15 15:56 accounts.20110102212607.xac.20110515155228.log
-rw-r--r--  1 khn khn 1027729 2011-05-15 15:52 accounts.20110102212607.xac.20110515160125.xac
-rw-r--r--  1 khn khn    4565 2011-05-15 15:52 accounts.20110102212607.xac.20110515154608.log
-rw-r--r--  1 khn khn 1027190 2011-05-15 15:46 accounts.20110102212607.xac.20110515155222.xac
-rw-r--r--  1 khn khn   22813 2011-05-15 15:43 accounts.20110102212607.xac.20110515154000.log
-rw-r--r--  1 khn khn     170 2011-05-13 13:42 accounts.20110102212607.xac.20110513134228.log
-rw-r--r--  1 khn khn 1026040 2011-05-13 13:42 accounts.20110102212607.xac.20110515154602.xac
-rw-r--r--  1 khn khn     192 2011-05-13 13:40 accounts.20110102212607.xac.20110513133848.log
-rw-r--r--  1 khn khn 1026040 2011-05-13 13:38 accounts.20110102212607.xac.20110513134222.xac
-rw-r--r--  1 khn khn   13460 2011-05-13 13:38 accounts.20110102212607.xac.20110513133512.log
-rw-r--r--  1 khn khn 1025906 2011-05-13 13:35 accounts.20110102212607.xac.20110513133841.xac

```
Obviously, something happened on or about Jan 2 of this year. Looking further back, I find this:

```
-rw-r--r-- 1 khn khn 965056 2011-01-02 21:26 accounts
```

This file shows up in Nautilus as a gzip file. I have a vague memory of encountering an error when opening Gnucash one day, and subsequently opening a backup file.

Questions:

[LIST=1]
[*]Can I delete all the [FONT="Courier New"].log[/FONT] files in this directory?
[*]Can I delete all but the most recent few [FONT="Courier New"].xac[/FONT] files (after backing up the older files)?
[*]Can I rename [FONT="Courier New"]accounts.20110102212607.xac[/FONT] to just plain accounts and use that as the default data file from now on?
[/LIST]

Many thanks for your help...

JGB
Use this link [http://wiki.gnucash.org/wiki/FAQ](http://wiki.gnucash.org/wiki/FAQ). Questions 3.1.4 & 3.1.5 give the necessary info.
FrankL

---

