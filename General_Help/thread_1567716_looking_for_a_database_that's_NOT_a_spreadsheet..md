---
title: "looking for a database that's NOT a spreadsheet."
date: 2010-09-04
forum: General Help
---

### Post by erbeesr on 2010-09-04
I have been using Lotus Approach for years!  I am wondering if there is a stand-alone "on my computer only" designable database that doesn't look like a SPREADSHEET and will import .dbf files.  I have waaaay to many records to start over. I have used 8.0.4 for a while and have just upgraded to 10.0.4.  Any suggestions?
erbeesr

---

### Post by DeMus on 2010-09-04
> **erbeesr said:**
> I have been using Lotus Approach for years!  I am wondering if there is a stand-alone "on my computer only" designable database that doesn't look like a SPREADSHEET and will import .dbf files.  I have waaaay to many records to start over. I have used 8.0.4 for a while and have just upgraded to 10.0.4.  Any suggestions?
erbeesr

Use the database in OpenOffice.org. It can do that.

---

### Post by JedMeister on 2010-09-04
Sorry, read post properly and deleted dumb response!:oops:

---

### Post by Rinzwind on 2010-09-04
Hey. Lotus approach? You use that under windows I pressume?

Is MYSQL an option? For windows there is a dbf2mysql.exe to convert dbf to mysql. [http://www.google.nl/search?aq=f&sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=dbf2mysql.exe](http://www.google.nl/search?aq=f&sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=dbf2mysql.exe)


Just to finish up in style:
There is also a package called dbf2mysql
[http://packages.ubuntu.com/dapper/dbf2mysql](http://packages.ubuntu.com/dapper/dbf2mysql)
Soooooo I guess you will be save under Linux too ;)

---

### Post by erbeesr on 2010-09-05
Thanks, I'll try dbf2mysql

---

### Post by perspectoff on 2010-09-05
> **erbeesr said:**
> Thanks, I'll try dbf2mysql

I think that's an excellent suggestion.

However, also realize that MySQL has been bought by Oracle and may not remain open source into the distant future.

PostgreSQL may be a better database in the long run for this reason, even though MySQL is ubiquitous.

Unfortunaetely, I don't know utilities to convert a Lotus database into PostgreSQL.

---

### Post by JedMeister on 2010-09-05
My 2c:
If you are looking for a "desktop only" approach I think DeMus' idea of using OpenOffice Base is well worth a look before you muck around with MySQL (or any other SQL). 

While MySQL (etc) is surely possible and in another circumstance may even be a better fit (definitely more scalable), I think the KISS mantra may be at least worth a shot. A brief google confirms that OpenOffice Base should easily be able to import your file (and probably resave with edited data). Easy way to check - try on a backup copy of one of your files...

---

### Post by Innigo on 2010-09-06
JedMeister is quite right. However, if you want future proofing or scalability/migration to a full blown RDBMS, consider SQLAlchemy. It can map your DB to Oracle, Postresql, MySQL or even (I think) Ms-sql.

---

### Post by aysiu on 2010-09-06
Check out Glom. It's sort of like a twisted Linux version of FileMaker.

---

