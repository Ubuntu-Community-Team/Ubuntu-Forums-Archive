---
title: "searching for simple program for sql"
date: 2009-10-26
forum: General Help
---

### Post by vitaly87 on 2009-10-26
hello!
i trying to find some easy program to work on it for my learning sql. in windows i am working with orcal my sql. 
i found some program in ubuntu called anymeal but i cant connect to anything. if anybody now some easy program to do a basing things like add remove find in data base without any server.

---

### Post by duanedesign on 2009-10-26
i am not real familiar with sql. Let me ask around in some of my groups and see if anyone was any suggestions

---

### Post by cprofitt on 2009-10-26
Want to be clear -- you are using  Oracle and MySql -- not Microsoft SQL  Right?

---

### Post by phillw on 2009-10-26
> **vitaly87 said:**
> hello!
i trying to find some easy program to work on it for my learning sql. in windows i am working with orcal my sql. 
i found some program in ubuntu called anymeal but i cant connect to anything. if anybody now some easy program to do a basing things like add remove find in data base without any server.


Add / remove data from a database without a server ?????:o

That's what servers are for.

I recall someone mentioning about a flat table that can be done in ubuntu without a server, but can't recall, nor find, it.

Popping on a MySQL server is pretty easy, and there are a couple of GUI proggies for MySQL


There is no need to instal a fully blown LAMP system, you can just put MySQL on its own & use the likes of MySQL Administrator 
and MySQL Query Browser to access it.

[https://help.ubuntu.com/9.04/serverguide/C/mysql.html](https://help.ubuntu.com/9.04/serverguide/C/mysql.html)

Once you have the mysql server running, sysnaptics will help you if you type in MySQL GUI
Install the Ubuntu flagged GUI ones.

Regards,

Phill.

---

### Post by diesch on 2009-10-26
> **vitaly87 said:**
> hello!
i trying to find some easy program to work on it for my learning sql. in windows i am working with orcal my sql. 


You can use MySQL in Ubuntu, too. There some graphical frontends like mysql-query-browser and mysql-navigator

> **vitaly87 said:**
> 
i found some program in ubuntu called anymeal but i cant connect to anything. if anybody now some easy program to do a basing things like add remove find in data base without any server.

anymeal is a program to manage cooking recipes that uses MySQL as its storage backend. I don't think that's what you want.

---

### Post by amoeba801 on 2009-10-26
You can learn SQL in Ubuntu without installing or setting up anything.

[sqlite]("http://www.sqlite.org/") is an alternative MySQL that does not require a server which, I think, is already installed as a default package on your system. You can test for it, and use it from the command line:
> $ sqlite
SQLite version 2.8.17
Enter ".help" for instructions
sqlite>

You can then use SQL commands at the sqlite prompt to create tables, and add, delete and query data. 
If you don't want to use the command line there is [SqliteStudio]("http://sqlitestudio.one.pl/index.rvt"), or in your firefox browser via an [add-on]("https://addons.mozilla.org/en-US/firefox/addon/5817"). 

Just about every programming language and web framework supports sqlite. In particular, python which is installed on your system has sqlite as a standard library package. You can use python with sqlite right now on you system without any installation or configuration.

If the command line sqlite is not installed on you system, use the following command:
> $ sudo apt-get install sqlite libsqlite3-dev

---

