---
title: "Databases"
date: 2011-09-18
forum: General Help
---

### Post by nir2000 on 2011-09-18
Hi!
I need to learn about databases and I know nothing about it, a total beginner.
Are there is a database on Ubuntu and what Database it is?
If there is one, how do I use it.
I've got a tutorial on Mysql but I don't understand how to work with it in Ubuntu.
please any help me.
Help will be greatly appreciated.
Thank you in advance.

---

### Post by brucehohl on 2011-09-18
If you want to start by understanding database basics and Structured Query Language (SQL) I suggest you spend some time with SQLite. What you learn about SQLite will almost certainly apply to any other database you use in the future.
$ sudo apt-get install sqlite3 sqlite3-doc
[http://www.sqlite.org/](http://www.sqlite.org/)

It would actually be very beneficial to do this from gnome-terminal to make it easy to explore all the capabilities but there are also various graphical front-end tools like: 
$ sudo apt-get install sqlitebrowser
$ sudo apt-get install sqliteman
[https://addons.mozilla.org/en-US/firefox/addon/sqlite-manager/](https://addons.mozilla.org/en-US/firefox/addon/sqlite-manager/)

There are of course other options like PostgreSQL and LibreOffice Base. If you give move information about what you are trying to achieve you might get a better answer.

---

### Post by Elmer Fudd on 2011-09-18
Can you be more specific about what you want to do with the Database?

The simplest for you to start might be the one included in LibreOffice (or OpenOffice). Use the Database Wizard and the help files to get yourself started.

good luck.

---

### Post by nir2000 on 2011-09-19
Thank you Bruce I'll check on those links you have given me.

---

### Post by nir2000 on 2011-09-19
Elmer, thank you for your attention. Mainly I need to know SQL and how to program with Databases.

---

### Post by drdos2006 on 2011-09-19
Hi there
This web site might help you more.

[http://dabodev.com/](http://dabodev.com/)

[http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment1.html](http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment1.html)

[http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment2.html](http://c0129431.cdn.cloudfiles.rackspacecloud.com/dataenvironment2.html)

regards

---

