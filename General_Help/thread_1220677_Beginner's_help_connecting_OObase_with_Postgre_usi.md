---
title: "Beginner's help connecting OObase with Postgre using SDBC"
date: 2009-07-23
forum: General Help
---

### Post by Sleepallnight on 2009-07-23
Hi I'm quite new in posting threads so pardon me if I did something wrong in posting. 

I need to connect my tables in PostgreSQL with OObase. There's a textbox in OObase where we supposedly could just put the location of our Postgre tables in. I've tried /etc/postgresql/8.2/main/ but it produces:

Couldn't establish database connection to 'sdbc:postgresql:/etc/postgresql/8.4/main/' (missing "="after "/etc/postgresql/8.4/main/" in connection info string)

Does anyone knows where the default location of Postgre tables are actually situated in Ubuntu 9.04?

Extra info:
I used sudo apt-get install postgresql postgresql-client postgresql-contrib to install postgre

Thanks for your concern.

---

### Post by Sleepallnight on 2009-07-24
Got it myself [http://www.postgresonline.com/journal/index.php?/archives/8-Using-OpenOffice-Base-2.3.1-with-PostgreSQL.html](http://www.postgresonline.com/journal/index.php?/archives/8-Using-OpenOffice-Base-2.3.1-with-PostgreSQL.html)

I got it from here:

[http://martinusadyh.web.id/2009/06/20/view-your-database-schema-with-openoffice-301/](http://martinusadyh.web.id/2009/06/20/view-your-database-schema-with-openoffice-301/)

the site explains how to connect OObase to JDBC but its in Bahasa Indonesia language. 

: )

---

