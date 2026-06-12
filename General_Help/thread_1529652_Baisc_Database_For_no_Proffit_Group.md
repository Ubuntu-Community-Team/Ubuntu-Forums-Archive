---
title: "Baisc Database For no Proffit Group"
date: 2010-07-12
forum: General Help
---

### Post by cbaughman on 2010-07-12
Hello-

A Non Profit Organization I work with has built a contacts  Database in MS Access, however they have it hosted on one machine and have asked me to help them find the best solution for them to share this database outside the office.

We would me moving the database onto a new machine in the process, I don't have a copy of the database yet, nor have I gotten i true idea of the size i expect it's only 5-6k lines with a 100 or so columns, but that's only a educated guess.

I need to have around 10 users able to Edit the Database, and maybe 50 able to read the database. I was also hoping to set up some basic FTP (or samba) access on the sever if possible. 

I would really like to move this to an open source solution to save money and for my personal feelings on software. Even if this will bring more work on my head this should be a good learning experience. 

I'm looking for some suggestions on the best way to approach this, I keep seeing MySql as the top dog in the open source database world. Can MS access still manipulate MySql? 

Any other suggestions? What OS will be best? Any hardware suggestions? 

Thank you

---

### Post by mike555 on 2010-07-12
check out ;  [http://www.linuxalt.com/](http://www.linuxalt.com/) or ; [http://www.osalt.com/](http://www.osalt.com/)

---

### Post by oldfred on 2010-07-12
Some links to databases.
Databases:
OpenOffice database
MDB Viewer
Glom - design is loosely based on FileMaker Pro
[http://www.kexi-project.org/](http://www.kexi-project.org/)
[http://www.koffice.org/kexi/](http://www.koffice.org/kexi/)
[http://www.knoda.org/](http://www.knoda.org/)
[http://www.gnome-db.org/](http://www.gnome-db.org/)

For a backend either PostgreSQL or MySQL would be my choice. I used msAccess as a front end to MS-SQL server using the ODBC connects and I would think it would work with any ODBC database. The biggest issue is not the database but what front end do you use for editing, viewing & reporting. Most users create custom front ends when using ProtgreSQL or MySQL.

---

### Post by sidzen on 2010-07-12
"Any other suggestions? What OS will be best? Any hardware suggestions?"  --[cbaughman]("http://ubuntuforums.org/member.php?u=854862")

A NPO ought to be able to get a donation of outdated computers from the local university or community college.  This will be minus the hard drives.  Just look for a P4 or better that runs a 400 MHz bus and supports 1-2GB  PC3200 RAM.  This ought to be sufficent with the Open Office Database.  
No need for KDE or Gnome as desktop environments -- go light with XFCE or LXDE -- it will boost performance, if you don't go a server (no GUI).  
I agree with oldfred, Postgre is good. So would be a Debian or Debian-based distro running said desktops.
Get the boss to spring for or go halfers on attendance at a local or regional Linux Users conference!  The contacts made will be worth it!

---

