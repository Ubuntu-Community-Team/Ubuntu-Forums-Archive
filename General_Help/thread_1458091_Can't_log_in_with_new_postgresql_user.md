---
title: "Can't log in with new postgresql user"
date: 2010-04-19
forum: General Help
---

### Post by ean5533 on 2010-04-19
This is my first time using postgresql (I'm a recent convert from mysql) and while I've had no trouble with anything complicated, I'm having some problems with the basics. I created a couple roles with login access, but I'm not able to log into them with psql. See below:

```
::~/.../projects/BookSoft/qt4-gui/BookSoft$ psql -d BookSoft
psql (8.4.3)
Type "help" for help.

BookSoft=# create user bsLogin with password 'abc';
CREATE ROLE
BookSoft=# \q
::~/.../projects/BookSoft/qt4-gui/BookSoft$ psql -d BookSoft -U bsLogin
**psql: FATAL:  role "bsLogin" does not exist**
::~/.../projects/BookSoft/qt4-gui/BookSoft$ psql -d BookSoft
psql (8.4.3)
Type "help" for help.

BookSoft=# create user bsLogin with password 'abc';
**ERROR:  role "bslogin" already exists**
BookSoft=# 

```

Note, I turned off localhost password authentication just to make things easier as I tried to figure this out. This is what's currently in my /etc/postgresql/8.4/main/pg_hba.conf file:

```
local   all         postgres                          ident
**local   all         all                               trust**
host    all         all         127.0.0.1/32          md5
host    all         all         ::1/128               md5
```

(And yes, I restarted postgres after making these changes.)

So, I know I'm missing something REALLY obvious here, but I can't figure out what it is. Any ideas?

---

### Post by ean5533 on 2010-04-19
I just figured it out. When you create a user in postgres, it converts the created username to lowercase. For example...

```
create user nEWusEr;
```

...creates the user "newuser", all lowercase. You'd think this means that it's not case sensitive, right? Well, apparently the command line arguments for psql aren't handled properly. See below:

```
::~$ psql -d BookSoft
psql (8.4.3)
Type "help" for help.

BookSoft=# create user bsLogin;
CREATE ROLE
BookSoft=# \q
::~$ psql -d BookSoft -U **bsLogin**;
psql: FATAL:  role "bsLogin" does not exist
::~$ psql -d BookSoft -U **bslogin**;
psql (8.4.3)
Type "help" for help.

BookSoft=> 
```

Lovely.

---

### Post by Oasu4g on 2010-05-12
Have you submitted it as a bug?

---

### Post by ean5533 on 2010-05-12
> **A. Tim said:**
> Have you submitted it as a bug?

Yep. Here is the response I got from them:

> Right.  This is because of a mixture of trying to adhere to the SQL
standard (which mandates that unquoted identifiers are case-folded) and
convenience of usafe of the shell command line.  The strict solution would
be to case-fold unquoted identifiers passed as arguments to psql, so
you'd be required to type something like
psql \"nEWuSer\"
to be able to log in as such a user -- otherwise the quotes would be
stripped by the shell.  However, this is so inconvenient that it has
been dumped in favor of not doing case-folding of idenfiers in shell
command line arguments, regardless of quoting.

In short, not a bug ...

I'm not sure how much I agree with them. If I understand the response correctly they're saying that the **default** for SQL is to case-fold (i.e. make lowercase) unquoted literals, but the **default** for the username argument is NOT to case fold unquoted literals. Their reason for not changing it is that it would be annoying for users who constantly try to log in as users that have non-case-folded usernames.

Or in other words, they don't want to inconvenience the minority in order to please the majority. Weird.

---

