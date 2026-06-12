---
title: "&quot;Queries&quot; about MySQL"
date: 2010-10-27
forum: General Help
---

### Post by Curbuntu on 2010-10-27
I know this isn't strictly an Ubuntu question, but...

I need to come up to speed very quickly on basic MySQL database manipulation, because I have to transfer a small website based on a very small MySQL database from one hosting company to another within the next 48 hours.  I want to make certain everything works correctly after the transfer.   Until today I’ve never had to deal with MySQL databases of any sort, so I frantically Googling, and reading and working through the mySQL chapters in O’Reilly’s “Learning PHP & MySQL” book.


  Although I didn’t have direct move-it-from-here-to-there access to the database file through the control panel’s file system (probably because it’s in “root”), I was able to back it up, and download the backup as a file called (for simplicity’s sake) simple.sql.  (Okay, it was tar.gz’d, but I extracted it on this end.)  On the hosting server I can open and access the database, so I know that I have the correct username and password.
  I can’t open simple.sql on local host as a MySQL database (that is, from the “mysql” prompt), though I can open simple.sql with an editor (Geany) and everything appears normal.  I can open other MySQL databases on my system, and I can create them and manipulate them (INSERT, ALTER, etc.) from the mysql prompt.  I assume this means that I have correctly installed mysql server and client, and that I’m correctly remembering the mysql root password.
  

I notice that none of the other MySQL databases in /var/lib/mysql/ (which seems to be the default folder for mysql databases in Ubuntu 10.04.1 LTS) actually ends in the .sql extension.  Instead, the database name is actually a folder name, and the resulting folder is populated by names like tablename.frm, tablename.MYD, and tablename.MYI, etc.  I think I see the equivalent structure of several tables in simple.sql when I open it in Geany.
  

That’s a long explanation, exposing my vast ignorance of this subject, but my questions are two:
  
[LIST=1]
[*]If I upload the simple.sql to the     new hosting company, will that process automatically create the     directory-name/table-file structure that I’m seeing on my personal     system (localhost) with properly working databases?
[/LIST]
 
[LIST=1]
[*]If I needed to make a copy of this     simple.sql database accessible as a MySQL file on localhost, how     would I do it?
[/LIST]
  Thanks in advance.

---

### Post by katykat on 2010-10-27
On the remote website you would go into phpmyadmin (or their equivalent MySQL editor) and IMPORT the file. 

Locally 
mysql -uLOGIN -pPASSWORD databasename < simple.sql 
should work.

Though I rarely do that, and simply use my own local version of phpmyadmin.

---

