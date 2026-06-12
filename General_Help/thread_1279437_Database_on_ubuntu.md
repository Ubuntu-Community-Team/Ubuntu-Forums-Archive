---
title: "Database on ubuntu"
date: 2009-09-30
forum: General Help
---

### Post by Ceiber Boy on 2009-09-30
What is the name of the database program that is used in ubuntu?

---

### Post by lovinglinux on 2009-09-30
I guess you are referring to MySQL, but there are others. For instance, Firefox uses SQLite, which does not require a server.

---

### Post by Ceiber Boy on 2009-10-01
> **lovinglinux said:**
> I guess you are referring to MySQL, but there are others. For instance, Firefox uses SQLite, which does not require a server.


No, not really. i want to create a simple database, i could use the openoffice database program byt its a heavy program for the simple databases i wish to create!

---

### Post by nikhilk on 2009-10-01
> **Ceiber Boy said:**
> No, not really. i want to create a simple database, i could use the openoffice database program byt its a heavy program for the simple databases i wish to create!

You could use SQLite for "simple" databases. But it is really hard to comment as simple is a relative term. Probably if you specify what features do want to use, you will get better suggestions.

---

### Post by wojox on 2009-10-01
I think LL's sqlite suggestion would do you right. It's small and fast. 

[http://www.sqlite.org/whentouse.html](http://www.sqlite.org/whentouse.html)

---

### Post by mike555 on 2009-10-01
KeepNote is good for data ...   [http://rasm.ods.org/keepnote/](http://rasm.ods.org/keepnote/)

---

### Post by lovinglinux on 2009-10-01
> **Ceiber Boy said:**
> No, not really. i want to create a simple database, i could use the openoffice database program byt its a heavy program for the simple databases i wish to create!

If you want something like Microsoft Access, then you could try [Kexi](http://kexi-project.org/about.html). I've never used it tho.

Perhaps SQLite could be useful too. It is already installed by default, but you can install [sqlitebrowser](apt:sqlitebrowser) [apt-get] or [SQLite Manager](https://addons.mozilla.org/en-US/firefox/addon/5817) extension for Firefox, to allow you to create and browse your tables. You can also control it from command-line with [sqlite3](apt:sqlite3).

---

### Post by Ceiber Boy on 2009-10-01
Sorry for not being a bit more specific, im abit embarrassed as i would like to have a database of my DVD collection as it is a bit on the large side!

i've only worked once with databases and it was MS office 03, and it was a bit of a bad experiance, hence i was looking for somthing simple that i could start with

thanks for being understanding

---

### Post by lovinglinux on 2009-10-01
> **Ceiber Boy said:**
> Sorry for not being a bit more specific, im abit embarrassed as i would like to have a database of my DVD collection as it is a bit on the large side!

i've only worked once with databases and it was MS office 03, and it was a bit of a bad experiance, hence i was looking for somthing simple that i could start with

thanks for being understanding

If you want to catalog a DVD movie collection, then I recommend [gcstar](apt:gcstar). For data collection you could use [gnomecatalog](apt:gnomecatalog), but there are other options.

---

