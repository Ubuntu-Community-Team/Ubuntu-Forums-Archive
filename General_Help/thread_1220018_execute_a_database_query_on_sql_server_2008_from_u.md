---
title: "execute a database query on sql server 2008 from ubuntu"
date: 2009-07-22
forum: General Help
---

### Post by waraltca on 2009-07-22
Hi there,

I need your help to find the way to execute a query on a windows server from ubuntu.

The server has windows server 2003 and sql server 2008 standard edition.
The workstation has ubuntu 9.04

There is a software named isql from sybase that works as I need, the problem is that isql doesn't works on ubuntu.

Does anybody know what can I do?

thanks.

---

### Post by prem1er on 2009-07-22
SQuirreL

[http://squirrel-sql.sourceforge.net/](http://squirrel-sql.sourceforge.net/)

---

### Post by UranUtan on 2009-07-22
Or running iSQL within Wine?

---

### Post by waraltca on 2009-07-22
> **prem1er said:**
> SQuirreL

[http://squirrel-sql.sourceforge.net/](http://squirrel-sql.sourceforge.net/)

checking...
thanks!

[QUOTE=UranUtan]Thanks for answering!!
the problem with wine is that I can not connect to other server by network. Or I can??[/QUOTE]

---

### Post by waraltca on 2009-07-22
> **prem1er said:**
> SQuirreL

[http://squirrel-sql.sourceforge.net/](http://squirrel-sql.sourceforge.net/)
[COLOR="Red"]
Unable to find any mirror information for the "squirrel-sql-3.0.2-standard.zip" file. Please select another file[/COLOR].

Could you help me with that??
Thanks!

---

### Post by prem1er on 2009-07-22
[http://sourceforge.net/projects/squirrel-sql/files/](http://sourceforge.net/projects/squirrel-sql/files/)

Use this link and select the version you want.

---

### Post by waraltca on 2009-07-24
> **prem1er said:**
> [http://sourceforge.net/projects/squirrel-sql/files/](http://sourceforge.net/projects/squirrel-sql/files/)

Use this link and select the version you want.

thanks again!

I was able to run it. But I'm still unable to acces an sql server 2008 standard located on a network pc.

I think the problem is related with the driver I used. I don't know how to overcome that problem.

Could you help me with some information about that? 

I really appreciate your help.

thanks.

---

### Post by waraltca on 2009-08-11
> **UranUtan said:**
> Or running iSQL within Wine?

Have you acceeded by wine to a SQL server using isqlw??

---

